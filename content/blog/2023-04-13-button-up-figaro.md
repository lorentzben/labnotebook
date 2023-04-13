---
title: 'Button Up Figaro'
date: 2023-04-13T14:19:14Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
  - "normalize"
  - "figaro"
  - "SRS"
description: "Description for the page"
---

### Todos for Today

- Class
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Is my pairise permanova the same as the pairwise one
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Ade

#### Does Q score matter if we use cutoffs

To figure this out we have to look at the ampliseq code to see the logic comparisons

from ampliseq workflow: 

```nextflow
# workflows/ampliseq.nf

trunclenf = params.trunclenf ?: 0
trunclenr = params.trunclenr ?: 0
if ( !single_end && !params.illumina_pe_its && (params.trunclenf == null || params.trunclenr == null) && !is_fasta_input ) {
    find_truncation_values = true
    log.warn "No DADA2 cutoffs were specified (`--trunclenf` & `--trunclenr`), therefore reads will be truncated where median quality drops below ${params.trunc_qmin} (defined by `--trunc_qmin`) but at least a fraction of ${params.trunc_rmin} (defined by `--trunc_rmin`) of the reads will be retained.\nThe chosen cutoffs do not account for required overlap for merging, therefore DADA2 might have poor merging efficiency or even fail.\n"
} else { find_truncation_values = false }

if ( !is_fasta_input && (!params.FW_primer || !params.RV_primer) && !params.skip_cutadapt ) {
    log.error "Incompatible parameters: `--FW_primer` and `--RV_primer` are required for primer trimming. If primer trimming is not needed, use `--skip_cutadapt`."
    System.exit(1)
}
```

leads to subworkflow dada2_preprocessing:

```nextflow 
# subworkflows/local/dada2_preprocessing.nf

//find truncation values in case they are not supplied
    if ( find_truncation_values ) {
        TRUNCLEN ( DADA2_QUALITY1.out.tsv )
        TRUNCLEN.out.trunc
            .toSortedList()
            .set { ch_trunc }
        ch_versions_dada2_preprocessing = ch_versions_dada2_preprocessing.mix(TRUNCLEN.out.versions.first())
        //add one more warning or reminder that trunclenf and trunclenr were chosen automatically
        ch_trunc.subscribe {
            if ( "${it[0][1]}".toInteger() + "${it[1][1]}".toInteger() <= 10 ) { log.warn "`--trunclenf` was set to ${it[0][1]} and `--trunclenr` to ${it[1][1]}, this is too low! Please either change `--trunc_qmin` (and `--trunc_rmin`), or set `--trunclenf` and `--trunclenr`." }
            else if ( "${it[0][1]}".toInteger() <= 10 ) { log.warn "`--trunclenf` was set to ${it[0][1]}, this is too low! Please either change `--trunc_qmin` (and `--trunc_rmin`), or set `--trunclenf` and `--trunclenr`." }
            else if ( "${it[1][1]}".toInteger() <= 10 ) { log.warn "`--trunclenr` was set to ${it[1][1]}, this is too low! Please either change `--trunc_qmin` (and `--trunc_rmin`), or set `--trunclenf` and `--trunclenr`." }
            else log.warn "Probably everything is fine, but this is a reminder that `--trunclenf` was set automatically to ${it[0][1]} and `--trunclenr` to ${it[1][1]}. If this doesnt seem reasonable, then please change `--trunc_qmin` (and `--trunc_rmin`), or set `--trunclenf` and `--trunclenr` directly."
        }
    } else {
        Channel.fromList( [['FW', trunclenf], ['RV', trunclenr]] )
            .toSortedList()
            .set { ch_trunc }
    }
    ch_trimmed_reads.combine(ch_trunc).set { ch_trimmed_reads }
```

Leads to modules/local/trunclen.nf which is just a wrapper for

```python
# bin/trunclen.py
#!/usr/bin/env python3
# @author Daniel Straub
# Takes two CSV files from QIIME2 demux output, a quality threshold and a cutoff for the retained read fraction
# to generate a tuple of index locations that resemble the cutoff value used for DADA2 in QIIME2.

import pandas as pd
import sys

# argument check
if len(sys.argv) != 4:
    exit("Usage: dada_trunc_parameter.py <*_qual_stats.tsv> <int[0-40]> <float[0-1]>")

# parameters
data = pd.read_csv(sys.argv[1], delimiter="\t")  # quality values forward reads
qmin = float(sys.argv[2])  # quality threshold
rmin = float(sys.argv[3])  # read count threshold (fraction)

# select row with median values (file row 6, starting with "50%") and drop first row
median = data.iloc[1][1:].values.tolist()

# select row with count numbers (file row name "count")
reads = data.iloc[0][1:].values.tolist()
# extract maximum read count
fraction_reads = int(max(reads) * rmin)


# iterate through values and find first value that falls below threshold
def function(values, cutoff):
    trunc = len(values)
    for value in values:
        if value < cutoff:
            trunc = values.index(value)
            break
    return trunc


# find quality threshold
trunc_median = function(median, qmin)

# find read threshold
trunc_reads = function(reads, fraction_reads)

# final threshold
trunc = min(trunc_median, trunc_reads)

# print values
print(trunc, end="")
```

Example quality file they are examining:

```bash
Cycle	1	2	3	4	5	6	7	8	9	10	11	12	13	14	15
Count	1977937	1977937	1977937	1977937	1977937	1977937	1977937	1977937	1977937	1977937	1977937	1977937	1977937	1977937	1977937
Median	33	33	33	34	33	37	37	34	37	37	34	37	38	38	38
```

I was passing in --trunc_qmin: 30 and --trunc_rmin: 0.75 (default) 

So based on these values, my guess is that there was no truncation, this was contrasted with figaro which did trim and leads into the next question.

To answer the main question: no --trunc_qmin is not considered if you provide cutoffs :)

#### How does figaro determine the cutoffs?

Pretty straight forward question but will the answer be too?

Description from [whitepaper](https://files.zymoresearch.com/documents/figaro_whitepaper.pdf):

"that can select optimal trimming sites
for paired-end data that allows for minimizing expected sequencing errors while
maximizing read retention and maintaining sufficient read length for downstream merging."
 
It uses the cumulative expected errors, $y = a * e^{bx} + c$ n-th percentile for expected errors at a given position. 

Max EE are calculated based on forward and reverse trim positions with the correct overlap length. FEE and REE are iterated to determine how many reads would be retained. 

There is a balance between read retention and subtracting EE>1

$score = read_retention - [(expected_error_forward - 1)^2 + (expected_error_reverse - 1)^2]$

#### Check Alpha diversity test

Make sure that the factors are being filtered like beta diversity test

They were not even present so I added print calls

cycle 4 rev: 973b51163e2e4375a0bf2f233e3a9cd72e0402b4
visualize ampliseq res: 37592a7c3983effb09606b8187d4d29968b501b8
slurm sub: 20971956

```bash
[2d/c57294] process > REPORT05ALPHABOXPLOT (1)       [100%] 1 of 1 ✔

Completed at: 13-Apr-2023 16:32:41
Duration    : 1m 7s
CPU hours   : 1.3 (99.4% cached)
Succeeded   : 1
Cached      : 28
```

cycle 4 rev: 973b51163e2e4375a0bf2f233e3a9cd72e0402b4
visualize ampliseq res: 8bc14050feb6748038d76095d97aaa14e713513f 
slurm sub: 20972504

```bash
[1f/f2104c] process > REPORT05ALPHABOXPLOT (1)       [100%] 1 of 1 ✔

Completed at: 13-Apr-2023 16:55:52
Duration    : 1m 7s
CPU hours   : 1.3 (99.2% cached)
Succeeded   : 1
Cached      : 28
```

cycle 4 rev: 973b51163e2e4375a0bf2f233e3a9cd72e0402b4
visualize ampliseq res: 26f48e393a1068f142aabe32fee765ce5effcaf9 
slurm sub: 20973212

```bash
```

#### PERMANOVA post-hoc

Does my method follow the same procedure as the R package I found online?

#### Beta diversity measurments

Are there any other tests I should consider?

#### OTUs at 97% 

Provide the option to Cluster taxa into 97% otus

### Merge Figaro Back to Main

#### SRS vs Rarefy


### Todos for Tomorrow

- Class
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Is my pairise permanova the same as the pairwise one
  - Beta diversity measurements
  - Cluster to 97% similarity?
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Git Commit

#### Lab Notebook

```bash
11f3fb9 - Benjamin Lorentz, Thu Apr 13 16:02:05 2023 -0400 : add figaro updates
e5d432c - Benjamin Lorentz, Thu Apr 13 11:51:14 2023 -0400 : cutoff comparison found
47973f3 - Benjamin Lorentz, Thu Apr 13 10:35:30 2023 -0400 : add page for thursday
```

#### Visualize Ampliseq

```bash
26f48e3 - Benjamin Lorentz, Thu Apr 13 17:01:46 2023 -0400 : update 05
8bc1405 - Benjamin Lorentz, Thu Apr 13 16:44:00 2023 -0400 : update 05
37592a7 - Benjamin Lorentz, Thu Apr 13 16:17:54 2023 -0400 : update 05 report
```

#### Cycle 4

```bash
973b511 - Benjamin Lorentz, Thu Apr 13 16:00:54 2023 -0400 : update ade-cycle*figaro
```
  
---
title: 'Learn Decontam'
date: 2023-03-28T12:50:58Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "automate_16_nf"
description: "Description for the page"
---

### Todos for Today

- Class
  - read over Ellie's sections
  - what can I write? 
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Check ASV count to the dada2 table 
    - Alternativley use the dada2 table
  - figure out where to implement a filtering step
  - How does the other Ben's Analysis line up with mine/ampliseq?
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

#### Import, Phyloseq-ize and then export tsv table

I need to finish the code to saving a hd5 biom table to file.

Workdir: /scratch/bjl34716/ade/cycle-4/work/2f/656da911598186a483b442c3c5bf22

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: 9eaeccb4e6257b685cc18695cc9b357eee82e5a9
slurm job: 20329204

```bash
biom.exception.TableException: Unable to cast metadata: ['28', 'CYC3', 'YES', '4', 'CYCL3INF28']
```

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: 91915a12ceb69b4d68c4342d6ad7702cb2cca57f
slurm job: 20330381

```bash
Completed at: 28-Mar-2023 10:00:07
Duration    : 2m 5s
CPU hours   : 1.6 (99.6% cached)
Succeeded   : 2
Cached      : 26
```

So this works right now. The only thing right now is that the metadata is missing; I want to see if we can add it back in possibly, if not in 1 POM then we will just move on to the filtering

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: 060fefd727b26986b233ec2dfca2d56abb301e98
slurm job: 20332933

```bash
Command exit status:
  126

Command output:
  (empty)

Command error:
  /usr/bin/env: ‘.command.sh’: Permission denied

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c2/9e80eadcaa74936f34e9873888939a
```

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: 1a5ddb850e800fa6fc0ad134a550c5137bb586a3
slurm job: 20333945

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  There was a problem importing md-table.biom:
  
    md-table.biom is not a(n) BIOMV100Format file

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/ba/583e34873a30bb8fce7a77b8335a67
```

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: f0f94c735c26da2a381bbe7bf78efdf4d35a4fbc
slurm job: 20334642

```bash
Completed at: 28-Mar-2023 10:32:14
Duration    : 1m 7s
CPU hours   : 1.6 (99.9% cached)
Succeeded   : 1
Cached      : 27
```

#### Decontam Package

This is the sentence we are working off of:

"Amplicon sequence variants (ASVs) with less than 5 sequences in total were removed from the dataset before decontamination. Contaminant sequences were identified from extracted negative controls with the R package decontam and the probability threshold set to 0.5" - [Temporal dynamics of the cecal and litter microbiome of chickens raised in two separate broiler houses](https://www.frontiersin.org/articles/10.3389/fphys.2023.1083192/full)

We are using the Prevalence method to identify true negatives.

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: e3c9cbcdc0798a360b620ee5310af283c33221d5
slurm job: 20360495

```bash
Completed at: 28-Mar-2023 14:57:52
Duration    : 2m 6s
CPU hours   : 1.6 (99.4% cached)
Succeeded   : 2
Cached      : 26
```

#### Update downstream table qzas

Want to double check the biom from results/qiime2/abundance_tables/feature-table.biom is the same as results/dada2/ASV_table.tsv. 

The tables are not the same, so I want to be able to pull in the qiime version so that it matches the GENERATEBIOMFORGRAPHLAN process

TODO: modify the contam process to be a bool


cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: 50733c81ce90bce6bafd434ba6e43e88298ddc0a
slurm job: 20369004

```bash
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [jovial_almeida] DSL2 - revision: 50733c81ce [control]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /scratch/bjl34716/ade/cycle-4/litter
metadata : /scratch/bjl34716/ade/cycle-4/litter/metadata.tsv
item of interest : Treatment
ordered item of interest : ordered_item_of_interest.csv
outdir   : /work/sealab/bjl34716/ade/cycle-4/litter
rarefaction depth : 0
controls: /home/bjl34716/ade/cycle-4/litter/controls.tsv
profile : slurm,singularity

Process `RAREFACTIONPLOT` declares 3 input channels but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 71 or see '.nextflow.log' file for more details
```


cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: 1815081c6f5898d13f0d13f2028f085c1f3de703
slurm job: 20370685

```bash
Process `TSVTOQZA` declares 2 input channels but 3 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 68 or see '.nextflow.log' file for more details
```


cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev:  a540470980df15320c59985e77d655f5e872c321 
slurm job: 20371979

```bash

No such variable: filtered_table_biom

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 68 or see '.nextflow.log' file for more details
[ERROR] Terminal initialization failed; falling back to unsupported
java.lang.IllegalStateException: Shutdown in progress
        at java.base/java.lang.ApplicationShutdownHooks.add(ApplicationShutdownHooks.java:66)
        at java.base/java.lang.Runtime.addShutdownHook(Runtime.java:213)
        at jline.internal.ShutdownHooks.addHook(ShutdownHooks.java:79)
```

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: f9bbdb7e376aeb21aaf4b4f22eeeb8485a6004e1
slurm job: 20372443

```bash
```

NOT FINISHED, the rarefaction function is still using the unfiltered table, we'll have to fix the logic so that it is the correct one

### Update The rarefaction report Rmd file to use the QIIME Tables


### Todos for Tomorrow

- Class
  - read over Ellie's sections
  - what can I write? 
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
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

### Git Commits

#### Lab Notebook

```bash
2c4a75f - Benjamin Lorentz, Tue Mar 28 08:57:12 2023 -0400 : add page for Tuesday
```

#### Visualize Ampliseq

```bash
1815081 - Benjamin Lorentz, Tue Mar 28 16:39:34 2023 -0400 : update main.nf and contam_script.r
50733c8 - Benjamin Lorentz, Tue Mar 28 16:27:00 2023 -0400 : update main.nf and contam_script.r
e3c9cbc - Benjamin Lorentz, Tue Mar 28 14:51:41 2023 -0400 : update contam_script.r
f0f94c7 - Benjamin Lorentz, Tue Mar 28 10:27:26 2023 -0400 : update main.nf
1a5ddb8 - Benjamin Lorentz, Tue Mar 28 10:21:05 2023 -0400 : update main.nf
060fefd - Benjamin Lorentz, Tue Mar 28 10:13:20 2023 -0400 : update main.nf
91915a1 - Benjamin Lorentz, Tue Mar 28 09:53:00 2023 -0400 : update contam_script.r
9eaeccb - Benjamin Lorentz, Tue Mar 28 09:42:45 2023 -0400 : update main.nf and contam_script.r
```

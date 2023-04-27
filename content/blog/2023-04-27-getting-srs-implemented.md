---
title: 'Getting Srs Implemented'
date: 2023-04-27T14:02:31Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
description: "Description for the page"
---

### Todos for Today

- Class
  - Paper finalize
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Make TSVTOQZA a module, and use multiple import
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
- Check out https://youtu.be/oBfu3prR5FA

### Ade 

#### Restart analysis on Sapelo2

We need to figure out qzatable to just be the qza archive not the whole thing

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 791f834dd728be23fbbfec73c0a1ce8dacb18038
slurm job: 21479740

```bash
Process `SRSCURVE` declares 5 input channels but 6 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 84 or see '.nextflow.log' file for more details
[-        ] process > ORDERIOI              -
[-        ] process > FILTERNEGATIVECONTROL -
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 621ec107235a12c591d0606c5cc53aa75c3d3d80
slurm job: 21535570

```bash
WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/ec/e2412c6bc7a7f5bd04cc1e2ee0b284/.command.sh", line 18, in <module>
    unrarefied_table = Artifact.load('table.qza')
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/result.py", line 66, in load
    archiver = archive.Archiver.load(filepath)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 299, in load
    archive = cls.get_archive(filepath)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 259, in get_archive
    raise ValueError("%s does not exist." % filepath)
ValueError: table.qza does not exist.`, size: 958 (max: 255)
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: a2ab2c0c40591ccab7e474524ea82d857d0612e5
slurm job: 21536830

```bash
Launching `https://github.com/lorentzben/visualize-ampliseq` [reverent_almeida] DSL2 - revision: a2ab2c0c40 [srs]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /scratch/bjl34716/ade/cycle-4/litter-srs
metadata : /scratch/bjl34716/ade/cycle-4/litter-srs/metadata.tsv
item of interest : Treatment
ordered item of interest : /home/bjl34716/ade/cycle-4/litter/ord_ioi.csv
outdir   : /work/sealab/bjl34716/ade/cycle-4/litter-srs
rarefaction depth : 16500
controls: /home/bjl34716/ade/cycle-4/litter/controls.tsv
srs: true
profile : slurm,singularity

Missing process or function with name 'getAt'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 81 or see '.nextflow.log' file for more details
[-        ] process > ORDERIOI -
```

I am going to try to remap the data

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: ed04d835d3cea6bbdb6f170c30a21dd9ec35754f
slurm job: by hand

```bash
Multi-channel output cannot be applied to operator map for which argument is already provided

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 81 or see '.nextflow.log' file for more details
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: eec30a37991cbcc84555ca55d11b1ebdd85fa5c3
slurm job: by hand

```bash
Multi-channel output cannot be applied to operator map for which argument is already provided

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 81 or see '.nextflow.log' file for more details
```


cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 45f58de45d05feef5a6c87a4582fdc77b08a84ca
slurm job: by hand

```bash
Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Traceback (most recent call last):
    File ".command.sh", line 18, in <module>
      unrarefied_table = Artifact.load('table.qza')
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/result.py", line 66, in load
      archiver = archive.Archiver.load(filepath)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 299, in load
      archive = cls.get_archive(filepath)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 259, in get_archive
      raise ValueError("%s does not exist." % filepath)
  ValueError: table.qza does not exist.

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/cb/ae6f4cb740f706cbcfa2ac28afdd9c
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: dbf9acde6493c1db024335fc0d6822fc76cc5492
slurm job: by hand

```bash

Command error:


  processing file: srs_curve.rmd
  Quitting from lines 13-31 (srs_curve.rmd)
  Error in read_qza("table.qza") :
    Input artifact (table.qza) not found. Please check path and/or use list.files() to see files in current working directory.
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read_qza
  Execution halted


  processing file: srs_curve.rmd
  Quitting from lines 13-31 (srs_curve.rmd)
  Error in read_qza("table.qza") :
    Input artifact (table.qza) not found. Please check path and/or use list.files() to see files in current working directory.
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read_qza
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/29/826d5e55086f24fd6503ef6371559f
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: edc13d2af0d8e9a4cd6d2622d405fc34facdb1bc
slurm job: by hand

```bash
 Loading required package: shinycssloaders
  Loading required package: shinybusy
  Error: unexpected '/' in:
  "} else {qii
      norm_tab <- SRS(un_rare_tab, /"
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/b7/9404a62b043d3eaab3554a2e83ab4a
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: a073047c7fe8820c3f43329253ca76e92d8c4cc8
slurm job: by hand

```bash
 WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `Loading required package: vegan
Loading required package: permute
Loading required package: lattice
This is vegan 2.6-2
Loading required package: shiny
Loading required package: DT

Attaching package: ‘DT’

The following objects are masked from ‘package:shiny’:

    dataTableOutput, renderDataTable

Loading required package: shinycssloaders
Loading required package: shinybusy
Warning message:
In readLines("/scratch/bjl34716/ade/cycle-4/work/9d/7b7972e85efb549377fe955d7e35d1/srs_min_curve_val.txt") :
  incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/9d/7b7972e85efb549377fe955d7e35d1/srs_min_curve_val.txt'
Error in write_biom(norm_tab, "normalized-table.biom") :
  could not find function "write_biom"
Execution halted`, size: 744 (max: 255)
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 64870b29248261feb3b6a4b275943ee014e39a40
slurm job: by hand

```bash
Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Traceback (most recent call last):
    File ".command.sh", line 18, in <module>
      unrarefied_table = Artifact.load('table.qza')
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/result.py", line 66, in load
      archiver = archive.Archiver.load(filepath)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 299, in load
      archive = cls.get_archive(filepath)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 264, in get_archive
      raise ValueError("%s is not a QIIME archive." % filepath)
  ValueError: table.qza is not a QIIME archive.

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/01/e5e547183eacbeaa1e265ffd432aec
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 64870b29248261feb3b6a4b275943ee014e39a40
slurm job: by hand

```bash
Work dir:
  /scratch/bjl34716/ade/cycle-4/work/01/e5e547183eacbeaa1e265ffd432aec

Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/01/e5e547183eacbeaa1e265ffd432aec/.command.sh", line 18, in <module>
    unrarefied_table = Artifact.load('table.qza')
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/result.py", line 66, in load
    archiver = archive.Archiver.load(filepath)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 299, in load
    archive = cls.get_archive(filepath)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 264, in get_archive
    raise ValueError("%s is not a QIIME archive." % filepath)
ValueError: table.qza is not a QIIME archive.`, size: 974 (max: 255)
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 7251b27b27c1b0b2a433ec6cde7d01cc0dde31ae 
slurm job: by hand

```bash
Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Traceback (most recent call last):
    File ".command.sh", line 60, in <module>
      core = diversity.pipelines.core_metrics_phylogenetic(unrarefied_table, rooted_tree, 16500, metadata)
    File "<decorator-gen-421>", line 2, in core_metrics_phylogenetic
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      output_types, provenance)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 484, in _callable_executor_
      outputs = self._callable(scope.ctx, **view_args)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_diversity/_core_metrics.py", line 59, in core_metrics_phylogenetic
      metadata=metadata, n_jobs=n_jobs_or_threads)
    File "<decorator-gen-543>", line 2, in core_metrics
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      output_types, provenance)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 484, in _callable_executor_
      outputs = self._callable(scope.ctx, **view_args)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_diversity/_core_metrics.py", line 23, in core_metrics
      with_replacement=with_replacement)
    File "<decorator-gen-544>", line 2, in rarefy
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      output_types, provenance)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 390, in _callable_executor_
      output_views = self._callable(**view_args)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_feature_table/_normalize.py", line 18, in rarefy
      raise ValueError('The rarefied table contains no samples or features. '
  ValueError: The rarefied table contains no samples or features. Verify your table is valid and that you provided a shallow enough sampling depth.

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/ca/10c1c25a37c992be7e1d594d19bb67

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`
```
```

The table coming into COREMETRIC... is empty so I need to step backwards to:

norm_qza_table = TSVTOQZA2.out.qza.map{it.last()}
TSVTOQZA2(tsv_map_2, metadata_ch)
tsv_map_2 = SRSNORMALIZE.out.biom_normalized.map{
  it ->  [ [id: "SRS-Normalized-Biom"], it ]
}

SRSNORMALIZE( FILTERNEGATIVECONTROL.out.filtered_table_tsv, input_ch, SRSCURVE.out.min_val, params.rare)

rare = 16500/ cmin:

  Cmin The number of counts to which all samples will be normalized. Typically, the
  total OTU count of the sample with the lowest sequencing depth is chosen as
  Cmin. Samples with sequencing depth lower than the chosen Cmin will be
  discarded
  

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: f66f8b62516c5feb54779b7cfce0c3af6c592b74 
slurm job: by hand

```bash
Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Traceback (most recent call last):
    File ".command.sh", line 60, in <module>
      core = diversity.pipelines.core_metrics_phylogenetic(unrarefied_table, rooted_tree, 16500, metadata)
    File "<decorator-gen-421>", line 2, in core_metrics_phylogenetic
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      output_types, provenance)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 484, in _callable_executor_
      outputs = self._callable(scope.ctx, **view_args)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_diversity/_core_metrics.py", line 59, in core_metrics_phylogenetic
      metadata=metadata, n_jobs=n_jobs_or_threads)
    File "<decorator-gen-543>", line 2, in core_metrics
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      output_types, provenance)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 484, in _callable_executor_
      outputs = self._callable(scope.ctx, **view_args)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_diversity/_core_metrics.py", line 23, in core_metrics
      with_replacement=with_replacement)
    File "<decorator-gen-544>", line 2, in rarefy
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      output_types, provenance)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 390, in _callable_executor_
      output_views = self._callable(**view_args)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_feature_table/_normalize.py", line 18, in rarefy
      raise ValueError('The rarefied table contains no samples or features. '
  ValueError: The rarefied table contains no samples or features. Verify your table is valid and that you provided a shallow enough sampling depth.

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/fd/5cb6acca18e10a198be3335752bcbb
```

We need to go into the SRS dir: /scratch/bjl34716/ade/cycle-4/work/b7/30b7f38e7b77a6a8dca76de1bcc740

do colsums for the tsv file and then the biom:

lorentzb/qiime2r:2.0

```r
library(qiime2R)
library(tidyverse)
library(biomformat)

tsv_tab <- read_table('normalized-table.tsv')

> colSums(tsv_tab)
  "LT100"   "LT101"   "LT102"   "LT103"   "LT104"   "LT106"   "LT107"   "LT108"
    16500     16500     16500     16500     16500     16500     16500     16500
  "LT109"   "LT110"   "LT111"   "LT112"   "LT113"   "LT114"   "LT115"   "LT116"
    16500     16500     16500     16500     16500     16500     16500     16500
  "LT117"   "LT118"   "LT119"   "LT120"    "LT74"    "LT75"    "LT76"    "LT77"
    16500     16500     16500     16500     16500     16500     16500     16500
   "LT78"    "LT79"    "LT80"    "LT81"    "LT82"    "LT84"    "LT85"    "LT86"
    16500     16500     16500     16500     16500     16500     16500     16500
   "LT87"    "LT88"    "LT89"    "LT90"    "LT91"    "LT92"    "LT93"    "LT95"
    16500     16500     16500     16500     16500     16500     16500     16500
   "LT98"    "LT99" "MOCK323"   "NC168"   "NC287"
    16500     16500     16500     16500     16500
    
```



additionally the rownames(ASVIDs) are not present so this is an SRS issue:

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 8a8d57d5c41269a9f2e5dc09417867b2091f2d1c
slurm job: by hand

```bash
Completed at: 27-Apr-2023 14:46:48
Duration    : 12m 7s
CPU hours   : 1.2 (74.4% cached)
Succeeded   : 17
Cached      : 13
```

Success

##### Check the Rarefaction Method

Do we need the COREMETRICSRS method, or can we use the original one?

workdir: /scratch/bjl34716/ade/cycle-4/work/56/bfd5ef28d4a21157937007198cb015

```r
library(tidyverse)
library(qiime2R)

srs_tab_obj <- read_qza('table.qza')

srs_tab <- srs_tab_obj$data

colSums(srs_tab)
  LT100   LT101   LT102   LT103   LT104   LT106   LT107   LT108   LT109   LT110
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
  LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119   LT120
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82    LT84
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT98    LT99 MOCK323   NC168   NC287
  16500   16500   16500   16500   16500

> as.vector(rowSums(srs_tab))
   [1]     2     0     0     0     0     2     1     8     1     3     1     1
  [13]     1   234     6    92     2   320     3     3     1   301     1     3
  [25]   120   306     1    48     1     3     2     1   245     2    16    21
  [37]   237    36     1    40     3     3    13     1     2     2     7     1
  [49]     2    16    27     2    11     1     6     4     0     4     1    20
  [61]     1    24     2     1     6     1     1     1     8     1     1     5
  [73]     1     2     8     1     3     5     1     4     3    34     2     8
  [85]     1     2    36     1     2     1     1     3     1     2     6     8
  [97]     2     4    25     2     1     1     1     1    32     3     9     5
 [109]     1     4     1    63     6    11    62     4     3    15     0     0
 [121]     1     1     1     1     2     1     5  4342     3     1     1     2
 [133]   913     1     2    10     1     2     1     1     1    21  2152    16
 [145]     3     1   326    66     5  2509     2    70  2208     1  7225     1
 [157]     2    27     2     2     3     1     8     1     1     0     2  9154
 [169]   388    60  2944     1     4     7   735 33109    20   958  2531 67965
 [181]   192  1465  4461     7   935   100    24   107    58    26  7468   438
 [193]   253  3198    88   210    52   632    88   762    18     6   178     6
 [205]     1    83     5    45    16  6891     4     2   721 23936    95    77
 [217]    98     1    50    17   122   398    10    20     7  4000 11911     1
 [229]     5     2     1     3     3  1942    99   612     0  3836     6   744
 [241]   172    54    68    85    66   129     1   745  1310  7678    44    60
 [253]    23     4     1     1    24     1  7159     7     3     3     3     1
 [265]     5     7     3     2     2     5  5573  1923     7     5    23   543
 [277]  5135 75666     6  2833   426     2    75  1336    13  6768     4  4299
 [289]  6136 17827 11674  1622  9190     1     0    67     4     4     1     1
 [301]     2    23     2     7     1     5     1     1     5    19    61   432
 [313]    25  2893    34     1    78    15     1    11     8     4     2   209
 [325]     5   980    15   151     2     3     7     1     2     2   430    24
 [337]    94     2    38     3     2   712  1240     1     7    19   937    46
 [349]    11    78     8     5     4     4   541     1     8    15   146    12
 [361]     3     6   119     4     6     0     0     1     1    29     1     2
 [373]     1     1     0     2     8     0   136    52     0     0     1     1
 [385]     1     2     1     1    17     0     5  3605     2     4     1     1
 [397]     3     1     0     0     0     0     0     0     0     1  1619     4
 [409]     7    43     0    12    14    79     5     6     6     1    12     2
 [421]     0     2   314     0    33  2524    23    52     0     9     8    13
 [433]   357     1    13    56    47   114     1 22533    38     0     1   105
 [445]    29   147     0     3     3     0     0     1     0  2193     0     0
 [457]     0     0     0     2     1     0     0     0     1     0     6    19
 [469]     1     4     0     0  2745     2    14     2    18    42    39     1
 [481]     1     1     2     4   783     1     0     0     0     0     0     0
 [493]     0     0     0     0     0     0     0     0     0     0     0     0
 [505]     0     0     0     0     0     0     0     0     0     0     0     0
 [517]     0     0     0     0     0     0     0     0     0     2     1     0
 [529]     0     0     0     0     0     0     0     0     0     0     0     0
 [541]     0     0     0     0     0     0     0     0     0     0     0     0
 [553]     0     0     0     0     0     0     0     0     0     0     0     0
 [565]     1     0     0     0     0     0     0     0     0     0     0     0
 [577]     0     0     0     0     0     0     0     0     0     0     0     0
 [589]     0     0     0     0     0     0     0     0     0     0     0     0
 [601]     0     0     0     0     0     0     0     0     0     0     1    47
 [613]    21     6    62     2     1     6     2     7     2    18     2     0
 [625]     0     0     0     0     0     0     0     0     0     0     0     0
 [637]     0     0     0     0     0     0     0     0     0     0     0     0
 [649]     0     0     0     0     3     0     0     0     0     0     1     0
 [661]     9   168    21    16   207  4767   266   185  2828  1288   195  1560
 [673]     1   117   423   102  2352     1    63     2    29     8    44    10
 [685]    43    24     3    29  6617 23502   506    78    14    76    18   778
 [697]     5     6    69    14     2     6    68   113   232 62089    30  5716
 [709]    89  3182  4926   946  4279    10  1150     0     1    23   406   919
 [721]     2  1484     2     4     1     1     1     1     1     2     3   116
 [733]  8137  6039  1942     1     1  2398     0     2    70    13    22    57
 [745]  2968  1663   452   686    97  2921  5360   513     8   863     0     0
 [757]     2     1   151     2     2     2     0     0    13     0     0     1
 [769]     1     0     0     0     0     0     0     0     0     0     0     0
 [781]     0     0     0     0     0     0     0     0     0     0     0     0
 [793]     0     0     1     3   202     9    18    11     1     1     1    14
 [805]     4    12  1127     0     0     0     0     0     0     0    36     1
 [817]    11    10    21     1     1     9     0     0     0     0     0     0
 [829]     0     0     0     0     0     0     0     0     0     0     0     0
 [841]     0     0     0     0     0     0     0     0     0     0     0     0
 [853]     0     0     0     0     0     0     0     0     0     1     1     1
 [865]     1     1     1     2  1747     2     5     1     2     0     0   482
 [877]   463  2637     4     1     1     2    29     6     1     2     8     1
 [889]     1    19    99     1     4     1     2     2   113   217     1     1
 [901]     0     0     0     0     0     0     0     0     0     0     0     0
 [913]     0     0     0   771   158     1     1     1     1     2     1     2
 [925]     1     2     3     5     3    13     0     0     0     0     4     0
 [937]     1     0     0     0     0     0     0     0     0     0     0     1
 [949]     0  1313     0     0     0     1     1     1     5     1     0     4
 [961]     3     9     0     1    94     0   897     5     4     0     1     4
 [973]     3     0     0     0     0     0     0     0     1     0     0     0
 [985]     0     0     0     0     0     0     0     0     0     2    17     5
 [997]     0     0     0     0     0     0     0     0     0     0     0     0
[1009]     1   240     1     1    12    40     1     1     5     5     3     1
[1021]     1     5    48    64    13     6   385    14    16    51    10     6
[1033]     2     8     2    13     3    24     5    75     3     2     8     3
[1045]    57    16     6     2    13     4   145   492     2     2    74     2
[1057]    24     1   245     2     2    21     2     2    67    16     3     4
[1069]     1    24    17    15    31   227   103    12     3     1     1     0
[1081]     1     1    42     6    42     2    17    11     1    25     2    11
[1093]     6    49     4     4     8   118    11     3     8     5    92    14
[1105]     6    23    63     2    74    76   206     1    16     7   100     2
[1117]     1     2     3     5     7    31    35     4     2     1     2     1
[1129]     1     1     4     1     2     1     1     1     1     1     1     1
[1141]     2     2     1     7     1     0     2    11     2     1     1     1
[1153]     1     1     4     1     1     1     7     2     1     1     1     3
[1165]     1     1     2   410    46     1   203   528     1    34     5    31
[1177]     3   151   118     4     9    17    80     3     2    16    94   195
[1189]     1    16     1    14     2     2     2     1     1    21   384  6397
[1201]     3   289     3     0     3   154     2     1     1     1     1     1
[1213]     1     1     2     9  1050    18     1     0     0     0    10     2
[1225]     1     7     1    15   110     5   280     6    18    34     6    52
[1237]     2     1     1    22     2     0     1     1     2     1    22     2
[1249]     1     3     4     7    16     1     1     3     1     1   219     4
[1261]   478   273    16   774   328    23    35     7     4     2     3     3
[1273]     2     2     1     2     1    10     1     1     3     8     1     3
[1285]     6     1     7     9     4     1     2   153     1    10     2     0
[1297]     2     1     4    35     4     4     0     1    94     2     6    54
[1309]     1     3    16     3     3    17     1     2     1     1     5     0
[1321]    24   110     3     4  1207    38    23  2029  2024  1034   734    59
[1333]   157    10   130   822     5    10   320     0  7431   615  1459    36
[1345]    70 15302   140  5148    30   869    20    74  1337     4     7     5
[1357]     2   264    18   264    15     2    34     4    11     1   119    68
[1369]     8     2     1     2     1     2     0     2     2     1     7    87
[1381]     6   314     6   239     2    28     2    10    78     9     3     4
[1393]    72     4     8     1   128    10     5     1     6     2     2    25
[1405]    74     7    43     2     1     1     1     2     2     1     1     1
[1417]     2    62     3    12    63     6    89     9     6    24     2     1
[1429]    41     3   134     1     1     2     2     1     1     7     1     7
[1441]    17  1432     2    29   162     2     3    31    27     5     1     1
[1453]    11    24     1     1     0     4     1     1     3     4   131     2
[1465]     1     1    11   113     1    52   401    16     5     2    14     1
[1477]     1   455   117     6    17     1   233   330    42     5    25     2
[1489]    24    27     2    12     1   292   860   393   219    29     4    60
[1501]     7     1     1     1     1     2    79     1     3    30     1     1
[1513]     4     2   179     1     4     7     1    47   111    28   324 10474
[1525]     4     1   182     1     2     1   235     5     2   208    14     4
[1537]    40     1     9    17     1     1    38     8     1     1     1     1
[1549]     1     2     1     1     1     1     1     1     1     3     1     1
[1561]     1     1     3     1     2     6    73   497     3  1851    63  1824
[1573]     1     8     1     1     1    11     8    77    14     2     6     2
[1585]   767     1     3     1     1     5     2     1     3     1     1     0
[1597]    10     2    30     1     9     2     1     1     2    47     2    10
[1609]    16     1     9    14     1     2     6     1     1    17     2   118
[1621]     3  1163    21   126   289    83    10   327   225     5   454     2
[1633]     0   348   197  2070     6   996   134  1114    56   852   280     8
[1645]    54   260  6739    30   621     8     3   215    55   172     7     2
[1657]    29   258     2     0     2    34     6   207    35     7    75     3
[1669]   301    10   747     2     1    38    15   254    37     3     5   220
[1681]    12     6     2     2   219    46     2    59   625     6   892    64
[1693]    26   194    56    61    92   542    66   557   846     2     4     2
[1705]     3     6   514   171   875     1  1897    15     3  3948    12   603
[1717]   601   430    10    55   566    17  2025     3     3   576   119     6
[1729]  4099    98   185   397  2836  2398    31    12   370    69    17   160
[1741]    83   105

qiime_table_obj <- read_qza('diversity_core/rarefied_table.qza')
qiime_table <- qiime_table_obj$data

> colSums(qiime_table)
  LT100   LT101   LT102   LT103   LT104   LT106   LT107   LT108   LT109   LT110
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
  LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119   LT120
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82    LT84
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT98    LT99 MOCK323   NC168   NC287
  16500   16500   16500   16500   16500

> as.vector(rowSums(qiime_table))
   [1]     2     2     1     8     1     3     1     1     1   234     6    92
  [13]     2   320     3     3     1   301     1     3   120   306     1    48
  [25]     1     3     2     1   245     2    16    21   237    36     1    40
  [37]     3     3    13     1     2     2     7     1     2    16    27     2
  [49]    11     1     6     4     4     1    20     1    24     2     1     6
  [61]     1     1     1     8     1     1     5     1     2     8     1     3
  [73]     5     1     4     3    34     2     8     1     2    36     1     2
  [85]     1     1     3     1     2     6     8     2     4    25     2     1
  [97]     1     1     1    32     3     9     5     1     4     1    63     6
 [109]    11    62     4     3    15     1     1     1     1     2     1     5
 [121]  4342     3     1     1     2   913     1     2    10     1     2     1
 [133]     1     1    21  2152    16     3     1   326    66     5  2509     2
 [145]    70  2208     1  7225     1     2    27     2     2     3     1     8
 [157]     1     1     2  9154   388    60  2944     1     4     7   735 33109
 [169]    20   958  2531 67965   192  1465  4461     7   935   100    24   107
 [181]    58    26  7468   438   253  3198    88   210    52   632    88   762
 [193]    18     6   178     6     1    83     5    45    16  6891     4     2
 [205]   721 23936    95    77    98     1    50    17   122   398    10    20
 [217]     7  4000 11911     1     5     2     1     3     3  1942    99   612
 [229]  3836     6   744   172    54    68    85    66   129     1   745  1310
 [241]  7678    44    60    23     4     1     1    24     1  7159     7     3
 [253]     3     3     1     5     7     3     2     2     5  5573  1923     7
 [265]     5    23   543  5135 75666     6  2833   426     2    75  1336    13
 [277]  6768     4  4299  6136 17827 11674  1622  9190     1    67     4     4
 [289]     1     1     2    23     2     7     1     5     1     1     5    19
 [301]    61   432    25  2893    34     1    78    15     1    11     8     4
 [313]     2   209     5   980    15   151     2     3     7     1     2     2
 [325]   430    24    94     2    38     3     2   712  1240     1     7    19
 [337]   937    46    11    78     8     5     4     4   541     1     8    15
 [349]   146    12     3     6   119     4     6     1     1    29     1     2
 [361]     1     1     2     8   136    52     1     1     1     2     1     1
 [373]    17     5  3605     2     4     1     1     3     1     1  1619     4
 [385]     7    43    12    14    79     5     6     6     1    12     2     2
 [397]   314    33  2524    23    52     9     8    13   357     1    13    56
 [409]    47   114     1 22533    38     1   105    29   147     3     3     1
 [421]  2193     2     1     1     6    19     1     4  2745     2    14     2
 [433]    18    42    39     1     1     1     2     4   783     1     2     1
 [445]     1     1    47    21     6    62     2     1     6     2     7     2
 [457]    18     2     3     1     9   168    21    16   207  4767   266   185
 [469]  2828  1288   195  1560     1   117   423   102  2352     1    63     2
 [481]    29     8    44    10    43    24     3    29  6617 23502   506    78
 [493]    14    76    18   778     5     6    69    14     2     6    68   113
 [505]   232 62089    30  5716    89  3182  4926   946  4279    10  1150     1
 [517]    23   406   919     2  1484     2     4     1     1     1     1     1
 [529]     2     3   116  8137  6039  1942     1     1  2398     2    70    13
 [541]    22    57  2968  1663   452   686    97  2921  5360   513     8   863
 [553]     2     1   151     2     2     2    13     1     1     1     3   202
 [565]     9    18    11     1     1     1    14     4    12  1127    36     1
 [577]    11    10    21     1     1     9     1     1     1     1     1     1
 [589]     2  1747     2     5     1     2   482   463  2637     4     1     1
 [601]     2    29     6     1     2     8     1     1    19    99     1     4
 [613]     1     2     2   113   217     1     1   771   158     1     1     1
 [625]     1     2     1     2     1     2     3     5     3    13     4     1
 [637]     1  1313     1     1     1     5     1     4     3     9     1    94
 [649]   897     5     4     1     4     3     1     2    17     5     1   240
 [661]     1     1    12    40     1     1     5     5     3     1     1     5
 [673]    48    64    13     6   385    14    16    51    10     6     2     8
 [685]     2    13     3    24     5    75     3     2     8     3    57    16
 [697]     6     2    13     4   145   492     2     2    74     2    24     1
 [709]   245     2     2    21     2     2    67    16     3     4     1    24
 [721]    17    15    31   227   103    12     3     1     1     1     1    42
 [733]     6    42     2    17    11     1    25     2    11     6    49     4
 [745]     4     8   118    11     3     8     5    92    14     6    23    63
 [757]     2    74    76   206     1    16     7   100     2     1     2     3
 [769]     5     7    31    35     4     2     1     2     1     1     1     4
 [781]     1     2     1     1     1     1     1     1     1     2     2     1
 [793]     7     1     2    11     2     1     1     1     1     1     4     1
 [805]     1     1     7     2     1     1     1     3     1     1     2   410
 [817]    46     1   203   528     1    34     5    31     3   151   118     4
 [829]     9    17    80     3     2    16    94   195     1    16     1    14
 [841]     2     2     2     1     1    21   384  6397     3   289     3     3
 [853]   154     2     1     1     1     1     1     1     1     2     9  1050
 [865]    18     1    10     2     1     7     1    15   110     5   280     6
 [877]    18    34     6    52     2     1     1    22     2     1     1     2
 [889]     1    22     2     1     3     4     7    16     1     1     3     1
 [901]     1   219     4   478   273    16   774   328    23    35     7     4
 [913]     2     3     3     2     2     1     2     1    10     1     1     3
 [925]     8     1     3     6     1     7     9     4     1     2   153     1
 [937]    10     2     2     1     4    35     4     4     1    94     2     6
 [949]    54     1     3    16     3     3    17     1     2     1     1     5
 [961]    24   110     3     4  1207    38    23  2029  2024  1034   734    59
 [973]   157    10   130   822     5    10   320  7431   615  1459    36    70
 [985] 15302   140  5148    30   869    20    74  1337     4     7     5     2
 [997]   264    18   264    15     2    34     4    11     1   119    68     8
[1009]     2     1     2     1     2     2     2     1     7    87     6   314
[1021]     6   239     2    28     2    10    78     9     3     4    72     4
[1033]     8     1   128    10     5     1     6     2     2    25    74     7
[1045]    43     2     1     1     1     2     2     1     1     1     2    62
[1057]     3    12    63     6    89     9     6    24     2     1    41     3
[1069]   134     1     1     2     2     1     1     7     1     7    17  1432
[1081]     2    29   162     2     3    31    27     5     1     1    11    24
[1093]     1     1     4     1     1     3     4   131     2     1     1    11
[1105]   113     1    52   401    16     5     2    14     1     1   455   117
[1117]     6    17     1   233   330    42     5    25     2    24    27     2
[1129]    12     1   292   860   393   219    29     4    60     7     1     1
[1141]     1     1     2    79     1     3    30     1     1     4     2   179
[1153]     1     4     7     1    47   111    28   324 10474     4     1   182
[1165]     1     2     1   235     5     2   208    14     4    40     1     9
[1177]    17     1     1    38     8     1     1     1     1     1     2     1
[1189]     1     1     1     1     1     1     3     1     1     1     1     3
[1201]     1     2     6    73   497     3  1851    63  1824     1     8     1
[1213]     1     1    11     8    77    14     2     6     2   767     1     3
[1225]     1     1     5     2     1     3     1     1    10     2    30     1
[1237]     9     2     1     1     2    47     2    10    16     1     9    14
[1249]     1     2     6     1     1    17     2   118     3  1163    21   126
[1261]   289    83    10   327   225     5   454     2   348   197  2070     6
[1273]   996   134  1114    56   852   280     8    54   260  6739    30   621
[1285]     8     3   215    55   172     7     2    29   258     2     2    34
[1297]     6   207    35     7    75     3   301    10   747     2     1    38
[1309]    15   254    37     3     5   220    12     6     2     2   219    46
[1321]     2    59   625     6   892    64    26   194    56    61    92   542
[1333]    66   557   846     2     4     2     3     6   514   171   875     1
[1345]  1897    15     3  3948    12   603   601   430    10    55   566    17
[1357]  2025     3     3   576   119     6  4099    98   185   397  2836  2398
[1369]    31    12   370    69    17   160    83   105

> dim(srs_tab)
[1] 1742   45
> dim(qiime_table)
[1] 1376   45

> sum(as.vector(rowSums(qiime_table)) == 0)
[1] 0

> sum(as.vector(rowSums(srs_tab)) == 0)
[1] 366

> sum(as.vector(rowSums(srs_tab)[rowSums(srs_tab) != 0]) == as.vector(rowSums(qiime_table)))
[1] 1376

```

Okay we are good, the rarefaction just prunes taxa that are observed 0 times in the selected samples.

###### Downstream Analysis

Make sure each report pulls in the proper table.

Yes Nc and Yes SRS 

if you need a tsv normalized version: SRSNORMALIZE.out.tsv_normalized
if you need a qza normalized version: norm_qza_table (with 0s), or COREMETRICPYTHON.out.rare_table (no 0s)

Report 01

tsv filtered nc but not normalized: FILTERNEGATIVECONTROL.out.filtered_table_tsv
qza filtered nc but not normalized: qza_table


What is in the Report01 folder for no SRS no NC?:

```bash
ls /scratch/bjl34716/ade/cycle-4/work/04/39a8161b7715c92ea64f5fe8687304

filtered-table.tsv is not present
```

We need to make the NC/NC check and then just make sure the right one is passed through





If this works we have to work on the downstream analysis

#### SRS but no control

#### No SRS control

#### No SRS no control

### Unit testing:

Here is the nf-core test data location

https://github.com/nf-core/test-datasets/tree/ampliseq

### Todos for Tomorrow

- Class
  - Paper finalize
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - Yes NC Yes SRS
     - Yes NC no SRS
     - No NC Yes SRS
     - No NC No SRS
  - Tamura optmization for richness?
  - Make these subworkflows as opposed to one long workflow?
  - Unit tests based on the example data
  - Positive Control Analysis
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Check out https://youtu.be/oBfu3prR5FA

### Git Commits

#### lab notebook

```bash
86382d8 - Benjamin Lorentz, Thu Apr 27 11:54:38 2023 -0400 : notes before lunch
3081a99 - Benjamin Lorentz, Thu Apr 27 10:03:58 2023 -0400 : added page for thursday
```

#### Visualize Ampliseq

```bash
8a8d57d - Benjamin Lorentz, Thu Apr 27 14:33:49 2023 -0400 : update main.nf
f66f8b6 - Benjamin Lorentz, Thu Apr 27 14:04:41 2023 -0400 : update main.nf
3e15743 - Benjamin Lorentz, Thu Apr 27 14:03:26 2023 -0400 : update main.nf
7251b27 - Benjamin Lorentz, Thu Apr 27 13:25:58 2023 -0400 : update main.nf
64870b2 - Benjamin Lorentz, Thu Apr 27 11:48:55 2023 -0400 : update main.nf
a073047 - Benjamin Lorentz, Thu Apr 27 11:27:21 2023 -0400 : update main.nf
2e7a166 - Benjamin Lorentz, Thu Apr 27 11:10:53 2023 -0400 : update main.nf
edc13d2 - Benjamin Lorentz, Thu Apr 27 11:08:20 2023 -0400 : update main.nf
dbf9acd - Benjamin Lorentz, Thu Apr 27 11:06:15 2023 -0400 : update main.nf
45f58de - Benjamin Lorentz, Thu Apr 27 11:01:17 2023 -0400 : update main.nf
eec30a3 - Benjamin Lorentz, Thu Apr 27 10:59:16 2023 -0400 : update main.nf
ed04d83 - Benjamin Lorentz, Thu Apr 27 10:55:48 2023 -0400 : update main.nf
:...skipping...
8a8d57d - Benjamin Lorentz, Thu Apr 27 14:33:49 2023 -0400 : update main.nf
f66f8b6 - Benjamin Lorentz, Thu Apr 27 14:04:41 2023 -0400 : update main.nf
3e15743 - Benjamin Lorentz, Thu Apr 27 14:03:26 2023 -0400 : update main.nf
7251b27 - Benjamin Lorentz, Thu Apr 27 13:25:58 2023 -0400 : update main.nf
64870b2 - Benjamin Lorentz, Thu Apr 27 11:48:55 2023 -0400 : update main.nf
a073047 - Benjamin Lorentz, Thu Apr 27 11:27:21 2023 -0400 : update main.nf
2e7a166 - Benjamin Lorentz, Thu Apr 27 11:10:53 2023 -0400 : update main.nf
edc13d2 - Benjamin Lorentz, Thu Apr 27 11:08:20 2023 -0400 : update main.nf
dbf9acd - Benjamin Lorentz, Thu Apr 27 11:06:15 2023 -0400 : update main.nf
45f58de - Benjamin Lorentz, Thu Apr 27 11:01:17 2023 -0400 : update main.nf
eec30a3 - Benjamin Lorentz, Thu Apr 27 10:59:16 2023 -0400 : update main.nf
ed04d83 - Benjamin Lorentz, Thu Apr 27 10:55:48 2023 -0400 : update main.nf
a2ab2c0 - Benjamin Lorentz, Thu Apr 27 10:40:09 2023 -0400 : update main.nf
621ec10 - Benjamin Lorentz, Thu Apr 27 10:19:28 2023 -0400 : update main.nf
```

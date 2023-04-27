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

### Todos for Tomorrow

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
visualize ampliseq rev: 
slurm job: by hand

```bash
```


### Unit testing:

Here is the nf-core test data location

https://github.com/nf-core/test-datasets/tree/ampliseq



---
title: 'Continue Srs Implement'
date: 2023-04-19T15:01:35Z
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
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
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

#### SRS vs Rarefy

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 07587466d6bbae25e4463a153beff8c326d6d552
slurm sub: 21088572

```bash
WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `Warning in install.packages("SRS", repos = "http://cran.us.r-project.org") :
  'lib = "/opt/conda/envs/qiime2-2020.8/lib/R/library"' is not writable
Error in install.packages("SRS", repos = "http://cran.us.r-project.org") :
  unable to install packages
Execution halted
/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/35/053dfcda1f4003a350465840929adc/.command.sh", line 62, in <module>
    srs_curve = srs.actions.SRScurve(table)
  File "<decorator-gen-124>", line 2, in SRScurve
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
    output_types, provenance)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 452, in _callable_executor_
    ret_val = self._callable(output_dir=temp_dir, **view_args)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_srs/_SRScurve.py", line 53, in SRScurve
    run_commands([cmd])
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_srs/_SRScurve.py", line 29, in run_commands
    subprocess.run(cmd, check=True)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/subprocess.py", line 438, in run
    output=stdout, stderr=stderr)
subprocess.CalledProcessError: Command '['SRScurve.R', '/tmp/tmp4exldxlh/table.tsv', 'richness', '50', '0', '0', 'False', '10', 'False', 'black', 'red', 'solid', 'longdash', 'False', '/tmp/qiime2-temp-l0ipvzpu']' returned non-zero exit status 1.`, size: 1724 (max: 255)
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: b712f15097da8ae422db162c433d8f2b715e52e6
slurm sub: 21117067

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
    File ".command.sh", line 57
      Rscript -e srs_curve.r maxdepth
                 ^
  SyntaxError: invalid syntax

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/15/399059eaf30c21fb32e9e13d93d220
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: b8bbe5d8001a730f6172eabd43cd8ffe6fb24083
slurm sub: 21117096

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [big_monod] DSL2 - revision: b8bbe5d800 [srs]
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

Process `SRSCURVE` declares 3 input channels but 4 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 76 or see '.nextflow.log' file for more details
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 1a8fbe2f8156308a86ee05d30c910155ffe33061
slurm sub:  21117132

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
  Traceback (most recent call last):
    File ".command.sh", line 4, in <module>
      from qiime2 import Metadata
  ModuleNotFoundError: No module named 'qiime2'

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/66/a9e12341557c72e7d50a0e8058e854
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 8a0f8b739f69176f30329217ede26fcf8165a8aa
slurm sub: 21120241

```bash
Caused by:
  Missing output file(s) `SRS_curve.png` expected by process `SRSCURVE (1)`
  
Command exit status:
  0

Command output:
  Script started, file is srs_curve.r
  $ 
  Script done, file is srs_curve.r
  WARNING The sampling depth of 4 is quite small for rarefaction

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/e8/3f846c8455fbdbd3995eb3c2cb7b78
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: e9b57b11812824ae940d8784ea5196794c6d1ff4
slurm sub: 21124371

```bash
Caused by:
  Missing output file(s) `SRS_curve.png` expected by process `SRSCURVE (1)`
```

we need another way to save the file to disk

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 0e05b3a64d9b45a6aa17cc9bdd755eecb4b04006
slurm sub: 21126858

```bash
```

### Todos for Tomorrow

- Class
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
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
  
### Git Commits

#### Labnotebook

```bash
a602315 - Benjamin Lorentz, Tue Apr 18 17:36:20 2023 -0400 : final notes for tues
328c6c4 - Benjamin Lorentz, Tue Apr 18 17:34:22 2023 -0400 : edits from tues
```

#### Visualize Ampliseq

```bash
0e05b3a - Benjamin Lorentz, Wed Apr 19 16:42:36 2023 -0400 : update srs curve
e9b57b1 - Benjamin Lorentz, Wed Apr 19 16:03:08 2023 -0400 : update srs_curve.r
8a0f8b7 - Benjamin Lorentz, Wed Apr 19 15:46:18 2023 -0400 : update main.nf
1a8fbe2 - Benjamin Lorentz, Wed Apr 19 15:26:03 2023 -0400 : update main.nf
b8bbe5d - Benjamin Lorentz, Wed Apr 19 15:09:13 2023 -0400 : update main.nf
b712f15 - Benjamin Lorentz, Wed Apr 19 14:49:19 2023 -0400 : update main.nf and add srs_curve.r
0758746 - Benjamin Lorentz, Tue Apr 18 17:33:07 2023 -0400 : update main.nf
f01ca1b - Benjamin Lorentz, Tue Apr 18 17:12:32 2023 -0400 : update main.nf
a202271 - Benjamin Lorentz, Tue Apr 18 16:57:05 2023 -0400 : update main.nf
```
  

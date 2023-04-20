---
title: 'Srs as Rmarkdown'
date: 2023-04-20T12:44:59Z
draft: false
meta_img: "images/image.png"
tags:
  - "one tag"
  - "another tag"
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
visualize ampliseq rev: 0e05b3a64d9b45a6aa17cc9bdd755eecb4b04006
slurm sub: 21126858

```bash
WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `QIIME is caching your current deployment for improved performance. This may take a few moments and should only happen once per deployment.
Plugin error from diversity:

  float division by zero

Debug info has been saved to /tmp/qiime2-q2cli-err-715t9fgc.log`, size: 258 (max: 255)

N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
lorentzben/visualize-ampliseq contains uncommitted changes -- cannot pull from repository
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 0e05b3a64d9b45a6aa17cc9bdd755eecb4b04006
slurm sub: 21170351

```bash
Caused by:
  Missing output file(s) `SRS_curve.png` expected by process `SRSCURVE (1)`
```

Time to transition to a Rmarkdown file

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: ac8acdf03c8b07c5de835ea4aa38bedb250c6bd1
slurm sub: 21177416

```bash
Debug info has been saved to /tmp/qiime2-q2cli-err-1alls8r8.log`, size: 258 (max: 255)

N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
lorentzben/visualize-ampliseq contains uncommitted changes -- cannot pull from repository
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: ac8acdf03c8b07c5de835ea4aa38bedb250c6bd1
slurm sub: 21180891

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
    File ".command.sh", line 55
      srs_command_pdf = 'Rscript -e "rmarkdown::render('srs_curve.rmd', output_file='/scratch/bjl34716/ade/cycle-4/srs_curve.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='/scratch/bjl34716/ade/cycle-4')"'
                                                        ^
  SyntaxError: invalid syntax

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/25/e9abe1d7589ffe0414ba00f25aca4e

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `  File "/scratch/bjl34716/ade/cycle-4/work/25/e9abe1d7589ffe0414ba00f25aca4e/.command.sh", line 55
    srs_command_pdf = 'Rscript -e "rmarkdown::render('srs_curve.rmd', output_file='/scratch/bjl34716/ade/cycle-4/srs_curve.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='/scratch/bjl34716/ade/cycle-4')"'
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 88655d91c0c263e96869d75b461b6d1fe29bf927
slurm sub: 21182716

```bash
Command error:
    File ".command.sh", line 55
      srs_command_pdf = "Rscript -e "rmarkdown::render('srs_curve.rmd', output_file='/scratch/bjl34716/ade/cycle-4/srs_curve.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='/scratch/bjl34716/ade/cycle-4')""
                                     ^
  SyntaxError: invalid syntax

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/ba/ad7519384f0f35b91ceab3057b4930
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 03d2368252b696ec85b423a06f58344d5bdbc9f7
slurm sub: 21186552

```bash
Command error:
    File ".command.sh", line 55
      srs_command_pdf = 'Rscript -e "rmarkdown::render('srs_curve.rmd', output_file='/scratch/bjl34716/ade/cycle-4/srs_curve.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='/scratch/bjl34716/ade/cycle-4')"'
                                                        ^
  SyntaxError: invalid syntax

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c8/ae8909f7888901b38e0efa4b4d1bb9

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `  File "/scratch/bjl34716/ade/cycle-4/work/c8/ae8909f7888901b38e0efa4b4d1bb9/.command.sh", line 55
    srs_command_pdf = 'Rscript -e "rmarkdown::render('srs_curve.rmd', output_file='/scratch/bjl34716/ade/cycle-4/srs_curve.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='/scratch/bjl34716/ade/cycle-4')"'
```
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: d75034fc62c895f68dce4e61baef7e6be4c2edf4
slurm sub: 21187646

```bash
```

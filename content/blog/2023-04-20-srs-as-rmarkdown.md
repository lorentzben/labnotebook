---
title: 'Srs as Rmarkdown'
date: 2023-04-20T12:44:59Z
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
visualize ampliseq rev: 71cbbb53bd7b9742fc30827d5ae111b3ab765b48 
slurm sub:  21189038

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
    File ".command.sh", line 55
      srs_command_pdf = 'Rscript -e 'rmarkdown::render("srs_curve.rmd", output_file="/scratch/bjl34716/ade/cycle-4/srs_curve.pdf", output_format="pdf_document", clean=TRUE, knit_root_dir="/scratch/bjl34716/ade/cycle-4")''
                                     ^
  SyntaxError: invalid syntax

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/13/5e8fb53c13d2d9c6a4c221e420589f

Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `  File "/scratch/bjl34716/ade/cycle-4/work/13/5e8fb53c13d2d9c6a4c221e420589f/.command.sh", line 55
    srs_command_pdf = 'Rscript -e 'rmarkdown::render("srs_curve.rmd", output_file="/scratch/bjl34716/ade/cycle-4/srs_curve.pdf", output_format="pdf_document", clean=TRUE, knit_root_dir="/scratch/bjl34716/ade/cycle-4")''
                                   ^
SyntaxError: invalid syntax`, size: 383 (max: 255)
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 6ab07fab1f0818c2efe3524d6576bf7b7aa8d8c6
slurm sub: 21191871 

```bash
Command error:
  
  
  processing file: srs_curve.rmd
  Quitting from lines 13-29 (srs_curve.rmd) 
  Error in read.table("srs_curve_val.txt") : no lines available in input
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.table
  Execution halted
  
  
  processing file: srs_curve.rmd
  Quitting from lines 13-29 (srs_curve.rmd) 
  Error in read.table("srs_curve_val.txt") : no lines available in input
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.table
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/aa/cb14e7ae5a1a7d16eca1e5a8cb3f3d
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: c1727215db988b197d906a8b6946a649220e7b0a
slurm sub: 21192644

```bash
Command error:
  
  
  processing file: srs_curve.rmd
  Quitting from lines 13-31 (srs_curve.rmd) 
  Error in read.table("srs_curve_val.txt") : no lines available in input
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.table
  Execution halted
  
  
  processing file: srs_curve.rmd
  Quitting from lines 13-31 (srs_curve.rmd) 
  Error in read.table("srs_curve_val.txt") : no lines available in input
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.table
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/4e/83b0658828f2efd2e1ca56482a4555

```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 4f8498ad73f8b8f77f8e643e9b639ea91e71609f
slurm sub: 21194275

```bash
Work dir:
  /scratch/bjl34716/ade/cycle-4/work/2f/8fc5941308a1b7e8dfdc36a51a18b4

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `

processing file: srs_curve.rmd
Quitting from lines 13-31 (srs_curve.rmd)
Error in read.table("srs_curve_val.txt") : no lines available in input
Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.table
Execution halted


processing file: srs_curve.rmd
Quitting from lines 13-31 (srs_curve.rmd)
Error in read.table("srs_curve_val.txt") : no lines available in input
Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.table
Execution halted`, size: 481 (max: 255)
```

If this doesnt work we can package the python code into a file and then just run everything through bash

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 80924dc17edc8ff382c1c624360366a002ccc3ad
slurm sub: 21197493

```bash
Command error:
  
  
  processing file: srs_curve.rmd
  Quitting from lines 13-31 (srs_curve.rmd) 
  Error in Artifact.export_data(srs_curve, "srs") : 
    could not find function "Artifact.export_data"
  Calls: <Anonymous> ... withVisible -> eval_with_user_handlers -> eval -> eval
  Execution halted
  
  
  processing file: srs_curve.rmd
  Quitting from lines 13-31 (srs_curve.rmd) 
  Error in Artifact.export_data(srs_curve, "srs") : 
    could not find function "Artifact.export_data"
  Calls: <Anonymous> ... withVisible -> eval_with_user_handlers -> eval -> eval
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/f9/6c068e3979a45e304d9142ee61c54f
```

cycle 4 rev: 7231674bae44c72efeb3274bf2af48afe36b7573
visualize ampliseq rev: 360f38d6e80035a24a168fbdbcccad5f30d85da5
slurm sub: 21201345

```bash
[ec/537f5a] process > SRSCURVE (1)                   [100%] 1 of 1 ✔

Completed at: 20-Apr-2023 15:16:45
Duration    : 5m 7s
CPU hours   : 1.1 (94.6% cached)
Succeeded   : 1
Cached      : 29
```

Success!!

#### SRS Normalization

I have the skeleton of a process set up which will take user-provided values or the min-value from the table. I need to pull the table in (either from qiime results or from the filtered NC), then I need to save the tsv, biom and qza formats.

### Todos for Tomorrow

- Class
  - HW 5
  - Course Eval
  - Paper?
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
c91b3a5 - Benjamin Lorentz, Thu Apr 20 12:08:35 2023 -0400 : added pre lunch notes
647cbf4 - Benjamin Lorentz, Thu Apr 20 08:53:30 2023 -0400 : added page for thursday
```

#### Visualize Ampliseq

```bash
360f38d - Benjamin Lorentz, Thu Apr 20 14:56:24 2023 -0400 : update srs curve
80924dc - Benjamin Lorentz, Thu Apr 20 14:27:39 2023 -0400 : update main.nf
4f8498a - Benjamin Lorentz, Thu Apr 20 14:01:48 2023 -0400 : fix the srs cmax command
c172721 - Benjamin Lorentz, Thu Apr 20 13:41:46 2023 -0400 : update render_srs and srs_curve rmd
6ab07fa - Benjamin Lorentz, Thu Apr 20 13:22:12 2023 -0400 : update main.nf
71cbbb5 - Benjamin Lorentz, Thu Apr 20 12:24:54 2023 -0400 : update main.nf
d75034f - Benjamin Lorentz, Thu Apr 20 12:07:12 2023 -0400 : update main.nf
03d2368 - Benjamin Lorentz, Thu Apr 20 11:47:06 2023 -0400 : update main.nf
bc82317 - Benjamin Lorentz, Thu Apr 20 11:29:32 2023 -0400 : update main.nf
88655d9 - Benjamin Lorentz, Thu Apr 20 11:11:44 2023 -0400 : update main.nf
ac8acdf - Benjamin Lorentz, Thu Apr 20 10:27:48 2023 -0400 : change srs_curve.r to rmd and update main.nf
```
---
title: 'Make Viz Ampliseq Work Again'
date: 2023-06-02T13:20:27Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "Mock"
  - "Module"
  - "primer-detect"
description: "Description for the page"
---

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - fix report 12 from 356-455 (12_report.Rmd)
  - Longitudinal Analysis By hand
    - Check out slurm 23139002
  - Email Dr. Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Ade

#### Longitudinal Analysis By hand

cycle 4 rev: 2068d8b3d18e3c2271bd0586a8aef4cebaa5bbb0
visualize ampliseq rev: de88954bb71d619fcb5cccf23db14c5f912dcf25
slurm job: 23153671

```bash
 label: ANOSIM analysis (with options)
  List of 5
   $ echo      : logi FALSE
   $ fig.height: num 8
   $ fig.width : num 10
   $ message   : logi FALSE
   $ warning   : logi FALSE


Command error:
  ✖ dplyr::filter()     masks stats::filter()
  ✖ dplyr::lag()        masks stats::lag()
  ✖ tidyr::pack()       masks Matrix::pack()
  ✖ dplyr::select()     masks MASS::select()
  ✖ tidyr::unpack()     masks Matrix::unpack()

  Attaching package: 'rstatix'

  The following object is masked from 'package:MASS':

      select

  The following object is masked from 'package:stats':

      filter
      Attaching package: 'kableExtra'

  The following object is masked from 'package:dplyr':

      group_rows


  Attaching package: 'ggpubr'

  The following object is masked from 'package:qiime2R':

      mean_sd

  Loading required package: permute

  Attaching package: 'permute'

  The following object is masked from 'package:gtools':

      permute

  The following object is masked from 'package:deldir':

      getCol

  Loading required package: lattice
  This is vegan 2.6-2
  Quitting from lines 356-455 (12_report.Rmd)
   Error in cl.vec[within] <- levels(grouping)[grouping[take]] :
    NAs are not allowed in subscripted assignments
  Calls: <Anonymous> ... withVisible -> eval_with_user_handlers -> eval -> eval -> anosim
  In addition: There were 50 or more warnings (use warnings() to see the first 50)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c3/bbe97f162031075d50196a299a282f
```

Something is wrong here...


cycle 4 rev: 2068d8b3d18e3c2271bd0586a8aef4cebaa5bbb0
visualize ampliseq rev: 85f7c5515b7951e258448cf76236a4aaa6a7ed88
slurm job: 23178435

```bash
  Loading required package: lattice
  This is vegan 2.6-2
  Quitting from lines 365-466 (12_report.Rmd)
  Error in cl.vec[within] <- levels(grouping)[grouping[take]] :
    NAs are not allowed in subscripted assignments
  Calls: <Anonymous> ... withVisible -> eval_with_user_handlers -> eval -> eval -> anosim
  In addition: There were 50 or more warnings (use warnings() to see the first 50)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c2/a59797081f1526a9217ccf6d844d66

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line



slurmstepd: error: *** JOB 23178435 ON a2-11 CANCELLED AT 2023-06-02T12:13:16 ***
```

cycle 4 rev: 2068d8b3d18e3c2271bd0586a8aef4cebaa5bbb0
visualize ampliseq rev: cad0477788d6c859b692f218993a0b1b4618f834
slurm job: 23179130

```bash
```




#### Email Dr. Ade
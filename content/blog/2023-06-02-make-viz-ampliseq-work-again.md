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

### Todos for Today

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


  Attaching package: 'kableExtra'

  The following object is masked from 'package:dplyr':

      group_rows

  Quitting from lines 140-171 (12_report.Rmd)
  Error in Eij * D^2 : non-conformable arrays
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> <Anonymous> -> PerMANOVAF -> apply
  In addition: Warning messages:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: In matrix(tree$edge[order(tree$edge[, 1]), ][, 2], byrow = TRUE,  :
    data length [4039] is not a sub-multiple or multiple of the number of rows [2020]
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/1d/e5081473fd26dce4c83e23cc8df2d9

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh
```
```

cycle 4 rev: 2068d8b3d18e3c2271bd0586a8aef4cebaa5bbb0
visualize ampliseq rev: 0230b78148bd5b05bad250cbeade98905ba1031b
slurm job: 23180389

```bash
```

Still waiting on this to finish


#### Email Dr. Ade

I sent the results to Dr. Ade for him to examine, unfortunately didn't have the longitudinal analysis complete, can upload later.

### Todos for Next Week

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Longitudinal Analysis By hand
    - Check out slurm 23139002
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Git Commit

#### Lab Notebook

```bash
0d2d726 - Benjamin Lorentz, Fri Jun 2 12:15:46 2023 -0400 : notes before lunch
dc1994a - Benjamin Lorentz, Fri Jun 2 09:22:07 2023 -0400 : added page for Friday
47af326 - Benjamin Lorentz, Thu Jun 1 17:03:12 2023 -0400 : final notes for thursday
```

#### Visualize Ampliseq

```bash
0230b78 - Benjamin Lorentz, Fri Jun 2 15:12:43 2023 -0400 : update lefse.nf
dfbf6a7 - Benjamin Lorentz, Fri Jun 2 13:22:26 2023 -0400 : update 12_report.Rmd
cad0477 - Benjamin Lorentz, Fri Jun 2 12:12:13 2023 -0400 : update 12_report.md
85f7c55 - Benjamin Lorentz, Fri Jun 2 11:09:49 2023 -0400 : update 12_report.md
```

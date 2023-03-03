---
title: 'Examine Ade Old Midterm'
date: 2023-03-03T15:21:33Z
draft: false
meta_img: "images/image.png"
tags:
  - "ade"
  - "nextflow"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Today

- Stat 6220 
  - midterm exam
- Ade 
  - review slurm 19590971
  - review slurm 19597932
  - send code 
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Midterm Exam

I want to run the practice exam and then I can do the real one.
Finished 35/40 for the first section not great not horrible. 

### Ade

#### Slurm 19597932 

automate_16_nf rev: 82bf6d435ddb6d4467708e21fc1920d57cd8ad11
cycle 4 rev: ce3cee01e5826dc2fb51eef86db5089eba069ab4
slurm sub: 19597932

```bash
[fb/c2d0ad] process > LefseFormat (1)                [100%] 1 of 1, failed: 1 ✘
Command error:
  ** R
  ** byte-compile and prepare package for lazy loading
  ** help
  *** installing help indices
  ** building package indices
  ** installing vignettes
  ** testing if installed package can be loaded from temporary location
  ** testing if installed package can be loaded from final location
  ** testing if installed package keeps a record of temporary installation path
  * DONE (jamba)
  Warning message:
  In library(package, lib.loc = lib.loc, character.only = TRUE, logical.return = TRUE,  :
    there is no package called ‘jamba’
  Loading required package: renv

  Attaching package: ‘renv’

  The following object is masked from ‘package:stats’:

      update

  The following objects are masked from ‘package:utils’:

      history, upgrade

  The following objects are masked from ‘package:base’:
  Loading required package: dplyr

  Attaching package: ‘dplyr’

  The following objects are masked from ‘package:stats’:

      filter, lag

  The following objects are masked from ‘package:base’:

      intersect, setdiff, setequal, union

  Loading required package: tibble
  Loading required package: qiime2R
  Loading required package: phyloseq
  Loading required package: jamba
  Error in read.table(file, header = F, col.names = coltitles, skip = 2,  :
    more columns than column names
  Calls: qza_to_phyloseq -> read_q2metadata -> read.table
  Execution halted
  mv: cannot stat 'lefse_formatted.txt': No such file or directory
```



#### Slurm 19590971


automate_16_nf rev: 82bf6d435ddb6d4467708e21fc1920d57cd8ad11
cycle 4 rev: 6ef9f022997aa62afb8526e88489b2fca2de5d80
slurm sub: 19590971

```bash
[f1/84aecf] process > LefseFormat (1)                [100%] 1 of 1, failed: 1 ✘
[-        ] process > LefseAnalysis                  -
[07/a0b050] process > ExportSetup (1)                [100%] 1 of 1 ✔
[-        ] process > GenerateReport                 -
Error executing process > 'LefseFormat (1)'

Caused by:
  Process `LefseFormat (1)` terminated with an error exit status (1)

Command executed:

  #!/usr/bin/env bash
  mkdir combos
  Rscript init_and_refresh.R
  cp day_21_cycle_4_metadata.tsv "metadata.tsv"
  Rscript qiime_to_lefse.R Treatment
  mv lefse_formatted.txt combos/

Command exit status:
  1

Command output:

  ✔  checking for file ‘/tmp/Rtmpo96XYn/remotes91e5136e7616/jbisanz-qiime2R-2a3cee1/DESCRIPTION’


  ─  preparing ‘qiime2R’:


     checking DESCRIPTION meta-information ...

  ✔  checking DESCRIPTION meta-information


  ─  checking for LF line-endings in source and make files and shell scripts


  ─  checking for empty or unneeded directories
     Omitted ‘LazyData’ from DESCRIPTION


  ─  building ‘qiime2R_0.99.6.tar.gz
  Command error:
  ** R
  ** byte-compile and prepare package for lazy loading
  ** help
  *** installing help indices
  ** building package indices
  ** installing vignettes
  ** testing if installed package can be loaded from temporary location
  ** testing if installed package can be loaded from final location
  ** testing if installed package keeps a record of temporary installation path
  * DONE (jamba)
  Warning message:
  In library(package, lib.loc = lib.loc, character.only = TRUE, logical.return = TRUE,  :
    there is no package called ‘jamba’
  Loading required package: renv

  Attaching package: ‘renv’

  The following object is masked from ‘package:stats’:

      update

  The following objects are masked from ‘package:utils’:

      history, upgrade
      The following objects are masked from ‘package:base’:

      load, remove

  Loading required package: dplyr

  Attaching package: ‘dplyr’

  The following objects are masked from ‘package:stats’:

      filter, lag

  The following objects are masked from ‘package:base’:

      intersect, setdiff, setequal, union

  Loading required package: tibble
  Loading required package: qiime2R
  Loading required package: phyloseq
  Loading required package: jamba
  Error in read.table(file, header = F, col.names = coltitles, skip = 2,  :
    more columns than column names
  Calls: qza_to_phyloseq -> read_q2metadata -> read.table
  Execution halted
  mv: cannot stat 'lefse_formatted.txt': No such file or directory
```

My qiime2lefse image is not working... I could generate a 2.0 version with all these items. 
I want to see if I have all the results to send to Dr. Ade

```r

library(dplyr)
library(tibble)
library(qiime2R)
library(phyloseq)
library(jamba)
```


PAUSE

We found the dirs that have the ade data in them:

C:\Users\bjl34716\Documents\Aggrey\rush\twenty_one\day_21_rarefaction_median_50_perc\qiime
C:\Users\bjl34716\Documents\Aggrey\rush\twenty_eight\day_28_revert_rarefaction_60_perc\qiime

We can package that all up for him and send it off. I do want to compare these results to the ones that I made with the new data. 

I started a draft email response but I have to turn the biom tables into tsv so I will do that first thing next week.

### Todos for Next Week

- Ade 
  - rebuild docker if you want to 
  - turn bioms into tsvs
  - send code and tables
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Git Commits

#### lab notebook

```bash
ebfb80e - Benjamin Lorentz, Fri Mar 3 10:23:56 2023 -0500 : added a page for friday
```
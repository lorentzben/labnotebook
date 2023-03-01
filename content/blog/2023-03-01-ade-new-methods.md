---
title: 'Ade New Methods'
date: 2023-03-01T16:40:06Z
draft: false
meta_img: "images/image.png"
tags:
  - "ade"
  - "nextflow"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Today

- Ade 
  - why is visualize ampliseq failing out?
  - set up the old pipeline analysis to send the feature table over
  - find out what version was last used 
  - send code 
- Stat 6220 
  - Review for Midterm
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
  
### Ade Analysis

#### 01 MBA issues

visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77 
cycle 4 rev: 44734efb931e4965db37ffc7f780990d97051048
slurm sub: 19537430

```bash
Command error:
  
  
  processing file: 01_report_MbA.Rmd
  Loading required package: phyloseq
  
  Attaching package: 'dplyr'
  
  The following objects are masked from 'package:stats':
  
      filter, lag
  
  The following objects are masked from 'package:base':
  
      intersect, setdiff, setequal, union
  
  Quitting from lines 38-113 (01_report_MbA.Rmd) 
  Error in `*tmp*`$dataSet : $ operator is invalid for atomic vectors
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> ApplyAbundanceFilter
  In addition: There were 37 warnings (use warnings() to see them)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/5a/e028b8aff01dec2a015fc2a4cc11ff
```

visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77 
cycle 4 rev: 9ab2240b65446a5cfd7d90031681de21d97e18e9
slurm sub: 19542293

```bash
Completed at: 01-Mar-2023 15:59:00
Duration    : 29m 11s
CPU hours   : 1.1 (0.8% cached)
Succeeded   : 25
Cached      : 1
```
Success!!

#### Old method

I have pulled revision 82bf6d435ddb6d4467708e21fc1920d57cd8ad11 onto the server in the ade folder, I need to figure out what kind of driver script I used. My guess is something like the yadav script. 

I then need to run the analysis with depths of 5000 and 6000 or 6000 and 70000...


### Todos for Tomorrow

- Ade 
  - set up the old pipeline analysis to send the feature table over
  - send code 
- Stat 6220 
  - Review for Midterm
  - Examine the Group Proposal
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

#### Lab Notebook

```bash
d5c4089 - Benjamin Lorentz, Wed Mar 1 11:41:23 2023 -0500 : added page for wednesday
```

#### cycle_4

```bash
088364c - Benjamin Lorentz, Wed Mar 1 16:59:00 2023 -0500 : added slurm-submission.sh
9ab2240 - Benjamin Lorentz, Wed Mar 1 14:17:51 2023 -0500 : update ade-cycle-4-nextflow
```
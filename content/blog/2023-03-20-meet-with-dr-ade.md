---
title: 'Meet With Dr Ade'
date: 2023-03-20T14:30:36Z
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

- Finalize Homework 3
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Run the same analysis with the Negative Controls to get out ahead of it. 
  - Meet with Dr. Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Meet With Dr. Ade

#### Questions I have for him 

Basically, we want to run the negative control data through and the positive control, then we can compare the abundances of the positive vs the expected (which we need from Dr. O) and then we can run an ANOVA type test to see if NC looks like our data or not. 

I did not process the negative control samples, I can process them but I need a little bit more information. 

- How were these Negative Controls constructed?
- What library was used for the positive controls?
  - https://docs.qiime2.org/2023.2/tutorials/quality-control/
  
#### Fix Visualize Ampliseq for drunk_kare

cycle 4 ref: 9b90edcb464dfbc84df6a709dddf69a74ee7b9a3 
slurm sub: 19919997

```bash
Command error:
  ✖ dplyr::lag()    masks stats::lag()

  Attaching package: 'kableExtra'

  The following object is masked from 'package:dplyr':

      group_rows

  Quitting from lines 156-161 (03_report_test.Rmd)
  Error in file(file, "rt") : cannot open the connection
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.csv -> read.table -> file
  In addition: Warning messages:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: Transformation introduced infinite values in discrete y-axis
  3: Transformation introduced infinite values in discrete y-axis
  4: In file(file, "rt") :
    cannot open file 'results/overall_summary.tsv': No such file or directory
  Execution halted
  
3d/61453e
```

I re-copied over the dir for day 21 and resubmitted the job:

cycle 4 ref: 9b90edcb464dfbc84df6a709dddf69a74ee7b9a3 
slurm sub: 19997406

```bash

```

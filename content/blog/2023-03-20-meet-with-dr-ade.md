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

### Dr. Ade

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
I had the directory structure incorrect
```

cycle 4 ref: 9b90edcb464dfbc84df6a709dddf69a74ee7b9a3 
slurm sub: 19998115

```bash
```

#### Meeting with Dr. Ade

Microshades and R package for Microbiome Data

Basically, we want to run the negative control data through and the positive control, then we can compare the abundances of the positive vs the expected (which we need from Dr. O) and then we can run an ANOVA type test to see if NC looks like our data or not. 

I did not process the negative control samples, I can process them but I need a little bit more information. 

- How were these Negative Controls constructed?
  - They were just the kit generated DNA
  - He wants me to run the data through and then filter those results from the dataset see:
  " Contaminant sequences were identified from extracted negative controls with the R package decontam and the probability threshold set to 0.5. After contaminant removal, samples with less than 1,000 sequences were removed"- https://www.frontiersin.org/articles/10.3389/fphys.2023.1083192/full
- What library was used for the positive controls?
  - https://docs.qiime2.org/2023.2/tutorials/quality-control/
  - Email Sent
  
He wants me to examine the litter samples to see if the same mess of PCoAs etc exist.
This is on another sheet in the sample-sheet google doc. 


### Set up Ade Litter Analysis

I will make the metadata and mapping file, but then we will have to add a process for the decontam package. 


### Todos for Tomorrow

- Finalize Homework 3
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Set up analysis for Litter samples
  - figure out where to implement a filtering step
  - How does the other Ben's Analysis line up with mine/ampliseq?
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

#### Lab Notebook

```bash
8b83c16 - Benjamin Lorentz, Mon Mar 20 14:58:30 2023 -0400 : notes after dr ade meet
1ad9dd6 - Benjamin Lorentz, Mon Mar 20 13:39:50 2023 -0400 : updates to the mock samples run
e15d9e9 - Benjamin Lorentz, Mon Mar 20 10:33:27 2023 -0400 : add page for Monday
```

#### Cycle 4

```bash
003b380 - Benjamin Lorentz, Mon Mar 20 16:56:00 2023 -0400 : add litter dir
```



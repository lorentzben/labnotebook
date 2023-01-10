---
title: 'Downstream'
date: 2023-01-10T15:36:39Z
draft: false
meta_img: "images/image.png"
tags:
  - "jackwood"
  - "visualize-ampliseq"
  - "rarefaction"
description: "Description for the page"
---

### Todos for Today:

- Visualize Ampliseq
  - !!! update all downstream diversities !!!
- Read notes for stat class for tomorrow
- Generate a Mock community M&M or other and validate pipelines
- Examine some papers collected

### Question for This Week:

Can we use a mock community to describe the common taxa in the different chicken gut segments AND can we use that community to benchmark the pipeline we have developed?

### Visualize Ampliseq

#### Report 04

error from last run 

```bash
Quitting from lines 32-54 (04_report_test.Rmd) 
  Error in names(x) <- value : 
    'names' attribute [2] must be the same length as the vector [1]
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> colnames<-
  In addition: Warning message:
```

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: 075d8807eb9f2b69a44f5c4724f65867649767c0
slurm sub: 16877183

```bash
success
```

#### Report 05

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: 58d595edc1d741f1c7e051767f964fa438919e5f 
slurm sub: 16888071

```bash
processing file: 05_report.Rmd
  Quitting from lines 40-65 (05_report.Rmd) 
  Error in `[[<-.data.frame`(`*tmp*`, ioi, value = integer(0)) : 
    replacement has 0 rows, data has 86
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> [[<- -> [[<-.data.frame
  In addition: Warning messages:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  Execution halted

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/97/73bbcf2785b3b3260349aa9a9c785c
```

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: db84f6228eb2061b36d9c4ebd47907efe9782ae7
slurm sub: 16890528

```bash
processing file: 05_report.Rmd
  Quitting from lines 40-65 (05_report.Rmd) 
  Error in `[[<-.data.frame`(`*tmp*`, ioi, value = integer(0)) : 
    replacement has 0 rows, data has 86
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> [[<- -> [[<-.data.frame
  In addition: Warning messages:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  Execution halted

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/bc/8ca08941b51c77f67b159309e34b59

```

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: 600a0eec54a65a29ed1daf5457a4d5713bcdb53f
slurm sub: 16897071

```bash
succeeded
```

#### Report 06

Succeeded

#### Report 07

We need to add a process in [for this](https://docs.qiime2.org/2022.11/plugins/available/diversity/alpha-rarefaction/) to be fed into 07_report, and this can be implemented using Python


#### Report 08

Not needed

#### Report 09

Completed

#### Report 10

Completed

#### Report 11

Not needed

#### Report 12

Not needed

#### Report 13

Not Needed

### Stat 6220


Took a look at the correlation information


### Todos for Tomorrow:

- Visualize Ampliseq
  - implement the alpha-rarefaction curve
  - update path in 07 report
- Generate a Mock community M&M or other and validate pipelines
- Examine some papers collected

### Git Commits

#### Lab Notebook

```bash
db93696 - Ben Lorentz, Tue Jan 10 17:15:52 2023 -0500 : updates for tuesday
575bfe3 - Ben Lorentz, Tue Jan 10 09:10:59 2023 -0500 : added page for tuesday
```

#### Visualize Ampliseq

```bash
600a0ee - Ben Lorentz, Tue Jan 10 16:18:05 2023 -0500 : update 05_report
db84f62 - Ben Lorentz, Tue Jan 10 15:07:55 2023 -0500 : updated main.nf and report 05
58d595e - Ben Lorentz, Tue Jan 10 14:34:03 2023 -0500 : update main.nf and 05_report.md
075d880 - Ben Lorentz, Tue Jan 10 10:59:15 2023 -0500 : update 04_report

```
---
title: Roadmap to Break
author: Ben Lorentz
date: '2022-12-07'
slug: roadmap-to-break
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Visualize Ampliseq (STALE)
  - examine slurm run 15474870
- Host microbiome interaction
  - new paper
  
### Tasks for the next 1.5 weeks

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- re-watch the lecture for ChIP-seq

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

  
### Visualize Ampliseq

#### Examine slurm run 15474870

slurm: 15474870
revision: e30e26195d9d0d6995879e32ab9daac179d9cdb6

```bash
[21/db14bf] process > UNCOMPRESSDIVMATS (1)          [100%] 1 of 1, failed: 1 ✘

  > # make jaccard div matrix
  > jaccard <- qiime2R::read_qza("jaccard2.qza")

Command error:
  Error in qiime2R::read_qza("jaccard2.qza") :
    Input artifact (jaccard2.qza) not found. Please check path and/or use list.files() to see files in current working directory.
  Execution halted
```

I fixed the path of jaccard in the uncompress diversity

slurm: 15704770
visualize-ampliseq revision: d2ecdf1c899166f9676943e4b6c6a9662645da29
ampliseq-benchmark revision: f1acf1d8aa4d02c792db3254b040dd7a76cc2d7b

```bash
processing file: 10_report.Rmd
  Quitting from lines 39-56 (10_report.Rmd) 
  Error in split.default(x = seq_len(nrow(x)), f = f, drop = drop, ...) : 
    group length is 0 but data length > 0
  Calls: <Anonymous> ... split.data.frame -> lapply -> split -> split.default
  In addition: Warning message:
  In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  Execution halted

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/a6/141ac4e7be97260ba0e75058b5ef5f

#Submitted : .command.run : 15707183

Work dir: 
/scratch/bjl34716/nf_dev/ampliseq-benchmark/work/b9/34d33169fbfedf2939aeb51a21caea
```

We could make a conda env to store nextflow in so we don't have to ML it

TODO we need to find the boxplots from diversity, or modify the uncompress diversity or add a new process

### Todos for Tomorrow:

- Visualize Ampliseq 
  - check diverity for boxplot visualization
  - modify uncompress diverity
  - add a new process for boxplot
- Host microbiome interaction
  - new paper
  
### Git Commits

#### Lab Noteboook

```bash
863b53e - Benjamin Lorentz, Wed Dec 7 09:56:17 2022 -0500 : page for wednesday
```

#### Visualize-Ampliseq

```bash
c5f3ab1 - Benjamin Lorentz, Wed Dec 7 17:02:42 2022 -0500 : Updated 10_report.md
d2ecdf1 - Benjamin Lorentz, Wed Dec 7 15:13:12 2022 -0500 : Fix filepaths uncomress_diversity.r
```

#### Ampliseq Benchmark

```bash
15c33da - Benjamin Lorentz, Wed Dec 7 15:31:05 2022 -0500 : Modify slurm-sub-(low,med,high)
f1acf1d - Benjamin Lorentz, Wed Dec 7 15:22:23 2022 -0500 : Update slurm-sub-med.sh
```

---
title: '2023 03 21 Ade Analysis'
date: 2023-03-21T15:05:47Z
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
  
### Ade Analysis

#### Generate Mapping file

cycle 4 ref: 0d6a567f20bb2f6d5aee1992553f45206ea8d998
slurm sub: 20041248

```bash
Error executing process > 'NFCORE_AMPLISEQ:AMPLISEQ:RENAME_RAW_DATA_FILES (LT107)'

Caused by:
  Process `NFCORE_AMPLISEQ:AMPLISEQ:RENAME_RAW_DATA_FILES` input file name collision -- There are multiple input files for each of the following file names: 11-28_S347_L001_R2_001.fastq.gz


Tip: you can try to figure out whats wrong by changing to the process work dir and showing the script file named .command.sh
```

cycle 4 ref: 95a8d59b88e834c0d7dcf49c4535c5f0650bd51b
slurm sub: 20041288

```bash
```

### Filtering Table for contataminates

1. we have to unzip a qza either naturally or we can use qiime2r in R
2. we need the package Decontam and filter out taxa identified in the negative controls
3. turn this back into a qza and pass it into the rest of the process

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
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
f44528c - Benjamin Lorentz, Tue Mar 21 11:07:08 2023 -0400 : add page for tuesday
00a7ab8 - Benjamin Lorentz, Mon Mar 20 16:58:04 2023 -0400 : added notes for the end of monday
```

#### cycle 4

```bash
95a8d59 - Benjamin Lorentz, Tue Mar 21 16:16:08 2023 -0400 : update mapping file
0d6a567 - Benjamin Lorentz, Tue Mar 21 16:12:59 2023 -0400 : rename driver script
7e6e811 - Benjamin Lorentz, Tue Mar 21 16:11:31 2023 -0400 : update driver script
850e57d - Benjamin Lorentz, Tue Mar 21 15:35:19 2023 -0400 : added mapping file for litter
003b380 - Benjamin Lorentz, Mon Mar 20 16:56:00 2023 -0400 : add litter dir
```
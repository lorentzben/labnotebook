---
title: 'Implement Decontam'
date: 2023-03-24T14:30:42Z
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
  
### Ade

from yesterday:

#### Function to Filter the Contamination out

1. Create a function
2. Pull table in 
  2a. Read QZA -> phyloseq
3. Pull in file with the sampleIDs of the NC samples
4. How does decontam work?
5. Output Filtered table
  5a. QZA/phyloseq -> QZA/TSV for downstream analysis
6. Replace former table.qza files with filtered file.
  6a. OPT filter out Mock communities if applicable
  
cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: 54f6f11e7135e78a11d4e98376b5ce94a4e25576
slurm sub: 20076228

```bash

```
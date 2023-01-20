---
title: 'Examining Huang'
date: 2023-01-20T15:21:10Z
draft: false
meta_img: "images/image.png"
tags:
  - "metagenome assembled genome"
  - "MAGs"
  - "huang"
description: "Description for the page"
---

### Todos for today

- gg-catalog
  - examine the Huang table
    - examine methods
    - examine results
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Huang

495 samples from 5 compartments (dudodenum, jejunum, ileum, cecum and colorectum)
9.04 million non-redundant genes, with an average open reading frame (ORF) length of 697 bp.
Used CAMRA3 for tax classification 
able to classify ~ 99% of genes to kingdom level
Genus ~ 26%
Species ~ 2.29%

For their co-occurance network they used the 285 samples older than 40 days at the genus level 

I was able to load the relative abundance tables into R in a way that makes sense to me.

git commit 5b319da9c4cea442477055d89a9f75557311c152

```bash
add 02_huang and data/huang-2018/*

    - added code to load the huang relative abundace tables into memory
    - TODO separate col/rows out by tissue type
    - TODO compare these results to the Zhang results
```

I want to see if in the future it makes sense to try to recreate the abundance calculation (in the supps) with the long read data so that we could see if the rel abund values are similar. 

### Todos for next week

- gg-catalog
  - Huang
    - separate out tissue types
    - redo the diversity calcs to see if they are the same
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
  
### Git Commits

#### Lab Notebook

```bash
6613826 - Benjamin Lorentz, Fri Jan 20 10:22:25 2023 -0500 : page for friday
```

#### gg-catalog

```bash
5b319da - Benjamin Lorentz, Fri Jan 20 16:56:36 2023 -0500 : add 02_huang and data/huang-2018/*
```
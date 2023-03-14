---
title: 'Restarting With Kegg'
date: 2023-03-14T12:59:24Z
draft: false
meta_img: "images/image.png"
tags:
  - "huang2018"
  - "Kegg"
  - "peptidase"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - finish downloading Huang 2018 dataset
  - Find out which Kegg genes are involved in Nitrogen Metabolism
  - Generate a gene network 
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### gg-catalog

#### Downloading the Huang 2018 data

While waiting for the data to download, I wanted to start to look into what is dietary protein and what kind of Kegg IDs should I be looking for:

There is a good chart of [protein degradation](https://www.kegg.jp/pathway/map=map04974&keyword=peptidase) and then from there here are some of the good keggs to examine. 

### Genes that are involved in nitrogen metabolism


I think going through the gene ID pretty useful, but I want to make sure that the abundances match up with the table in 03.profiles/02.relative.KEGG.abundance/*.ratio


### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Find out which Kegg genes are involved in Nitrogen Metabolism
    - examine printed pathways
  - Generate a gene network 
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Git Commits

#### Lab Notebook

```bash
5892367 - Benjamin Lorentz, Tue Mar 14 09:00:53 2023 -0400 : added page for tuesday
```

#### gg-catalog

```bash
607d65a - Benjamin Lorentz, Tue Mar 14 16:58:38 2023 -0400 : update code/03_huang_kegg_examine.sh
efaead4 - Benjamin Lorentz, Tue Mar 14 15:26:58 2023 -0400 : added rnotebook and word doc
```
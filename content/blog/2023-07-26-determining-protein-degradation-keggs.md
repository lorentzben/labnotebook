---
title: 'Determining Protein Degradation Keggs'
date: 2023-07-26T13:24:44Z
draft: false
meta_img: "images/image.png"
tags:
  - "microbiome-review"
  - "kegg ontology network"
  - "gg-catalog"
description: "Description for the page"
---

### Todos for Today

- gg-catalog
  - Identify KEGG pathways that deal with Protein Metabolism/Nitrogen metabolism
  
- Read papers about microbiome analysis

- STAT 6315
  - Watch Module 13
  - Finish Module 13 Homework
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
 
### gg-catalog

Based on the meeting on Monday (7-24) we need to find the list of Keggs who have to do with protien degradation, I think the best goal would be to start with [this map](https://www.kegg.jp/kegg-bin/show_pathway?ko04974) and follow it from crude protein to products. 

There are 20 amino acids, humans can generate 11 of them but 9 must be consumed through diet, they are the essential amino acids. [source](https://www.healthline.com/health/protein-digestion)

- all amino acids synthesized in humans are derived from the intermediates in glycolosis, the citric acid cycle or pentose phosphate pathway [source](https://www.slideshare.net/SonaliGadge3/amino-acid-pathway)

Two important enzymes are amylase and lipase, though they mostly break down carbohydrates and fat, I am curious to see if they break down ammino acids at all? [source](https://www.healthline.com/health/protein-digestion)

There are a bunch of types of amino acids (over 500) but alpha amino acids are the ones we think of. [source](https://en.wikipedia.org/wiki/Amino_acid)

I have a preliminary list of keggs to look into, we might want to add the build up processes too (anabolism) since there could be some interchange between AAs.

### Todos for Tomorrow

- gg-catalog
  - Identify KEGG pathways that deal with Protein Metabolism/Nitrogen metabolism
  
- Read papers about microbiome analysis

- Reply to Shailes 

- STAT 6315
  - Watch Module 13
  - Finish Module 13 Homework
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation

### Git commits

#### Lab Notebook

```bash
7255040 - Benjamin Lorentz, Wed Jul 26 12:37:10 2023 -0400 : notes before lunch
a592e1e - Benjamin Lorentz, Wed Jul 26 09:33:19 2023 -0400 : add page for wednesday
```

#### gg-catalog

```bash
fa168fa - Benjamin Lorentz, Wed Jul 26 17:06:06 2023 -0400 : add data/nitrogen-degradation-kegg-pathways.tsv
```

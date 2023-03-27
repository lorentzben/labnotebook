---
title: 'Decontam Implement'
date: 2023-03-27T14:43:20Z
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
  - Check ASV count to the dada2 table 
    - Alternativley use the dada2 table
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

#### Import, Phyloseq-ize and then export tsv table

Do this the proper way, https://joey711.github.io/phyloseq/import-data.html I have been doing too much hacky solutions right now.

I need to have the biom format package right now
https://github.com/joey711/biomformat

I was able to update the docker image to include biom format and it is now lorentzb/decontam:1.2 I have a feeling since the file was not a biom hd5 loaded format it won't be able to write it correctly, but we can try and if not save a TSV and then convert to hd5. 

#### TSV, BIOM-ize and QZA table

#### Update downstream table qzas

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Check ASV count to the dada2 table 
    - Alternativley use the dada2 table
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
  
### Git Commit

#### lab notebook

```bash
c03cc23 - Benjamin Lorentz, Mon Mar 27 14:51:12 2023 -0400 : notes midday monday
535ce4f - Benjamin Lorentz, Mon Mar 27 10:45:19 2023 -0400 : added page for monday
```

#### visualize ampliseq

```bash
af816c0 - Ben Lorentz, Mon Mar 27 15:44:30 2023 -0400 : update renv
e8251a0 - Benjamin Lorentz, Mon Mar 27 14:52:47 2023 -0400 : added build
562201c - Benjamin Lorentz, Mon Mar 27 14:50:14 2023 -0400 : update contam script
```


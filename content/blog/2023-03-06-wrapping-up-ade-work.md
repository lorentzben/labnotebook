---
title: 'Wrapping Up Ade Work'
date: 2023-03-06T14:09:58Z
draft: false
meta_img: "images/image.png"
tags:
  - "ade"
  - "nextflow"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Today

- Submit TAP docs
- Ade 
  - rebuild docker if you want to 
  - turn bioms into tsvs
  - send code and tables
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Ade Work

#### Turn bioms into TSVs

I was able to build a docker image and a script that turns biom and tax info into a csv, the git revision is: 4559a5cf67dbc64ffb9ca85528bce69d2fdb6d4e in the repo https://github.com/lorentzben/cycle-4

### Ben Jackwood

Ben came by to ask what amount of computing power we would need to run the whole blast and then parser pipeline. I suggested we test a local blast query to see if it is memory or processor limited. I also suggested he and Brian look into a NAS or other data vault type solution. 

### Regmi

Dr. Regmi came by to ask about how to start going about training a new student in microbiome work and if there's a class. I suggested he start with rosalind and then build into the moving pictures tutorial for QIIME2, and then that I built a pipeline to analyse and visualize the results. He also suggested that Dr. Fairchild has a Sr level undergrad course where you go out into houses and processing sites, or that he is teaching a welfare course in the springs that would be good to audit for some background. 

### Todos for Tomorrow


- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Git Commits

#### Lab Notebook

```bash
4559a5c - Benjamin Lorentz, Mon Mar 6 16:26:02 2023 -0500 : update script to join tax to table
7e70b42 - Benjamin Lorentz, Mon Mar 6 11:34:16 2023 -0500 : add uncompressed biom files
d0a5ad3 - Benjamin Lorentz, Mon Mar 6 11:22:50 2023 -0500 : re-structure old method directory
```

#### Cycle 4

```bash
9edc7df - Benjamin Lorentz, Mon Mar 6 14:51:07 2023 -0500 : notes after ben jackwood and regmi
7aed9cb - Benjamin Lorentz, Mon Mar 6 09:11:27 2023 -0500 : add page for monday
```
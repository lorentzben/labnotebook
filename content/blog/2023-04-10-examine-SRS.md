---
title: 'Examine SRS'
date: 2023-04-10T14:56:45Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
  - "normalize"
description: "Description for the page"
---

### Todos for Today

- Class
  - Examine Comments on Word Doc
  - Homework 4
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
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

#### What Does FIGARO need?

I updated the figaro docker image to:
1. enter a bash setting
2. include procps

I have pushed this to lorentzb/figaro:1.0 

cycle 4 rev: 374b13a9b92c744712ec095c038608b7ad8d046c
visualize ampliseq rev: 70d8f4f2904bdf309f0fb012913bc8827822fe3b
slurm sub: 20874558

I was able to run figaro and have some sense of parsing the results the issue comes from passing those results into the paramfiles or others. Maybe we need a small driverscript that will edit the paramfile to include the cutoffs if they are generated, and will read in the json file from figaro.

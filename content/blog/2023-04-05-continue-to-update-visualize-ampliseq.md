---
title: 'Continue to Update Visualize Ampliseq'
date: 2023-04-05T14:21:17Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
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
  - Fix Downstream Uses of table with filtered
    - ORDIOI issue
    - Update 10
    - Update 12
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

#### Fix the order ioi method

Currently the method will read in the ordered IOI if provided, but it fails to write it out to file, so I want to go by hand and see what the issue is, and then update the code.

cycle 4 rev: e4cda0d877e7f7a9a1c695be00a3f9d445830311
visualize ampliseq rev: ac114e300c20aa9f02b36c14d21ad1888d3ff090
slurm sub: 20735135

```bash
Completed at: 05-Apr-2023 11:53:54
Duration    : 27m 8s
CPU hours   : 1.2 (36.6% cached)
Succeeded   : 17
Cached      : 9
```

#### Update Report 10 

#### Update Report 12

#### 6b NMDS Plots

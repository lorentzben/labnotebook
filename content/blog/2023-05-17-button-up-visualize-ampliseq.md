---
title: 'Button Up Visualize Ampliseq'
date: 2023-05-17T12:22:23Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
  - "Module"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish Modularization
    - Yes SRS No NC Yes Mock Yes Rarefaction
    - Remove TODOs
  - Taguchi optmization for richness?
  - Make these subworkflows as opposed to one long workflow?
  - Unit tests based on the example data
  - Positive Control Analysis
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
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

#### Test All Use Cases

Yes SRS No NC Yes Mock Yes Rarefaction

cycle 4 rev: a66a53047ceeda98c28c02d7c3a1aa7788bf4960
visualize ampliseq rev: 558b4af7e4dca29d90550a07998d9da730f73130
slurm job: 22873906

```bash
Completed at: 16-May-2023 17:06:24
Duration    : 17m 12s
CPU hours   : 2.1 (74.3% cached)
Succeeded   : 4
Cached      : 29
```

#### Remove TODOs

Done

#### Update References in 14

Done check revision: eddd6a3f44ff5fa01636d6acce36bcde3bbc8c89

#### Taguchi optmization for richness

We Don't really need to use taguchi, we can just plot a table/array

Interesting results, first SRS will produce the average richest measurement, and will keep similar number of samples which we like. I feel like SRS is a robust method to move forward with.


#### Check output 

Based on rev: b5cb1caba1d39fc0218304356c9e8cedbb917b45

#### Mock Community Samples


### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Check updated output analysis
  - Positive Control Analysis
  - Mock Community Investigation
  - Run a proper analysis to send to Ade
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
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

#### Lab notebook

```bash
7961a66 - Benjamin Lorentz, Wed May 17 11:59:34 2023 -0400 : notes before lunch
f3ce8a3 - Benjamin Lorentz, Wed May 17 08:46:44 2023 -0400 : add page for wednesday
```

#### Visualize Ampliseq

```bash
b5cb1ca - Benjamin Lorentz, Wed May 17 13:49:20 2023 -0400 : update conf and main.nf
eddd6a3 - Benjamin Lorentz, Wed May 17 11:57:13 2023 -0400 : update 14 citations
```
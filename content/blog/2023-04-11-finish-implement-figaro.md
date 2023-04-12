---
title: 'Finish Implement Figaro'
date: 2023-04-11T14:56:03Z
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
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Make a script to parse figaro cutoffs and edit the param files
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

#### Figaro Driver Script

Is there a python package to parse YAML files?

Yes it is called pyaml and I have it installed in lorentzb/figaro:1.2 

cycle 4 rev: a0d5d49488705468a68a817b31e9352b831e95bf 
visualize ampliseq rev: 9eb6cb85ee329c5e40eb399c36c71046f78f08b2
slurm job: 20933907

```bash
```


### Todos for Tomorrow

- Class
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - examine figaro results
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

### Git commits

#### Lab Notebook

```bash
50125a9 - Benjamin Lorentz, Tue Apr 11 10:56:52 2023 -0400 : add page for tuesday
```

#### Cycle 4
```bash
a0d5d49 - Benjamin Lorentz, Tue Apr 11 17:07:25 2023 -0400 : update litter params, figaro batch and viz params
8452fca - Benjamin Lorentz, Tue Apr 11 16:54:19 2023 -0400 : update figaro find
f933b0f - Benjamin Lorentz, Tue Apr 11 16:34:11 2023 -0400 : add figaro-find
```

#### Visualize Ampliseq

```bash
9eb6cb8 - Ben Lorentz, Tue Apr 11 12:10:11 2023 -0400 : added dependencies for figaro parser
```

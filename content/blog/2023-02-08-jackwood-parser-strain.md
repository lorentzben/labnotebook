---
title: 'Jackwood Parser Strain'
date: 2023-02-08T15:21:52Z
draft: false
meta_img: "images/image.png"
tags:
  - "jackwood blast"
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - implement the two xml parsers
  - create a new dict that holds isolate counts
  - meet with Ben to talk about two points above 2/9/23
- gg-catalog
  - Zhang
    - follow up on slurm process 18610239
    - create a minimap process (either concat or separate)
      - read about what a meta map is and if we can implement it
    - check for read loss (does it match the paper?)
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
  
### Jackwood Blast Parser

#### Implement the xml parsing

Of note, you do not reassign a dict when you add a value to the list, you just append just like any other list.

Strain and isolate are the two fields, what we are going to want to do is to assign the val of isolate and if it is nonetype then we want to pull strain:

(just do this opposite of how you did the nones)

#### Generate the new dictionary


### gg-catalog-nf

#### What is happening with slurm-18610239

We need to map the output from indexing?
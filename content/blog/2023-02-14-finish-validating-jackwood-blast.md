---
title: 'Finish Validating Jackwood Blast'
date: 2023-02-14T13:23:31Z
draft: false
meta_img: "images/image.png"
tags:
  - "jackwood blast"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - fix the joining of the percent id and query tables and writing them out
  - fix the tag for 1.2 so that it has the xml parser in it. (no strain data)
  - validate the strain table again
  - rm strain table param
- gg-catalog
  - Zhang
    - follow up on slurm process 18670379 (2/9/23)
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

#### fix the percent query and percent identity

I think we want to make a function that takes a dict of list of tuples and turns it into a dataframe and then we can join the dataframes based on taxa AND strain.
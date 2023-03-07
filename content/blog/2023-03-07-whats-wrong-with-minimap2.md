---
title: 'What's Wrong With Minimap2'
date: 2023-03-07T13:56:43Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---


### Todos for Today


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
  
### gg-catalog-nf

#### Minimap2 by hand

From 02-23:

It's weird that the mapped reads do not decrease at all, I am going to look through the logfiles to see what it says. 

What was the original data labeled as?

So maybe my mapping was the issue? 

```bash
minimap2 chicken_and_feed_genomes.fa Duodenum.fq.gz -o Duodenum.fq.gz.host.paf  -x map-hifi -t 40 
```

I want to look at this command vs the one the pipeline completed and see what the difference is. 
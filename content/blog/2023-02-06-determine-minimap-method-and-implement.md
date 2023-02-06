---
title: 'Determine Minimap Method and Implement'
date: 2023-02-06T14:12:08Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Next Week

- Jackwood Blast
  - add in the isolate field into parser and output
  - meet with Ben to talk about two points above 2/2/23
- gg-catalog
  - Zhang
    - followup on slurm-18229634
    - try to incorporate the -c flag when samtools merging to see if the filesize is the same as concat
    - create a minimap process (either concat or separate)
      - create a channel/process for each screening reference
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
  
### gg-catalog-nf

#### slurm process 18229634

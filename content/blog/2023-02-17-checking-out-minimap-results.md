---
title: 'Checking Out Minimap Results'
date: 2023-02-17T13:55:09Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - examine slurm 19101810
    - create a minimap process (either concat or separate)
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

#### slurm results 19101810

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: a7ec8c326a14a81a9aef1a218e7dc16168b12c03
slurm sub: 19101810

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2O15xKthBGS8oB
executor >  slurm (7)
[ba/34a78b] process > FILTLONG (SRR19732514)       [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)           [100%] 1 of 1, cached: 1 ✔
[d5/0b8e76] process > MINIMAP2_ALIGN (SRR19683890) [100%] 7 of 7 ✔
Completed at: 16-Feb-2023 19:55:43
Duration    : 3h 15m 38s
CPU hours   : 418.4 (82.7% cached)
Succeeded   : 7
Cached      : 8
```

So we have 7 sucessful bam files generated. I think the next step is to make some fast/q/a files from the bams so that we can [compare the counts to the original and filtlong values](https://lorentznotebook.netlify.app/blog/2023-02-01-minimap2-implement/). 
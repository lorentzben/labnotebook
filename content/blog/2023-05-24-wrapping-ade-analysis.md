---
title: 'Wrapping Ade Analysis'
date: 2023-05-24T13:56:42Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "Mock"
  - "Module"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
  - Run a proper analysis to send to Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.

### Ade

#### Picking proper parameters

In report 01, I want to double check the headines to make sure they are correct, and not right up against anything



cycle 4 rev: 122e6ebf4ff816c8d3743207ad3bc357fc232379
visualize ampliseq rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job:  22998938

```bash
```

Table 3 Note this is to the least rich sample, not the final analysis. 

Table 4 Note, this is from the proper rardepth, so like 3 but updated and only diversity.

Report 05 check how the adjusting p-value make sense

cycle 4 rev: 862562856bb047aeef4ca08bdd05a469d0063f2b
visualize ampliseq rev: a1bdb51bc10ca4fec1d7bc75e4e398b91ed60bf8
slurm job: 22997178

```bash
Completed at: 24-May-2023 11:15:08
Duration    : 1m 7s
CPU hours   : 1.9 (100% cached)
Succeeded   : 0
Cached      : 44
```



Who was filtered out of the negative control analysis?



What was the accuracy of the mock analysis?

[] Re-run the analysis with HQ and New Visualize ampliseq?
[] figure out what primers are present?
  - https://github.com/linsalrob/primer-trimming
  - https://github.com/OpenGene/fastp
  - 
[] re-run with cutadapt

#### Ben's Other analysis

What steps did he take?

What steps do I take?



#### Longitudinal Analysis

See if it makes a difference in this specific analysis. 

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Try to detect the primers present
  - Use cutadapt to remove primers
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
  - Run a proper analysis to send to Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.

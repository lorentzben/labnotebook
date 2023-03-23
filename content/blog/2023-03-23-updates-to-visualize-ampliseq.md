---
title: 'Updates to Visualize Ampliseq'
date: 2023-03-23T12:39:15Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "automate_16_nf"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - fix the rarefaction function
  - figure out where to implement a filtering step
  - How does the other Ben's Analysis line up with mine/ampliseq?
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

#### Updates to Visualize Ampliseq

From Yesterday (3/22)
  
```bash
maxdepth=$(count_table_minmax_reads.py filtered-table.tsv maximum 2>&1)

#check values
if [ "$maxdepth" -gt "75000" ]; then maxdepth="75000"; fi
if [ "$maxdepth" -gt "5000" ]; then maxsteps="250"; else maxsteps=$((maxdepth/20)); fi
```
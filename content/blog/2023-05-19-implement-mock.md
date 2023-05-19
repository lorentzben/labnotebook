---
title: 'Implement Mock'
date: 2023-05-19T12:30:12Z
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

### Ade

#### Diagnose Filterseqs

So we are having an issue with filtering the sequences we should go back and use the steps outlied by the qiime forum:

```md

You can take your existing feature-table and rep-seqs.qza file that you got from Deblur or DADA2 and work from there.

    Filter the samples you want from your feature table using the filter-sample 11 plugin.
    Use the new filtered table to remove sequences from your rep-seqs.qza file with the filter-seqs 8 plugin.
    Then you can build your new tree with this new rep-seqs file. You can also use the fragment-insertion plugin for tree building.
```
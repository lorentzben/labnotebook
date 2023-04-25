---
title: 'Ade Local SRS'
date: 2023-04-25T13:42:54Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
  - "STAT 6220"
description: "Description for the page"
---

### Todos for Today

- Class
  - Paper?
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Set up a local analysis on small data while Sapelo2 is under maintenece
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

#### Local Analysis

cycle 4 rev:

```bash
Use DADA2 taxonomy classification
ERROR: Please check input samplesheet -> Forward read FastQ file does not exist!
/mnt/c/Users/bjl34716/Documents/Aggrey/ade/1-21_S265_L001_R1_001.fastq.gz
```


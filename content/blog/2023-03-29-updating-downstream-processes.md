---
title: 'Updating Downstream Processes'
date: 2023-03-29T14:29:19Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Tomorrow

- Class
  - read over Ellie's sections
  - what can I write? 
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
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

#### Update downstream table qzas

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: f9bbdb7e376aeb21aaf4b4f22eeeb8485a6004e1
slurm job: 20372443

```bash
WARN: Failed to publish file: /scratch/bjl34716/ade/cycle-4/work/92/ce1a11981556e5d4260bee05f6ef7f/13_report_28-03-2023_17.45.58.html; to: /work/sealab/bjl34716/ade/cycle-4/litter/html/13_report_28-03-2023_17.45.58.html [copy] -- See log file for details
Completed at: 28-Mar-2023 17:46:35
Duration    : 51m 5s
CPU hours   : 1.6 (7.4% cached)
Succeeded   : 21
Cached      : 7
```

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: f9bbdb7e376aeb21aaf4b4f22eeeb8485a6004e1
slurm job: 20430469

```bash
```


### Update The rarefaction report Rmd file to use the QIIME Tables
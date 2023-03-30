---
title: 'Send Some Results to Ade'
date: 2023-03-30T12:28:02Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
description: "Description for the page"
description: "Description for the page"
---

### Todos for Today

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

#### Dig up old revisions and run with rarefact so that I can send something while I continue to work

cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: df62a69b9f614cd51ec08cd3fde4899e01d40668
slurm sub: 20072884

```bash
Completed at: 23-Mar-2023 14:06:33
Duration    : 2m 5s
CPU hours   : 1.6 (97.9% cached)
Succeeded   : 4
Cached      : 22
```

The previous visualize ampliseq rev was  6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77


cycle 4 rev: 078b239b1945f8f7c61fb602bb3b06654927209b
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20450743

```bash
Error executing process > 'NFCORE_AMPLISEQ:AMPLISEQ:MULTIQC'

Caused by:
  /work/sealab/bjl34716/ade/cycle-4/litter/multiqc: Disk quota exceeded



WARN: Failed to render execution report -- see the log file for details
WARN: Failed to render execution report -- see the log file for details
WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value:
````

cycle 4 rev: 078b239b1945f8f7c61fb602bb3b06654927209b
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20452442

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
lorentzben/visualize-ampliseq contains uncommitted changes -- cannot pull from repository
(END)
```

cycle 4 rev: 078b239b1945f8f7c61fb602bb3b06654927209b
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20452496

```bash
```


#### Clean Up Work Dir

13847 directories, 87758 files

I am pulling all previous analyses out of the work dir and moving to the lacie drive.




#### Update downstream table qzas

### Update The rarefaction report Rmd file to use the QIIME Tables

### Class

#### Read Ellies writing

#### What Can I do?
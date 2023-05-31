---
title: 'Continuing Ade Report'
date: 2023-05-31T14:03:34Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "Mock"
  - "Module"
  - "primer-detect"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - compare fastp and prinseq analyses
    - examine slurm 23044970
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
  - Longitudinal Analysis By hand
  - Email Dr. Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Ade

#### Compare fastp and prinseq analyses

examine slurm 23044970

cycle 4 rev:  369a02f3135fdce9bd6b5c744f52a8758063f59c
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23044970

```bash
Completed at: 26-May-2023 14:22:38
Duration    : 42m 11s
CPU hours   : 2.3 (0.2% cached)
Succeeded   : 43
Cached      : 1
```

I'm not convinced that this is a better result so I think we'll just go with what we have and ask if they filtered out primers


#### How does the other Ben's Analysis line up with mine/ampliseq?

- keep ee < 2
- trunc q < 30 
- silva 138 used for database
- ASV with count < 5 removed 
- rarefied to 1,000 seqs
- range 1,769 - 93,023

- ASV not present in more than 0.1% relative abundance in any sample
- Core microbiome: RA > 0.1% and present in 80% of samples

cycle 4 rev: 76e16cedb95dbf821ce064c2a70ff3db3a0f864c
visualize ampliseq rev: d8cfbe9871bfd3ae8add451c7547e0475a91e167
slurm job: 23135527

```bash
```

#### Updated Params with Ben Z's params


#### Longitudinal Analysis By hand

#### Email Dr. Ade
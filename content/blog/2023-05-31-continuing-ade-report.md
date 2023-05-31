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


#### Updated Params with Ben Z's params

ycle 4 rev: 76e16cedb95dbf821ce064c2a70ff3db3a0f864c
visualize ampliseq rev: d8cfbe9871bfd3ae8add451c7547e0475a91e167
slurm job: 23135527

```bash
Waiting files transfer to complete (1 files)
Completed at: 31-May-2023 14:27:43
Duration    : 1h 4m 15s
CPU hours   : 4.1 (0.2% cached)
Succeeded   : 42
Cached      : 2
```

Based on the results they look similar faith pd comes back significant, but otherwise they're the same. Can offer as a result but not needed. 

#### Longitudinal Analysis By hand

examining the code here: https://docs.qiime2.org/2023.5/tutorials/pd-mice/#longitudinal-analysis

We need an ampliseq run for day 7 to day 28 so I setup an analysis for that:

cycle 4 rev: 681d1bd138828175a89c9c9b8a904f56c0f9d906
visualize ampliseq rev: d8cfbe9871bfd3ae8add451c7547e0475a91e167
slurm job: 23139002

```bash
```

#### Email Dr. Ade

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Longitudinal Analysis By hand
    - Check out slurm 23139002
  - Email Dr. Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Git Commits

#### Lab Notebook

```bash
ce12035 - Benjamin Lorentz, Wed May 31 13:12:24 2023 -0400 : notes before lunch
7979ff8 - Benjamin Lorentz, Wed May 31 10:11:03 2023 -0400 : add page for wednesday
1a695a8 - Benjamin Lorentz, Tue May 30 17:07:01 2023 -0400 : final notes for Tuesday
```

#### Cycle 4

```bash
681d1bd - Benjamin Lorentz, Wed May 31 16:12:44 2023 -0400 : add driver and paramfile for all samples
54d3f44 - Benjamin Lorentz, Wed May 31 15:59:27 2023 -0400 : added all sample metadata and mapping for longitudinal analysis
76e16ce - Benjamin Lorentz, Wed May 31 12:02:13 2023 -0400 : add paramfiles for ben z param analysis
2d7183c - Benjamin Lorentz, Tue May 30 16:54:12 2023 -0400 : add report and update markdown file
```


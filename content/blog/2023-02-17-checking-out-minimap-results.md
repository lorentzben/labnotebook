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

### Turn bams to fastq

I pulled the [modules for fastq and fasta](https://nf-co.re/modules/samtools_fastq) and added a call to generate these files. 

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 4f49b6cedbcfa5ded78f6b94384638e6e53d1823
slurm sub: 19160219

```bash
I recognized that it will be underpowered CANCELLED
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: fd4c2fbd5b8e666db09bf625cbc8880f86e4bd6a
slurm sub: 19165713

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2jvbZKqRQWBgni
executor >  slurm (14)
[1d/c59eb7] process > FILTLONG (SRR19726169)       [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)           [100%] 1 of 1, cached: 1 ✔
[92/5bf0c7] process > MINIMAP2_ALIGN (SRR19736685) [100%] 7 of 7, cached: 7 ✔
[1b/0c1f89] process > SAMTOOLS_FASTQ (SRR19683890) [100%] 7 of 7 ✔
[d6/5f86d5] process > SAMTOOLS_FASTA (SRR19736685) [100%] 7 of 7 ✔
Completed at: 17-Feb-2023 16:17:57
Duration    : 2h 27m 7s
CPU hours   : 652.8 (64.1% cached)
Succeeded   : 14
Cached      : 15
```

The next step is to count the fastq reads. Like I did on 2/1

### Todos for Next Week

- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
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

### Git Commits

#### Lab Notebook

```bash
ed3062f - Benjamin Lorentz, Fri Feb 17 16:38:16 2023 -0500 : updated the cheatsheet
f289fdb - Benjamin Lorentz, Fri Feb 17 12:02:56 2023 -0500 : update link
e235eb0 - Benjamin Lorentz, Fri Feb 17 12:01:42 2023 -0500 : does this link work?
a73d27c - Ben Lorentz, Fri Feb 17 08:56:39 2023 -0500 : added page for friday
```

#### gg-catalog-nf

```bash
fd4c2fb - Benjamin Lorentz, Fri Feb 17 13:48:26 2023 -0500 : update main.nf
61ee5ad - Benjamin Lorentz, Fri Feb 17 13:47:37 2023 -0500 : update conf/modules.config
52fcaab - Benjamin Lorentz, Fri Feb 17 13:30:34 2023 -0500 : update main.nf
4f49b6c - Benjamin Lorentz, Fri Feb 17 13:27:00 2023 -0500 : update main.nf
070f47a - Benjamin Lorentz, Fri Feb 17 11:51:56 2023 -0500 : update main.nf
```




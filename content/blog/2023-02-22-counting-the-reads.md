---
title: 'Counting the Reads'
date: 2023-02-22T15:20:07Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---

### Todos for Today

- Stat 6220 
  - Homework 2
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

### gg-catalog-nf 

#### Counting the filtlong reads 

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 6fe044998088738457fd11cf3cd5de0d1d8b21b7
slurm sub: 19286289

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process 'SEQKIT_STATS' has been already used -- If you need to reuse the same component include it with a different name or include in a different workflow context

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 146 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 5ea2982f2b59bf9b32df8ed99c47eb08f5761eff
slurm sub: 19293940

```bash
file    format  type    num_seqs        sum_len min_len avg_len max_len Q1      Q2      Q3      sum_gap N50     Q20(%)  Q30(%)
SRR19726169.fastq.gz    FASTQ   DNA     516348  8512378786      2016    16485.7 44765   14341.0 15704.0 17869.0 0       16183   99.21   98.07
SRR19683891.fastq.gz    FASTQ   DNA     2730287 22192490145     2000    8128.3  46626   4742.0  7160.0  10575.0 0       9776    98.91   97.40
SRR15214153.fastq.gz    FASTQ   DNA     1965108 33312767376     2000    16952.1 52396   12960.0 15963.0 19852.0 0       17616   98.03   95.27
SRR19732514.fastq.gz    FASTQ   DNA     2126922 35601162605     2006    16738.3 50018   14438.0 15918.0 18250.0 0       16470   98.68   96.76
SRR19732729.fastq.gz    FASTQ   DNA     1914473 35535370004     2008    18561.4 50558   15000.0 17367.0 21045.0 0       18627   98.26   95.90
SRR19736685.fastq.gz    FASTQ   DNA     4240693 72100323222     2000    17002.0 53591   14331.0 16109.0 18784.0 0       16851   98.68   96.83
SRR19683890.fastq.gz    FASTQ   DNA     3896255 75237772044     2008    19310.3 63490   15551.0 18188.0 22018.0 0       19533   98.28   95.85
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 39b179f275bf370c815e848e1e4d6ecf01ce1e9a
slurm sub: 19296050

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SEQKIT_STATS_UNMAP` declares 1 input channel but 5 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 163 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 2537741a5a74fe577dde7bca18d3594fdd31791b
slurm sub: 19296556

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process 'CSVTK_CONCAT_FILT' has been already used -- If you need to reuse the same component include it with a different name or include in a different workflow context

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 179 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 946dee686609739d24ac6afacd414ccd14a34331
slurm sub: 19296667

```bash
Error executing process > 'CSVTK_CONCAT_UNMAP (filtlong)'

Caused by:
  Process `CSVTK_CONCAT_UNMAP` input file name collision -- There are multiple input files for each of the following file names: SRR19736685.tsv, SRR19683890.tsv, SRR19732729.tsv, SRR19732514.tsv, SRR19726169.tsv, SRR19683891.tsv, SRR15214153.tsv


Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`
```
```

I just need to make 3 separate calls 

### Todos for Tomorrow

- Stat 6220 
  - Homework 2
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - make 3 separate fastq calls
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
  
### Git Commit

#### labnotebook

```bash
36aed83 - Benjamin Lorentz, Wed Feb 22 10:21:32 2023 -0500 : add page for wednesday
```

#### gg-catalog-nf

```bash
946dee6 - Benjamin Lorentz, Wed Feb 22 14:25:13 2023 -0500 : update main.nf
2537741 - Benjamin Lorentz, Wed Feb 22 14:23:02 2023 -0500 : update main.nf
39b179f - Benjamin Lorentz, Wed Feb 22 14:14:21 2023 -0500 : update main.nf
5ea2982 - Benjamin Lorentz, Wed Feb 22 13:40:34 2023 -0500 : update main.nf
6fe0449 - Benjamin Lorentz, Wed Feb 22 11:40:22 2023 -0500 : update main.nf
```

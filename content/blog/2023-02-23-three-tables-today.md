---
title: 'Three Tables Today'
date: 2023-02-23T13:16:01Z
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

Happy Friday

### Todos for Today

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

### gg-catalog-nf

#### Separate or Remap the Reads for Seqkit 

I want to modify the metadata for each read so that it states what type they are, then the table should be correct. 

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 0c202599448cda61896570e856beb271ba82696d
slurm sub: 19326742

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [cranky_mayer] DSL2 - revision: 0c20259944 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 4f5c83df9af997b66974ed6d826697b1fb6aba2e
slurm sub: 19326743

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [angry_tuckerman] DSL2 - revision: 4f5c83df9a [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: eba549f9069703d6c66b18e6dbe183528805acdb
slurm sub: 19326745

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [furious_snyder] DSL2 - revision: eba549f906 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 7560da66143350a5fc75ed1fdcb9370ad87ae06e
slurm sub: 19326746 

```bash
[[id:null], /scratch/bjl34716/nf_dev/gg-catalog/work/92/490bbcd0f5e22b883dcb8b2e06e089/SRR15214153_1.fastq.gz]
[[id:null], /scratch/bjl34716/nf_dev/gg-catalog/work/1b/0c1f89fe288219fc5aebe953301d12/SRR19683890_1.fastq.gz]
[[id:null], /scratch/bjl34716/nf_dev/gg-catalog/work/25/d1bf493b0e3b34154bbf84ce73d490/SRR19683891_1.fastq.gz]
[[id:null], /scratch/bjl34716/nf_dev/gg-catalog/work/e3/1cfd621dc4a104f060ae6b8b521228/SRR19726169_1.fastq.gz]
[[id:null], /scratch/bjl34716/nf_dev/gg-catalog/work/4c/e5c6778c4ee9fe3c2e2e2e4656879e/SRR19732729_1.fastq.gz]
[[id:null], /scratch/bjl34716/nf_dev/gg-catalog/work/03/84e265db9bbb72a00e49ec49866c22/SRR19736685_1.fastq.gz]
[[id:null], /scratch/bjl34716/nf_dev/gg-catalog/work/f3/d17dcd68305bf94cedeb4b4e48df69/SRR19732514_1.fastq.gz]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: ad803ccf5fdd8b37f233654b93a1d77a640ca5e9
slurm sub: 19326748

```bash
Unknown method invocation `String` -- Did you mean?
  toString
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: fa59d383c6d6fdc3b536e37ee3b8e68195d71118
slurm sub: 19326749

```bash
Invalid method invocation `toString` with arguments:

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 167 or see '.nextflow.log' file for more details
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: f82bc3bd645a30a07a58b83b696b0f1b98e25ab7
slurm sub: 19326753

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [pensive_crick] DSL2 - revision: f82bc3bd64 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 98d88918de0879f0d63a139383f917e219a4331e
slurm sub: 19326754

```bash
[[id:fastq-SRR19683890], /scratch/bjl34716/nf_dev/gg-catalog/work/1b/0c1f89fe288219fc5aebe953301d12/SRR19683890_1.fastq.gz]
[[id:fastq-SRR15214153], /scratch/bjl34716/nf_dev/gg-catalog/work/92/490bbcd0f5e22b883dcb8b2e06e089/SRR15214153_1.fastq.gz]
[[id:fastq-SRR19683891], /scratch/bjl34716/nf_dev/gg-catalog/work/25/d1bf493b0e3b34154bbf84ce73d490/SRR19683891_1.fastq.gz]
[[id:fastq-SRR19732729], /scratch/bjl34716/nf_dev/gg-catalog/work/4c/e5c6778c4ee9fe3c2e2e2e4656879e/SRR19732729_1.fastq.gz]
[[id:fastq-SRR19736685], /scratch/bjl34716/nf_dev/gg-catalog/work/03/84e265db9bbb72a00e49ec49866c22/SRR19736685_1.fastq.gz]
[[id:fastq-SRR19726169], /scratch/bjl34716/nf_dev/gg-catalog/work/e3/1cfd621dc4a104f060ae6b8b521228/SRR19726169_1.fastq.gz]
[[id:fastq-SRR19732514], /scratch/bjl34716/nf_dev/gg-catalog/work/f3/d17dcd68305bf94cedeb4b4e48df69/SRR19732514_1.fastq.gz]
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 7106182dd2cf9cfc1e027329d9a3fc98923366a8
slurm sub: 19326757

```bash
bjl34716@ss-sub3 code$ less /scratch/bjl34716/nf_dev/gg-catalog/work/23/3db5c8f418e324911d195819af36a0/filtlong.tsv
file    format  type    num_seqs        sum_len min_len avg_len max_len Q1      Q2      Q3      sum_gap N50     Q20(%)  Q30(%)
SRR15214153_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19683890_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19732729_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19683891_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19732514_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19736685_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19726169_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR15214153_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19683890_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19732729_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19683891_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19726169_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19732514_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19736685_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00    0.00
SRR19726169_other.fastq.gz      FASTQ   DNA     516348  8512378786      2016    16485.7 44765   14341.0 15704.0 17869.0 0       16183   99.21   98.07
SRR19683891_other.fastq.gz      FASTQ   DNA     2730287 22192490145     2000    8128.3  46626   4742.0  7160.0  10575.0 0       9776    98.91   97.40
SRR15214153_other.fastq.gz      FASTQ   DNA     1965108 33312767376     2000    16952.1 52396   12960.0 15963.0 19852.0 0       17616   98.03   95.27
SRR19732729_other.fastq.gz      FASTQ   DNA     1914473 35535370004     2008    18561.4 50558   15000.0 17367.0 21045.0 0       18627   98.26   95.90
SRR19732514_other.fastq.gz      FASTQ   DNA     2126922 35601162605     2006    16738.3 50018   14438.0 15918.0 18250.0 0       16470   98.68   96.76
SRR19736685_other.fastq.gz      FASTQ   DNA     4240693 72100323222     2000    17002.0 53591   14331.0 16109.0 18784.0 0       16851   98.68   96.83
SRR19683890_other.fastq.gz      FASTQ   DNA     3896255 75237772044     2008    19310.3 63490   15551.0 18188.0 22018.0 0       19533   98.28   95.85
```

```bash
filename	read lost in filtlong	per read loss in filtlong	read lost in minimap	per read loss in minmap
SRR19726169.fastq	5057	0.97%	0	0.00%
SRR15214153.fastq	19282	0.97%	0	0.00%
SRR19683890.fastq	37453	0.95%	0	0.00%
SRR19683891.fastq	142030	4.94%	0	0.00%
SRR19732514.fastq	20994	0.98%	0	0.00%
SRR19732729.fastq	18220	0.94%	0	0.00%
SRR19736685.fastq	41509	0.97%	0	0.00%
```

It's weird that the mapped reads do not decrease at all, I am going to look through the logfiles to see what it says. 

What was the original data labeled as?

So maybe my mapping was the issue? 

```bash
minimap2 chicken_and_feed_genomes.fa Duodenum.fq.gz -o Duodenum.fq.gz.host.paf  -x map-hifi -t 40 
```

### Todos for Next Week

- Stat 6220 
  - Homework 2 (ask prof about last question)
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
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
7f3629a - Benjamin Lorentz, Thu Feb 23 15:55:20 2023 -0500 : updated notes for thurs
fb89814 - Benjamin Lorentz, Thu Feb 23 08:18:59 2023 -0500 : page for thursday
```

#### gg-catalog-nf

```bash
ce88e8c - Benjamin Lorentz, Thu Feb 23 15:37:40 2023 -0500 : update main.nf
7106182 - Benjamin Lorentz, Thu Feb 23 09:33:33 2023 -0500 : update main.nf
98d8891 - Benjamin Lorentz, Thu Feb 23 09:28:34 2023 -0500 : update main.nf
f82bc3b - Benjamin Lorentz, Thu Feb 23 09:27:01 2023 -0500 : update main.nf
fa59d38 - Benjamin Lorentz, Thu Feb 23 09:22:56 2023 -0500 : update main.nf
ad803cc - Benjamin Lorentz, Thu Feb 23 09:20:58 2023 -0500 : update main.nf
07573ff - Benjamin Lorentz, Thu Feb 23 09:19:41 2023 -0500 : update main.nf
7560da6 - Benjamin Lorentz, Thu Feb 23 09:18:26 2023 -0500 : update main.nf
eba549f - Benjamin Lorentz, Thu Feb 23 09:16:59 2023 -0500 : update main.nf
4f5c83d - Benjamin Lorentz, Thu Feb 23 09:15:02 2023 -0500 : update main.nf
0c20259 - Benjamin Lorentz, Thu Feb 23 09:13:08 2023 -0500 : update main.nf
```
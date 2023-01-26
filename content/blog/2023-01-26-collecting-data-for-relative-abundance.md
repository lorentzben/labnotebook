---
title: 'Collecting Data for Relative Abundance'
date: 2023-01-26T13:22:24Z
draft: false
meta_img: "images/image.png"
tags:
  - "metagenome assembled genome"
  - "MAGs"
  - "zhang"
  - "relative abundance"
  - "nextflow"
description: "Description for the page"
---

### Todos for Today

- Homework 1 Stat 6220
- gg-catalog
  - Zhang
    - collect data
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Summarize info for meeting with Aggrey

### gg-catalog

#### collecting Zhang data

gg-catalog rev: 65129682fde2019a1c5b2fa0cd01d6d2a52f6a6a 
gg-catalog-nf rev: a9ac6237aa894be7d44250f06a52b03395349636
slurm sub: 17890397

```bash
Disk quota exceeded
```

gg-catalog rev: 5c61b0802f5c075cc358ef6b61e13ab8ad94d9c9
gg-catalog-nf rev: a9ac6237aa894be7d44250f06a52b03395349636
slurm sub: 17915854

```bash
```

We have a duo sequence we can look into SRR19683891

The goal is to filter the data with the params:
requiring read lengths over 2 kb and average read accuracy over 99%

We also need to keep track of how many reads we have at the start and then after filering and then after that we need to align with minimap 2

A tool that looks like it can handle this is [FiltLong](https://github.com/rrwick/Filtlong):

filtlong --min_length 2000 --keep_percent 99  input.fastq.gz | gzip > output.fastq.gz

I built a docker image for filtlong, and pushed it to lorentzb/filtlong:1.0

I am going to build a minimap2 image also; Done

#### Developing workflow for the generation of clean reads

There is an error with locale and bash for the filtlong image. We could either build a conda img or put a conda in a docker img to try to fix this if its a problem with nextflow...

https://anaconda.org/bioconda/filtlong

```bash
Singularity> filtlong --min_length 2000 --keep_percent 99 ../zhang/reads/duodenum/SRR19683891.fastq | gzip > SRR19683891.fastq.gz

Scoring long reads
  2872317 reads (22416650091 bp)

Filtering long reads
  target: 22192483590 bp
  keeping 22192490145 bp

Outputting passed long reads
```

I was able to get the reads filtered by hand, next is minimap2
The process gets killed interactivly needs more memory. My thought is to index the files and save the indexes somewhere so that they can just be downloaded and used. 

### Todos for Tomorrow

- Homework 1 Stat 6220
- gg-catalog
  - Zhang
    - collect data
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Summarize info for meeting with Aggrey

### Git Commits

#### Lab Notebook

```bash
bae7529 - Benjamin Lorentz, Thu Jan 26 08:25:22 2023 -0500 : added page for thursday
a9d2ced - Benjamin Lorentz, Wed Jan 25 16:49:29 2023 -0500 : notes for the end of wednesday
```

#### gg-catalog

```bash
d38d5cf - Benjamin Lorentz, Thu Jan 26 15:33:15 2023 -0500 : update 00_collect_data.sh
5c61b08 - Benjamin Lorentz, Thu Jan 26 08:21:15 2023 -0500 : updated 00_collect_data
```

#### gg-catalog-nf

```bash
32f86f9 - Benjamin Lorentz, Thu Jan 26 16:25:46 2023 -0500 : updated readme and main.nf
c3c6a5e - Benjamin Lorentz, Thu Jan 26 11:23:06 2023 -0500 : update filtlong dockerfile
1a1de81 - Benjamin Lorentz, Thu Jan 26 10:53:06 2023 -0500 : update main.nf add dockerfiles
```


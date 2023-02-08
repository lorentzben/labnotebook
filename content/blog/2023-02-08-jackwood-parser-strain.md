---
title: 'Jackwood Parser Strain'
date: 2023-02-08T15:21:52Z
draft: false
meta_img: "images/image.png"
tags:
  - "jackwood blast"
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - implement the two xml parsers
  - create a new dict that holds isolate counts
  - meet with Ben to talk about two points above 2/9/23
- gg-catalog
  - Zhang
    - follow up on slurm process 18610239
    - create a minimap process (either concat or separate)
      - read about what a meta map is and if we can implement it
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
  
  
### Jackwood Blast Parser

#### Implement the xml parsing

Of note, you do not reassign a dict when you add a value to the list, you just append just like any other list.

Strain and isolate are the two fields, what we are going to want to do is to assign the val of isolate and if it is nonetype then we want to pull strain:

(just do this opposite of how you did the nones)

So I seem to be able to make the strain dictionary and have it retun,

TODO:
  1. confirm the strain counts sum to the whole IBV Count
  2. Merge the strain dicts like the species dicts
  3. make sure merged strain dict gets printed to file
  4. Make sure database gets updated with strain and species info 
  
I've got something that saves a result that makes some sense to disk, next up is to validate it. Git Commit 9dc35dd1fda1b40a853cd76f19b9599b2a5c62e8

#### Generate the new dictionary


### gg-catalog-nf

#### What is happening with slurm-18610239

We need to map the output from indexing?

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 480361d1c9e2f273bbfbe290d489a985f1a28940
slurm sub: 18653067

```bash
Command error:
  [WARNING] Indexing parameters (-k, -w or -H) overridden by parameters used in the prebuilt index.
  [WARNING] For a multi-part index, no @SQ lines will be outputted. Please use --split-prefix.
  [M::main::89.264*0.20] loaded/built the index for 507 target sequence(s)
  [M::mm_mapopt_update::92.256*0.22] mid_occ = 500
  [M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 507
  [M::mm_idx_stat::94.054*0.24] distinct minimizers: 113152470 (39.56% are singletons); average occurrences: 6.599; average sp$  [E::sam_parse1] no SQ lines present in the header
  [W::sam_read1_sam] Parse error at line 1758
  samtools sort: truncated file. Aborting
  [main_samview] fail to read the header from "-".

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/6e/e19ee64235abd1b4773ed0316cea27
  
#I removed the index

rm -rf /scratch/bjl34716/nf_dev/gg-catalog/work/fa/8985309130258a2e58dc2c8d66168e
```

### Todos for Tomorrow

- Jackwood Blast
  - meet with Ben to talk about two points above 2/9/23
  - validate the strain table
  - add strain table param
  - strain more info table?
- gg-catalog
  - Zhang
    - follow up on slurm process 18653067
    - create a minimap process (either concat or separate)
      - read about what a meta map is and if we can implement it
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
37f5c3e - Benjamin Lorentz, Wed Feb 8 12:08:15 2023 -0500 : added notes before lunch
45709f3 - Benjamin Lorentz, Wed Feb 8 10:23:47 2023 -0500 : add page for wednesday
662eab9 - Benjamin Lorentz, Tue Feb 7 17:39:40 2023 -0500 : notes for the end of tuesday
```

#### gg-catalog-nf

```bash
480361d - Benjamin Lorentz, Wed Feb 8 15:43:12 2023 -0500 : update main.nf
e127897 - Benjamin Lorentz, Tue Feb 7 17:35:32 2023 -0500 : update main.nf
8dca95c - Benjamin Lorentz, Tue Feb 7 17:32:55 2023 -0500 : update main.nf
358a425 - Benjamin Lorentz, Tue Feb 7 17:28:28 2023 -0500 : update main.nf \n print out the reads first to see what the issue is
dc8f550 - Benjamin Lorentz, Tue Feb 7 17:22:12 2023 -0500 : update modules.config
```

#### jackwood_blast_parser

```bash
9dc35dd - Benjamin Lorentz, Wed Feb 8 17:17:47 2023 -0500 : update blast_parser.py
```
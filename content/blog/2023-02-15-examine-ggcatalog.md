---
title: 'Examine Ggcatalog'
date: 2023-02-15T15:30:29Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - follow up on slurm process 18670379 (2/9/23)
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
  
### gg-catalog-nf

#### examin slurm 18670379 (2/9/23)

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 480361d1c9e2f273bbfbe290d489a985f1a28940
slurm sub: 18670379

```bash
Command error:
  [WARNING][1;31m Indexing parameters (-k, -w or -H) overridden by parameters used in the prebuilt index.[0m
  [WARNING][1;31m For a multi-part index, no @SQ lines will be outputted. Please use --split-prefix.[0m
  [M::main::63.751*0.23] loaded/built the index for 507 target sequence(s)
  [M::mm_mapopt_update::67.003*0.27] mid_occ = 500
  [M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 507
  [M::mm_idx_stat::69.171*0.29] distinct minimizers: 113152470 (39.56% are singletons); average occurrences: 6.599; average spacing: 5.372; total length: 4011685380
  [E::sam_parse1] no SQ lines present in the header
  [W::sam_read1_sam] Parse error at line 1758
  samtools sort: truncated file. Aborting
  [main_samview] fail to read the header from "-".

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/7d/00357575ad21eaf2c570d99e676a00
```

The filtering and indexing steps worked fine, but the align step failed. I want to pass the concatenated fasta in as opposed to the index. 

#### Pass reads in as opposed to index

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: ad53d79ad2690e43ab66d0da6e6832b8aa2c80c6
slurm sub: 19014151

```bash
[[id:combined, single_end:true], [/scratch/bjl34716/gg-catalog/refs/concat-gal-zea-glycine.fna.gz]]
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fas$[[id:combined, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/fa/8985309130258a2e58dc2c8d66168e/concat-gal-zea-gly$Execution cancelled -- Finishing pending tasks before exit
[[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.fas$Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/minimap2/align/main.nf' at line: 2 $
[a3/c70037] Cached process > FILTLONG (SRR19732729)
```

I need to map the reads like I did for the other channels

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 402c280b9d0c3f465ca48092daf356f60660fdb0
slurm sub: 19015137

```bash
Command error:
  [M::mm_idx_gen::75.742*1.60] collected minimizers
  [M::mm_idx_gen::82.654*1.95] sorted minimizers
  [WARNING][1;31m For a multi-part index, no @SQ lines will be outputted. Please use --split-prefix.[0m
  [M::main::82.654*1.95] loaded/built the index for 507 target sequence(s)
  [M::mm_mapopt_update::85.186*1.92] mid_occ = 500
  [M::mm_idx_stat] kmer size: 19; skip: 19; is_hpc: 0; #seq: 507
  [M::mm_idx_stat::86.603*1.91] distinct minimizers: 203018761 (87.88% are singletons); average occurrences: 1.970; average spacing: 10.030; total length: 4011685380
  [E::sam_parse1] no SQ lines present in the header
  [W::sam_read1_sam] Parse error at line 1678
  samtools sort: truncated file. Aborting
  [main_samview] fail to read the header from "-".

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/c2/bc40ecc6bc16c600c007d9641b1bc9
```

What is the --split-prefix?



gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 37a7a60e144fccc14ef18c70b5e16a4351d20532
slurm sub: 19018732

```bash
 minimap2 \
      -ax map-hifi --split-prefix \
      -t 6 \
      "concat-gal-zea-glycine.fna.gz" \
      "SRR15214153.fastq.gz" \
       \
      -L \
      -a | samtools sort | samtools view -@ 6 -b -h -o SRR15214153.bam
      
Command error:
  [ERROR] failed to open file '6': No such file or directory
  samtools sort: failed to read header from "-"
  [main_samview] fail to read the header from "-".

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/97/52995fc0450b0c4af69a6ded78df8f

```

Based on [this github reply](https://github.com/lh3/minimap2/issues/548#issuecomment-580545383) I think you need to tell the minimap what to call the prefixes. 

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 0274457dfb83a74a26d4d0edb9d9b1f73e1e0066
slurm sub: 19020095

```bash

```

It seems that minimap2 is happy with this parameter submission

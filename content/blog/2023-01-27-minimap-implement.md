---
title: '2023 01 27 Minimap Implement'
date: 2023-01-27T15:31:43Z
draft: true
meta_img: "images/image.png"
tags:
  - "one tag"
  - "another tag"
description: "Description for the page"
---

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

### gg-catalog

Data is collected

#### make minimap index and save to cloud

I put together a script to index the 3 reference genomes, and pushed it to the server 

gg-catalog rev: d2652b15b34949bc5531ffebf0aea8358367c6e3
gg-catalog-nf rev: 32f86f9cf6eb4998eef54f164a581da3e3a28695
slurm sub: 17964829

```bash
INFO:    Using cached SIF image
[M::mm_idx_gen::22.442*1.82] collected minimizers
[M::mm_idx_gen::27.178*2.03] sorted minimizers
[M::main::34.993*1.78] loaded/built the index for 214 target sequence(s)
[M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 214
[M::mm_idx_stat::36.002*1.76] distinct minimizers: 70434703 (49.99% are singletons); average occurrences: 2.795; average spacing: $[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -d galgal.mmi /scratch/bjl34716/gg-catalog/refs/GalGal-reference.fna.gz
[M::main] Real time: 36.094 sec; CPU: 63.405 sec; Peak RSS: 4.697 GB
INFO:    Using cached SIF image
[M::mm_idx_gen::54.369*1.75] collected minimizers
[M::mm_idx_gen::67.709*1.99] sorted minimizers
[M::main::77.321*1.86] loaded/built the index for 687 target sequence(s)
[M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 687
[M::mm_idx_stat::78.275*1.85] distinct minimizers: 60811177 (55.20% are singletons); average occurrences: 6.712; average spacing: $[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -d zeamays.mmi /scratch/bjl34716/gg-catalog/refs/ZeaMays-reference.fna.gz
[M::main] Real time: 78.491 sec; CPU: 144.695 sec; Peak RSS: 9.315 GB
INFO:    Using cached SIF image
[M::mm_idx_gen::25.835*1.78] collected minimizers
[M::mm_idx_gen::30.919*1.98] sorted minimizers
[M::main::36.648*1.82] loaded/built the index for 284 target sequence(s)
[M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 284
[M::mm_idx_stat::37.149*1.81] distinct minimizers: 47120889 (53.64% are singletons); average occurrences: 3.818; average spacing: $[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -d glycinemax.mmi /scratch/bjl34716/gg-catalog/refs/GlycineMax-reference.fna.gz
[M::main] Real time: 37.418 sec; CPU: 67.348 sec; Peak RSS: 5.764 GB
```
Sucess! this was a fast process just memory intensive, good to know!

Next step is since we have all the seqs, is to maybe try to get the process to go through!

#### Nextflow Implement Filtlong

how do you use a process more than once?



---
title: 'Samtools View'
date: 2023-03-08T14:27:59Z
draft: false
meta_img: "images/image.png"
tags:
  - "samtools"
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---


### Todos for Tomorrow


- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
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
  
### gg-catalog-nf

#### Samtools view

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: baa43921ad60d52048fb4842662f28e8668d9b57
slurm sub: 19742122

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [goofy_colden] DSL2 - revision: baa43921ad [main]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /home/bjl34716/my_utils/gg-catalog/code/mapping.tsv
contam    : /home/bjl34716/my_utils/gg-catalog/code/contam.tsv
single_end : false
pacbio : true
iontorrent : false
extension : /*.fastq
metadata: /home/bjl34716/my_utils/gg-catalog/code/metadata.tsv
outdir   : results
profile : slurm,singularity

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/JfZyomcroMRPy
executor >  slurm (43)
[ba/34a78b] process > FILTLONG (SRR19732514)         [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)             [100%] 1 of 1, cached: 1 ✔
[d1/8f1170] process > MINIMAP2_ALIGN (SRR19726169)   [100%] 7 of 7, cached: 7 ✔
[14/767973] process > SAMTOOLS_VIEW (SRR19736685)    [100%] 7 of 7 ✔
[0d/aa9835] process > SAMTOOLS_FASTQ (SRR19683890)   [100%] 7 of 7 ✔
[fe/5fbabf] process > SAMTOOLS_FASTA (SRR19736685)   [100%] 7 of 7 ✔
[20/4394fe] process > SEQKIT_STATS (SRR19726169)     [100%] 7 of 7, cached: 7 ✔
[bd/fde0b4] process > CSVTK_CONCAT (raw)             [100%] 1 of 1, cached: 1 ✔
[75/ead805] process > SEQKIT_STATS_FILT (SRR19732... [100%] 7 of 7, cached: 7 ✔
[f2/ad6f8c] process > CSVTK_CONCAT_FILT (filtlong)   [100%] 1 of 1, cached: 1 ✔
[b7/6f332b] process > SEQKIT_STATS_UNMAP (SRR1968... [100%] 21 of 21 ✔
[e5/9d3dc0] process > CSVTK_CONCAT_UNMAP (minimap)   [100%] 1 of 1 ✔
Completed at: 08-Mar-2023 02:00:33
Duration    : 8h 52m 23s
CPU hours   : 1097.1 (38.4% cached)
Succeeded   : 43
Cached      : 31
```




---
title: 'Remapping Clean to Gene Lib'
date: 2023-03-10T14:20:56Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - yes, but Need to confirm with cat samples
    - try out the indexing and mapping steps with BWA
      - rev c60deddafd6ce2b4d8dcc57e0b9301ef046d2f82
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### gg-catalog

#### Add the task.ext back in 

gg-catalog rev: 2827deb07ef8321df88f81e49e1e560387ffaa70
gg-catalog-nf rev: e0ee8cbf4e6942910734400a17111acd00a20b23
slurm job: 19813455

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [grave_dalembert] DSL2 - revision: e0ee8cbf4e [main]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /home/bjl34716/my_utils/gg-catalog/code/mapping_concat.tsv
contam    : /home/bjl34716/my_utils/gg-catalog/code/contam.tsv
single_end : false
pacbio : true
iontorrent : false
extension : /*.fastq
metadata: /home/bjl34716/my_utils/gg-catalog/code/metadata_concat.tsv
gene_lib : null
outdir   : results
profile : slurm,singularity

Missing `fromPath` parameter

```

gg-catalog rev: 4b058e842764d643035003abb51235ea63527ced
gg-catalog-nf rev: e0ee8cbf4e6942910734400a17111acd00a20b23
slurm job: 19813673

```bash
      \
      Chicken_five_gut_segment.combined.nr.identity95.overlap90.nr.fa.gz -p bwamem2/Chicken_five_gut_segment.combined.nr.identity95.overlap90.nr.fa.gz

  cat <<-END_VERSIONS > versions.yml
  "BWAMEM2_INDEX":
      bwamem2: $(echo $(bwa-mem2 version 2>&1) | sed 's/.* //')
  END_VERSIONS

Command exit status:
  140

Command output:
  (empty)

Command error:
  WARNING: Skipping mount /var/singularity/mnt/session/etc/resolv.conf [files]: /etc/resolv.conf doesn't exist in container
  Looking to launch executable "/usr/local/bin/bwa-mem2.avx512bw", simd = .avx512bw
  Launching executable "/usr/local/bin/bwa-mem2.avx512bw"
  [bwa_index] Pack FASTA... 24.18 sec
  * Entering FMI_search

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/90/fd862f41c74361e1c4d6a22941c519

Tip: view the complete command output by changing to the process work dir and entering the command `cat .command.out`


slurmstepd: error: *** JOB 19813673 ON d2-17 CANCELLED AT 2023-03-10T11:58:50 ***
```
```

gg-catalog rev: 4b058e842764d643035003abb51235ea63527ced
gg-catalog-nf rev: 6e13ede93201191b89fe3b575dc9f4cbc161b92d
slurm job: 19824367

```bash

### Function or example for relative abundance


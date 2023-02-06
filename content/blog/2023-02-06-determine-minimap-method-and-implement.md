---
title: 'Determine Minimap Method and Implement'
date: 2023-02-06T14:12:08Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Next Week

- Jackwood Blast
  - add in the isolate field into parser and output
  - meet with Ben to talk about two points above 2/2/23
- gg-catalog
  - Zhang
    - followup on slurm-18229634
    - try to incorporate the -c flag when samtools merging to see if the filesize is the same as concat
    - create a minimap process (either concat or separate)
      - create a channel/process for each screening reference
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

#### slurm process 18246719

gg-catalog rev: 9151c76456aa96916adcd52d3e4c52ca5a10320a
gg-catalog-nf rev: N/A
slurm sub: 18246719

```bash
it printed the results to the logfile, again...
```

let's save the intermediaries and then delete them at the end if needed.

we need to remove the files: 
  slurm-18229634.out
  slurm-18246719.out
  nearly 200GB
  
gg-catalog rev: d1cb13b370fbbbe293eee6695f8a8aadf1646252
gg-catalog-nf rev: N/A
slurm sub: 18436360

```bash

```

#### Merging sam files with colliding ID flag to see if that produces a smaller filesize

from the forums, cited in 02/03/2023, I found the flag samtools merge -c which will "combine @RG headers with colliding IDs [alter IDs to be distinct] Combine @PG headers with colliding IDs [alter IDs to be distinct]" I added both the c and p flags to see if this filesize will match the combined db size of 126G

gg-catalog rev: c4cff620c145854095baf9e7559fd638d345d842
gg-catalog-nf rev: N/A
slurm sub: 18441011

```bash
bjl34716@ss-sub3 diagnostic$ ls -lah /scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/indv-ref
-rw-r--r--. 1 bjl34716 sealab 189G Feb  2 17:07 merged_reads.sam
-rw-r--r--. 1 bjl34716 sealab 189G Feb  6 11:38 merged_reads_V2.sam
```

These resulted in the same output :/ So we have to work on the merging to see if that gives us better results.


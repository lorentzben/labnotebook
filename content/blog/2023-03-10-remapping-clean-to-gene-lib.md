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
```

### Function or example for relative abundance

I need some example seqs to work with... so I need a practice query which will be some of the first seqs from the clean reads:

/scratch/bjl34716/nf_dev/gg-catalog/work/32/d0957dccda9335bcf3d814a670e5b1/SRR19683891_other.fastq.gz

and then the index is located in: 
/scratch/bjl34716/nf_dev/gg-catalog/work/43/0370b57b959be32c0c311633aa0ff1

so we can open the docker image: 

https://depot.galaxyproject.org/singularity/mulled-v2-e5d375990341c5aef3c9aff74f96f66f65375ef6:2cdf6bf1e92acbeb9b2834b1c58754167173a410-0

I am still waiting on the file to unzip... will write a script in the scratch dir. Nevermind its good to go just need to collect some seqs from it. 


### Todos for Next Week

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

### Git Commits

#### Lab Notebook

```bash
fce6345 - Benjamin Lorentz, Fri Mar 10 12:03:06 2023 -0500 : notes at lunch
02c61ec - Benjamin Lorentz, Fri Mar 10 09:29:01 2023 -0500 : added page for friday
5a4f965 - Benjamin Lorentz, Thu Mar 9 16:57:59 2023 -0500 : added final notes for thursday
```

#### gg-catalog-nf

```bash
6e13ede - Benjamin Lorentz, Fri Mar 10 09:52:19 2023 -0500 : update conf/modules.config
6795ebc - Benjamin Lorentz, Fri Mar 10 09:32:40 2023 -0500 : update main.nf
e0ee8cb - Benjamin Lorentz, Fri Mar 10 09:19:37 2023 -0500 : update conf/modules.config
c60dedd - Benjamin Lorentz, Thu Mar 9 16:49:48 2023 -0500 : update main.nf
```

#### gg-catalog

```bash
4b058e8 - Benjamin Lorentz, Fri Mar 10 09:34:53 2023 -0500 : update params/concat_params.yaml
```
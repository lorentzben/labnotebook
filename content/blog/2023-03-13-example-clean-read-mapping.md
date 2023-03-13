---
title: 'Example Clean Read Mapping'
date: 2023-03-13T14:23:38Z
draft: false
meta_img: "images/image.png"
tags:
  - "BWA2"
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
  
### gg-catalog-nf 

#### Slurm Job 19824367

```bash
Name

MINIMAP2_ALIGN (cecum)

Command


minimap2 \
    -ax map-hifi --split-prefix temp_sam_ \
    -t 6 \
    "concat-gal-zea-glycine.fna.gz" \
    "cecum.fastq.gz" \
     \
    -L \
    -a | samtools sort | samtools view -@ 6 -b -h -o cecum.bam


cat <<-END_VERSIONS > versions.yml
"MINIMAP2_ALIGN":
    minimap2: $(minimap2 --version 2>&1)
END_VERSIONS

Status

Exit: 140 (FAILED) Attempts: 1 (action: FINISH)

Work directory

/scratch/bjl34716/nf_dev/gg-catalog/work/9e/e1bc1fc4fdce6ce2af967eb3a23044

MINIMAP2_ALIGN (colorectum)

Command


minimap2 \
    -ax map-hifi --split-prefix temp_sam_ \
    -t 6 \
    "concat-gal-zea-glycine.fna.gz" \
    "colorectum.fastq.gz" \
     \
    -L \
    -a | samtools sort | samtools view -@ 6 -b -h -o colorectum.bam


cat <<-END_VERSIONS > versions.yml
"MINIMAP2_ALIGN":
    minimap2: $(minimap2 --version 2>&1)
END_VERSIONS

Status

Exit: 140 (FAILED) Attempts: 1 (action: FINISH)

Work directory

/scratch/bjl34716/nf_dev/gg-catalog/work/de/4d7df060df8239747e53f8e76161e7
Error executing process > 'SAMTOOLS_FASTA (duodenum)'

Caused by:
  Process `SAMTOOLS_FASTA (duodenum)` terminated with an error exit status (1)

Command executed:

  samtools \
      fasta \
       \
      --threads 19 \
      -0 duodenum_other.fasta.gz \
      unmapped.bam \
      -1 duodenum_1.fasta.gz -s duodenum_singleton.fasta.gz

  cat <<-END_VERSIONS > versions.yml
  "SAMTOOLS_FASTA":
      samtools: $(echo $(samtools --version 2>&1) | sed 's/^.*samtools //; s/Using.*$//' ))
  END_VERSIONS

Command exit status:
  1
Command output:
  (empty)

Command error:
  [E::bgzf_read_block] Invalid BGZF header at offset 6040418483
  [E::bgzf_read] Read block operation failed with error 6 after 0 of 4 bytes
  samtools bam2fq: Failed to read bam record
  samtools bam2fq: Error writing to FASTx files.: Invalid argument
  [M::bam2fq_mainloop] discarded 0 singletons
  [M::bam2fq_mainloop] processed 1159732 reads

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/ba/c020b29ab268a20d50e506bfa9e8bd

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`


slurmstepd: error: *** JOB 19824367 ON c5-3 CANCELLED AT 2023-03-13T10:23:40 ***
```
```

So we have an error with the mapping and an error with the samtools...

Lets try to re-submit with the resume if this also fails out then we can run without the resume and see if it has the same error.

gg-catalog rev: 4b058e842764d643035003abb51235ea63527ced
gg-catalog-nf rev: 6e13ede93201191b89fe3b575dc9f4cbc161b92d
slurm sub: 19868408

```bash
```

#### BWA example so I can calculate relative abundnance

Working directory: /scratch/bjl34716/nf_dev/gg-catalog/work/32/d0957dccda9335bcf3d814a670e5b1/


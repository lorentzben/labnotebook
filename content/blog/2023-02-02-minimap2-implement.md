---
title: 'Minimap2 Implement'
date: 2023-02-02T14:21:21Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Finalize Homework 1 Stat 6220
  - include notes from Dr. Chohurdy
- Jackwood Blast
  - add in the isolate field into parser and output
- gg-catalog
  - Zhang
    - create a minimap process
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
  
### Stat 6220 

#### Finalize homeowork 1

### gg-catalog-nf

#### minimap2 for loop 

We can either try the [input each](https://www.nextflow.io/docs/latest/process.html#input-repeaters-each) but more likely, I'm thinking if we can subset the ch_contam_reads, then we just make a process call for each one with each read, 

we can get the cleaned read by: 

```bash

minimap2 -a REF R1 R2 | samtools sort | samtools view -f 4 | samtools fastq -s R0 -1 R1 -2 R2

```

I have tried to setup a minimap run for the first reference

gg-catalog rev: a9cec6072cfbe08b36108527501d5cd4b96b31ae
gg-catalog-nf rev: e7eb1cc7ac25240dd518747d7132e2ee2e2275b0
slurm sub: 18155358

```bash

N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Unknown config attribute params.publish_dir_mode -- check config file: /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/nextflow.config

```

I removed the params.publish_dir_mode

gg-catalog rev: a9cec6072cfbe08b36108527501d5cd4b96b31ae
gg-catalog-nf rev: acf1675f50b7ef09b1b1b40ed18fc8b8bc9f7614
slurm sub: 18155771

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'getAt'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 90 or see '.nextflow.log' file for more details
[-        ] process > FILTLONG       -
```


#### Can we combine all 3 references into one index or do they have to be one-by-one

Dir structure:

```bash
/scratch/bjl34716/gg-catalog/refs/
  GalGal-reference.fna.gz  
  GlycineMax-reference.fna.gz  
  ZeaMays-reference.fna.gz
  
/scratch/bjl34716/gg-catalog/zhang/reads
├── cecum
│   ├── SRR15214153
│   │   └── SRR15214153.sra
│   ├── SRR15214153.fastq
│   └── SRR19732730.fastq
├── colorectum
│   ├── SRR19683890
│   │   └── SRR19683890.sra
│   ├── SRR19683890.fastq
│   ├── SRR19732729
│   │   └── SRR19732729.sra
│   └── SRR19732729.fastq
├── duodenum
│   ├── SRR19683891
│   │   └── SRR19683891.sra
│   └── SRR19683891.fastq
├── ileum
│   ├── SRR19736685
│   │   └── SRR19736685.sra
│   └── SRR19736685.fastq
└── jejunum
    ├── SRR19726169
    │   └── SRR19726169.sra
    ├── SRR19726169.fastq
    ├── SRR19732514
    │   └── SRR19732514.sra
    └── SRR19732514.fastq
    
/scratch/bjl34716/nf_dev/gg-catalog
  ├── compare-minimap
  │   ├── concat-ref
  │   └── indv-ref
  │       ├── gal-gal
  │       ├── glycine-max
  │       └── zea-mays
```

#### concat reference

```bash

cd /scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/concat-ref

cat /scratch/bjl34716/gg-catalog/refs/*.fna.gz > contam-refs.fna.gz

singularity run docker://lorentzb/minimap2:1.0 minimap2 -ax map-hifi contam-refs.fna.gz /scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq > SRR15214153.sam
```

This kept getting killed from memory:

gg-catalog rev: 9fb9a19fc16f8e41705713ff25d474bb7a738ad1
gg-catalog-nf rev: N/A
slurm sub: 18157122

```bash
```
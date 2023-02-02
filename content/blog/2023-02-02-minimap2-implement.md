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
[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -ax map-hifi contam-refs.fna.gz /scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq
[M::main] Real time: 1903.941 sec; CPU: 5089.747 sec; Peak RSS: 13.910 GB
```

success

gg-ref

gg-catalog rev: 72c5b4e98c0d873326926839cfaa53ba862c413b 
gg-catalog-nf rev: N/A
slurm sub: 18159019

```bash
[M::worker_pipeline::1220.806*1.42] mapped 8961 sequences
[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -ax map-hifi /scratch/bjl34716/gg-catalog/refs/GalGal-reference.fna.gz /scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq
[M::main] Real time: 1221.027 sec; CPU: 1730.478 sec; Peak RSS: 5.871 GB
```

glycine-max ref

gg-catalog rev: 72c5b4e98c0d873326926839cfaa53ba862c413b 
gg-catalog-nf rev: N/A
slurm sub: 18160527

```bash
[M::worker_pipeline::1038.678*1.83] mapped 8961 sequences
[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -ax map-hifi /scratch/bjl34716/gg-catalog/refs/GlycineMax-reference.fna.gz /scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq
[M::main] Real time: 1038.798 sec; CPU: 1903.994 sec; Peak RSS: 5.450 GB
```

zea-mays ref

gg-catalog rev: 72c5b4e98c0d873326926839cfaa53ba862c413b 
gg-catalog-nf rev: N/A
slurm sub: 18160575

```bash
[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -ax map-hifi /scratch/bjl34716/gg-catalog/refs/ZeaMays-reference.fna.gz /scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq
[M::main] Real time: 1743.096 sec; CPU: 2265.874 sec; Peak RSS: 7.765 GB
```

We need to count the number of records in a samfile

dir structure right now

```bash
/scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/indv-ref/
├── gal-gal
│   └── SRR15214153_gal_gal.sam
├── glycine-max
│   └── SRR15214153_glycine_max.sam
└── zea-mays
    └── SRR15214153_zea_mays.sam
```

I updated the script to sort and then merge the samfiles into one file.

things to check:

  - the sorted files out are still sam (human readable)
  - the merged file is still sam (human readble)
  - the number of records is the same as the concat DB
  - the number of records is the same as the fastx concat DB version
  

gg-catalog rev: 45f18c0697b5f0ae4d5d7ec97625b7b8765da9c4
gg-catalog-nf rev: N/A
slurm sub: 18160757

```bash

```

### Ben Jackwood

Ben sent me this email:

"Ben, 
Please see the attached output for when I attempt to run the script with the impromptu database. I do not think it generated a slurm output to view. Maybe we can sit down next week and figure out how to put the custom database into a format it will use. I have also attached the database. Thanks."

I'm not certain what his is exact issue is, but in order:

1. He needs to pull down the new version from github
2. He had the header on the database which needs to be removed so that there isn't database_out.

We will edit these two changes and see what else is left.

### Todos for Tomorrow

- Jackwood Blast
  - add in the isolate field into parser and output
  - meet with Ben to talk about two points above 2/2/23
- gg-catalog
  - Zhang
    - followup on slurm-18160757
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

### Git Commits

#### Lab Notebook 

```bash
a179a6f - Benjamin Lorentz, Thu Feb 2 11:58:26 2023 -0500 : notes before lunch
4e00890 - Benjamin Lorentz, Thu Feb 2 09:24:27 2023 -0500 : page for thursday
623fc91 - Benjamin Lorentz, Wed Feb 1 16:56:18 2023 -0500 : end of notes for wednesday
```

#### gg-catalog-nf

```bash
acf1675 - Benjamin Lorentz, Thu Feb 2 10:53:43 2023 -0500 : update modules.config and main.nf
e7eb1cc - Benjamin Lorentz, Thu Feb 2 10:33:52 2023 -0500 : update main.nf
79914ef - Benjamin Lorentz, Wed Feb 1 16:48:09 2023 -0500 : update main.nf
13c5a64 - Benjamin Lorentz, Wed Feb 1 16:45:56 2023 -0500 : update main.nf
7a5622f - Benjamin Lorentz, Wed Feb 1 16:32:24 2023 -0500 : update main.nf
e9c1643 - Benjamin Lorentz, Wed Feb 1 16:28:43 2023 -0500 : update main.nf
c163ac9 - Benjamin Lorentz, Wed Feb 1 16:23:34 2023 -0500 : update main.nf
```

### gg-catalog

```bash
45f18c0 - Benjamin Lorentz, Thu Feb 2 14:24:28 2023 -0500 : updated 05_sam_merge.sh
72c5b4e - Benjamin Lorentz, Thu Feb 2 12:44:32 2023 -0500 : added 02-05
9fb9a19 - Benjamin Lorentz, Thu Feb 2 11:35:15 2023 -0500 : add 01_concat_contam_refs.sh
a9cec60 - Benjamin Lorentz, Wed Feb 1 16:19:05 2023 -0500 : add contam.tsv and update test_params.yaml
```
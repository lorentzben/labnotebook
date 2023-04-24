---
title: 'Finish Out Class and Local'
date: 2023-04-24T12:53:43Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
  - "STAT 6220"
description: "Description for the page"
---

### Todos for Today

- Class
  - Cheetsheet for Midterm
  - Paper?
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Ade

#### Local Analysis

cycle 4 rev: 5697893f091bc79120302f682065f8b382801325

```bash
Couldnt open params
```

cycle 4 rev:

```bash
/usr/local/bin/python3: /usr/local/bin/python3: cannot execute binary file
ade-cycle-4-nextflow_litter_srs_local.sh: line 25: module: command not found
```

cycle 4 rev: 89c2751a6c2f92e1d65e42119f3b16241cc34654

```bash
N E X T F L O W  ~  version 22.10.4
Unknown configuration profile: 'local'
```

cycle 4 rev: 8287f21acac7bac4ba5263fbb3d2e9137a42a82e

```bash
N E X T F L O W  ~  version 22.10.4
Launching `https://github.com/nf-core/ampliseq` [spontaneous_mahavira] DSL2 - revision: 708b8398d0 [2.4.0]
Cannot enable more than one container engine -- Choose either one of: docker, singularity
```

enabled a docker in gacrc config file

cycle 4 rev: 0e80ff3bfaca40cb6190d77f862046b89b5baa00

```bash
Unable to read script: '/home/bjl34716/.nextflow/assets/nf-core/ampliseq/./workflows/ampliseq.nf' -- cause: /mnt/c/Users/bjl34716/Documents/Aggrey/ade/cycle-4/cycle_4_litter_metadata_local.tsv
```

cycle 4 rev:

```bash
Use DADA2 taxonomy classification
ERROR: Please check input samplesheet -> Forward read FastQ file does not exist!
/mnt/c/Users/bjl34716/Documents/Aggrey/ade/1-21_S265_L001_R1_001.fastq.gz
```

### Class

#### Cheetsheet/Exam Prep

Done!

### Todos for Tomorrow

- Class
  - Cheetsheet for Midterm
  - Paper?
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community


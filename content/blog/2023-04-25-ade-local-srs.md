---
title: 'Ade Local SRS'
date: 2023-04-25T13:42:54Z
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
  - Paper?
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Set up a local analysis on small data while Sapelo2 is under maintenece
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

cycle 4 rev:

```bash
Use DADA2 taxonomy classification
ERROR: Please check input samplesheet -> Forward read FastQ file does not exist!
/mnt/c/Users/bjl34716/Documents/Aggrey/ade/1-21_S265_L001_R1_001.fastq.gz
```

cycle 4 rev: 647c2761d616afeae46b23ca21e49ec816c337ae

```bash
Path string cannot start with a blank or special characters -- Offending path: ' /mnt/c/Users/bjl34716/Documents/Aggrey/ade/data/1-21_S265_L001_R1_001.fastq.gz'

 -- Check script '/home/bjl34716/.nextflow/assets/nf-core/ampliseq/./workflows/../subworkflows/local/parse_input.nf' at line: 22 or see '.nextflow.log' file for more details
```

cycle 4 rev: 64e06baa5b75f8289dbcefd90e0439deca40bd8b

```bash
ERROR: Please check input samplesheet -> Forward read FastQ file does not exist!
~/ade/data/1-21_S265_L001_R1_001.fastq.gz
```

It's still not reading the files

cycle 4 rev: 1a0a9c839b958f0c561744f4796dec5dd17c16a9

```bash 
Execution cancelled -- Finishing pending tasks before exit
-[nf-core/ampliseq] Pipeline completed with errors-
Error executing process > 'NFCORE_AMPLISEQ:AMPLISEQ:RENAME_RAW_DATA_FILES (LT81)'

Caused by:
  Process requirement exceeds available memory -- req: 12 GB; avail: 7.8 GB

Command executed:

  [ -f "LT81_1.fastq.gz" ] || cp "9-21_S273_L001_R1_001.fastq.gz" "LT81_1.fastq.gz"
  [ -f "LT81_2.fastq.gz" ] || cp "9-21_S273_L001_R2_001.fastq.gz" "LT81_2.fastq.gz"

  cat <<-END_VERSIONS > versions.yml
  "NFCORE_AMPLISEQ:AMPLISEQ:RENAME_RAW_DATA_FILES":
      sed: $(sed --version 2>&1 | sed -n 1p | sed 's/sed (GNU sed) //')
  END_VERSIONS

Command exit status:
  -
```
```


I reduced memory

cycle 4 rev:

```bash 
```

If this still gives issues then we can pivot to collecting the data for the positive controls. 

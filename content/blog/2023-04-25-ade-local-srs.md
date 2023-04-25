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

cycle 4 rev: fa04d2f19325c78d789accb5da9bdca89cae6e01

```bash 
-[nf-core/ampliseq] Pipeline completed successfully-
Completed at: 25-Apr-2023 11:24:34
Duration    : 56m 52s
CPU hours   : 1.8
Succeeded   : 69

Error occurred during initialization of VM
java.lang.Error: Properties init: Could not determine current working directory.
        at jdk.internal.util.SystemProps$Raw.platformProperties(java.base@17.0.3-internal/Native Method)
        at jdk.internal.util.SystemProps$Raw.<init>(java.base@17.0.3-internal/SystemProps.java:234)
        at jdk.internal.util.SystemProps.initProperties(java.base@17.0.3-internal/SystemProps.java:54)
        at java.lang.System.initPhase1(java.base@17.0.3-internal/System.java:2089)
NOTE: Nextflow is trying to use the Java VM defined by the following environment variables:
 JAVA_CMD: /home/bjl34716/miniconda3/envs/nf-core/lib/jvm/bin/java
 NXF_OPTS:

cp: cannot stat '/mnt/c/Users/bjl34716/Documents/Aggrey/ade/cycle-4/litter/local/figaro_result': No such file or directory
```

If this still gives issues then we can pivot to collecting the data for the positive controls. 


cycle 4 rev: 22b28c61982dc6f152726b044618d9e8c86a887a

```bash 
[-        ] process > ORDERIOI              -
[-        ] process > FILTERNEGATIVECONTROL -
[-        ] process > TSVTOQZA              -
Unknown process directive: `_out_file`

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 1167 or see '.nextflow.log' file for more details
```

cycle 4 rev:  e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: f9176d678bb080d575b5014b58298d850766ef03


```bash 
Unknown process directive: `_out_file`

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 1167 or see '.nextflow.log' file for more details
```

cycle 4 rev:  e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 1067e0daba99d0322140a8928445ca08c0b7d7d9

```bash
[-        ] process > ORDERIOI -
Unknown process directive: `_out_file`

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 423 or see '.nextflow.log' file for more details
```

cycle 4 rev:  e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 029c8072b45cbfa72d0155687163c36aaa9bbe65

```bash
No such variable: Exception evaluating property 'biom' for nextflow.script.ChannelOut, Reason: groovy.lang.MissingPropertyException: No such property: biom for class: groovyx.gpars.dataflow.DataflowBroadcast

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 82 or see '.nextflow.log' file for more details
```

cycle 4 rev:  e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 70f7a905cb7f2ed145dd6b3bf167793180b7d30f

```bash
Process 'TSVTOQZA' has been already used -- If you need to reuse the same component, include it with a different name or include it in a different workflow context

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 82 or see '.nextflow.log' file for more details
```

Since we want to reuse the process of TSVtoQZA we need to make this a module, import it
and call it twice using this:
[https://www.nextflow.io/docs/latest/dsl2.html#multiple-inclusions](https://www.nextflow.io/docs/latest/dsl2.html#multiple-inclusions)

### Todos for Tomorrow

- Class
  - Paper?
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Set up a local analysis on small data while Sapelo2 is under maintenece
  - Make TSVTOQZA a module, and use multiple import
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
  
### Git Commits

#### Labnotebook

```bash
3ca54d1 - Benjamin Lorentz, Tue Apr 25 10:33:33 2023 -0400 : notes from getting local setup
cbe7249 - Benjamin Lorentz, Tue Apr 25 09:44:49 2023 -0400 : added page for tuesday
57cb1e0 - Benjamin Lorentz, Mon Apr 24 17:03:19 2023 -0400 : final notes for monday
```

#### cycle 4

```bash
e2f5c2d - Benjamin Lorentz, Tue Apr 25 15:47:21 2023 -0400 : update the viz params
6720c6b - Benjamin Lorentz, Tue Apr 25 11:35:57 2023 -0400 : update viz params
22b28c6 - Benjamin Lorentz, Tue Apr 25 11:29:46 2023 -0400 : update params bash
fa04d2f - Benjamin Lorentz, Tue Apr 25 10:25:36 2023 -0400 : add config file and reduce memory for local analysis
1a0a9c8 - Benjamin Lorentz, Tue Apr 25 10:20:29 2023 -0400 : update litter/local/mapping
64e06ba - Benjamin Lorentz, Tue Apr 25 10:04:27 2023 -0400 : move data and mappingfile to ~/ade/data
647c276 - Benjamin Lorentz, Tue Apr 25 09:51:28 2023 -0400 : fixed the filepath for the mapping file
```

#### visualize-ampliseq

```bash
70f7a90 - Benjamin Lorentz, Tue Apr 25 16:43:27 2023 -0400 : update main.nf
029c807 - Benjamin Lorentz, Tue Apr 25 16:38:33 2023 -0400 : update main.nf
1067e0d - Benjamin Lorentz, Tue Apr 25 16:32:44 2023 -0400 : update main.nf
f9176d6 - Benjamin Lorentz, Tue Apr 25 16:02:30 2023 -0400 : update main.nf
```

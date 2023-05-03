---
title: 'Filter Samples'
date: 2023-05-03T13:04:08Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
description: "Description for the page"
---

### Todos for Today

- Class
  - if there are any paper edits
  - Email Summer Prof about iceland
  - Find out what fall class
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - Filter NC and Mock Samples
  - Taguchi optmization for richness?
  - Make these subworkflows as opposed to one long workflow?
  - Unit tests based on the example data
  - Positive Control Analysis
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Class

Email summer prof (check)
Fall class (check)

### Ade

Filter Mock/Control Process

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: e6e0ad0dd54c440d0b1cf915c67b0073f4edbd49
slurm sub: 21929436

```bash
Process `QIIME2_FILTERMOCK` declares 3 input channels but 1 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 94 or see '.nextflow.log' file for more details
[ERROR] Terminal initialization failed; falling back to unsupported
java.lang.IllegalStateException: Shutdown in progress
```

We might want to use [this process](https://github.com/nf-core/ampliseq/blob/master/modules/local/qiime2_export_absolute.nf) after the filtering? or what I've set up before

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: e53f25d4a710cd988844606295a1d35ca9f3e8e5
slurm sub: 21947317

```bash
[34/603eb3] process > REPORT14CITATIONS (1)          [100%] 1 of 1, cached: 1 ✔
Execution cancelled -- Finishing pending tasks before exit
Error executing process > 'QIIME2_FILTERNC (NC)'

Caused by:
  Process `QIIME2_FILTERNC (NC)` terminated with an error exit status (1)

Command executed:

  export XDG_CONFIG_HOME="${PWD}/HOME"

  qiime feature-table filter-samples \
      --i-table feature-table.qza \
      --m-metadata-file metadata.tsv \
      --p-where 'NC<>""' \
      --o-filtered-table NC.qza

  cat <<-END_VERSIONS > versions.yml
  "QIIME2_FILTERNC":
      qiime2: $( qiime --version | sed '1!d;s/.* //' )
  END_VERSIONS

Command exit status:
  1

Command output:
  (empty)
```
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: ea51aac1724951278133ea5c7c590e05afc68c34
slurm sub: 21947546

```bash
Error executing process > 'QIIME2_FILTERNC (NC)'

Caused by:
  Process `QIIME2_FILTERNC (NC)` terminated with an error exit status (1)

Command executed:

  export XDG_CONFIG_HOME="${PWD}/HOME"

  qiime feature-table filter-samples \
      --i-table feature-table.qza \
      --m-metadata-file metadata.tsv \
      --p-where [Treatment]='NC' \
      --o-filtered-table NC.qza

  cat <<-END_VERSIONS > versions.yml
  
```
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: e0fae1be957e749e1a5aa3fc0e8657c68d5dd9c2
slurm sub: 21950346

```bash
wrong docker img error
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 9a5a3af7b4402b5823fc171d6199f65539989b4e
slurm sub: 21951237

```bash
Completed at: 03-May-2023 14:20:12
Duration    : 17m 9s
CPU hours   : 0.9 (32.7% cached)
Succeeded   : 22
Cached      : 10
```

Downstream processes:

SRS Normalize:

Yes SRS Yes NC Mock:
  - MOCK.tsv

Yes SRS Yes NC: 
  - NC.tsv

Yes SRS:
  - SRSNORMALIZE.out.biom_normalized
  
Yes NC: 
  - NC.tsv

Yes Mock:
  - Mock.tsv

No SRS No Mock No NC:
 - results/qiime2/abundance_tables/feature-table.biom

GENERATEBIOMFORGRAPHLAN

Report 01


### Unit testing:

Here is the nf-core test data location

https://github.com/nf-core/test-datasets/tree/ampliseq


### Todos for Tomorrow

- Class
  - if there are any paper edits
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - Filter NC and Mock Samples
     - Update downstream processes for SRS NC MOCK
     - Implement the other ones
  - Taguchi optmization for richness?
  - Make these subworkflows as opposed to one long workflow?
  - Unit tests based on the example data
  - Positive Control Analysis
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
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
9a5f64a - Benjamin Lorentz, Wed May 3 09:07:02 2023 -0400 : page for Thursday
f6ec5fb - Benjamin Lorentz, Tue May 2 16:59:56 2023 -0400 : final notes for tuesday
```

#### Visualize Ampliseq

```bash
9a5a3af - Benjamin Lorentz, Wed May 3 13:47:02 2023 -0400 : update export absolute
e0fae1b - Benjamin Lorentz, Wed May 3 13:45:04 2023 -0400 : update qiime2filtersamples
ea51aac - Benjamin Lorentz, Wed May 3 10:59:39 2023 -0400 : update main.nf
e53f25d - Benjamin Lorentz, Wed May 3 10:36:02 2023 -0400 : update main.nf
```
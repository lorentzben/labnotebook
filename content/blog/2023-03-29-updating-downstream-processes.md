---
title: 'Updating Downstream Processes'
date: 2023-03-29T14:29:19Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Today

- Class
  - read over Ellie's sections
  - what can I write? 
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
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

#### Update downstream table qzas

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: f9bbdb7e376aeb21aaf4b4f22eeeb8485a6004e1
slurm job: 20372443

```bash
WARN: Failed to publish file: /scratch/bjl34716/ade/cycle-4/work/92/ce1a11981556e5d4260bee05f6ef7f/13_report_28-03-2023_17.45.58.html; to: /work/sealab/bjl34716/ade/cycle-4/litter/html/13_report_28-03-2023_17.45.58.html [copy] -- See log file for details
Completed at: 28-Mar-2023 17:46:35
Duration    : 51m 5s
CPU hours   : 1.6 (7.4% cached)
Succeeded   : 21
Cached      : 7
```

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: f9bbdb7e376aeb21aaf4b4f22eeeb8485a6004e1
slurm job: 20430469

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
lorentzben/visualize-ampliseq contains uncommitted changes -- cannot pull from repository
```

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: c878e8fc0d7d8e3f88aa8355d884f9aa961ca99d
slurm job: 20431775

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [zen_sanger] DSL2 - revision: c878e8fc0d [control]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /scratch/bjl34716/ade/cycle-4/litter
metadata : /scratch/bjl34716/ade/cycle-4/litter/metadata.tsv
item of interest : Treatment
ordered item of interest : ordered_item_of_interest.csv
outdir   : /work/sealab/bjl34716/ade/cycle-4/litter
rarefaction depth : 0
controls: /home/bjl34716/ade/cycle-4/litter/controls.tsv
profile : slurm,singularity

No such variable: filtered_table_biom

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 68 or see '.nextflow.log' file for more details
[-        ] process > ORDERIOI -
```

cycle_4 rev:  b9b22ea2b6ab083301a11551069c3ab4d0a6650d
visualize ampliseq rev: ae9d5e80cb4dbb7357b36bb04f96f012999008d8
slurm job: 20431974

```bash
WARN: Failed to publish file: /scratch/bjl34716/ade/cycle-4/work/d8/8d4042066cf3888b87dd163006e9d5/13_report_29-03-2023_15.49.21.html; to: /work/sealab/bjl34716/ade/cycle-4/litter/html/13_report_29-03-2023_15.49.21.html [copy] -- See log file for details
Completed at: 29-Mar-2023 16:01:05
Duration    : 1h 34m 56s
CPU hours   : 2.6 (0.3% cached)
Succeeded   : 27
Cached      : 1
```

Mar-29 16:01:05.269 [FileTransfer-1] WARN  nextflow.processor.PublishDir - Failed to publish file: /scratch/bjl34716/ade/cycle-4/work/d8/8d4042066cf3888b87dd163006e9d5/13_report_29-03-2023_15.49.21.html; to: /work/sealab/bjl34716/ade/cycle-4/litter/html/13_report_29-03-2023_15.49.21.html [copy] -- See log file for details
java.nio.file.FileSystemException: /work/sealab/bjl34716/ade/cycle-4/litter/html/13_report_29-03-2023_15.49.21.html: Disk quota exceeded

We have to clean up the work dir and update the rarefaction script.

### Update The rarefaction report Rmd file to use the QIIME Tables

### Todos for Tomorrow

- Class
  - read over Ellie's sections
  - what can I write? 
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
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

#### Lab Notebook

```bash
1b93d81 - Benjamin Lorentz, Wed Mar 29 11:55:03 2023 -0400 : added updates before lunch
e483eb9 - Benjamin Lorentz, Wed Mar 29 10:31:18 2023 -0400 : added page for wednesday
```

#### Visualize Ampliseq

```bash
ae9d5e8 - Benjamin Lorentz, Wed Mar 29 14:19:15 2023 -0400 : update main.nf
c878e8f - Benjamin Lorentz, Wed Mar 29 14:07:05 2023 -0400 : update main.nf
243ea4d - Benjamin Lorentz, Wed Mar 29 14:04:41 2023 -0400 : Revert "update main.nf"
7e7fe74 - Benjamin Lorentz, Wed Mar 29 14:03:27 2023 -0400 : update main.nf
```
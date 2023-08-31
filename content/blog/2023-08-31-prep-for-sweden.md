---
title: 'Prep for Sweden'
date: 2023-08-31T13:44:22Z
draft: false
meta_img: "images/image.png"
tags:
   - "stat 8200"
   - "bird-stress-analysis"
description: "Description for the page"
---

### Todos for today

- Storage Device for Aggrey

- class
  - Complete homework 1 problems
    - re-run early analysis with t-test/aov
  
- other sweden tasks
  - finish github etc
  - find a copy of Regmi Data to be able to show them 
  
- Regmi
  - Microbiome Work
    - Make script to get from raw data to QZAs
    - Compile all params I'm gonna need
    - Make a doc to import data into:
      - QIIME2
      - Phyloseq
      -biopython
- gg-catalog
  - better formatted table so that the clarity is better.
  - what ammino acids are being processed in each segment
    - valine is processed in the duodenum but not the jejunum
  - gene network of all keggs in one network for each tissue
  - go into the literature; gene catalogs for a biological process in an organism.
      - Need to compare/remove the common genes/processes 

 
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
  
### Sweden

- Email Anna !
- Make sure Space on Macbook
- Make Sure space on essd
- Finish first lecture exercise !

### Aggrey 

- Option for storage device !

### Regmi

- Upload raw seqs to server !
- Script up analysis

First intial attempt

bird_stress_rev: 2d7dcd6d3750e43761a82e5b8abe73e5634c7214
slurm job: 24485039

```bash
cp: omitting directory ‘/home/bjl34716/regmi/2021_regmi_bird_stress/data’
FATAL:   Unable to handle docker://quay.io/qiime2/core:2019.1.0 uri: failed to get checksum for docker://quay.io/qiime2/core:2019.1.0: reading manifest 2019.1.0 in quay.io/qiime2/core: manifest unknown: manifest unknown
```

bird_stress_rev: f23c805d476c769befdc02c8fc0c1efb56c084aa
slurm job: 24485053

```bash
```

### Project Managment

Going forward a [structure like this](https://bioinformaticsworkbook.org/projectManagement/Intro_projectManagement.html#gsc.tab=0) could be really useful to keep track of what is going on.

Like keep this notebook as a high level view of my projects but then have notes inside each repo in order to keep it better organized.

I still want to examine a database or some kind of structure to better track raw data/intermediates and projects in the long term;

This may include making a project metadata sheet, having a raw sample specific MIMS sheet and then the files generated. 

I spent a not insignificant amount of time trying to install schemasheets to turn the MIxS markdown files into spreadsheets so that they can be edited and then turned back? I'm still not certain of the goal here, but I want to see if that works before developing my own. But I will also have a meta-metadata file to track all my projects. Turns out the issue was that it needed python 3.9 

I made the file meta-metadata.md which I will use to track projects going forward and I need to do some retrospective: 
  - Ellestad shailes picrust
  - Ellestad Rothrock analysis
  - Kim JC analysis
  - Jordan Jackwood parser
  - Regmi microbiome analysis
  - Regmi RIFD analysis
  - Applegate villegas analysis
  
### Todos for Tomorrow

- class
  - Complete homework 1 problems
    - re-run early analysis with t-test/aov
  
- other sweden tasks
  - find a copy of Regmi Data to be able to show them
  - Make sure Space on Macbook
  - Make Sure space on essd
  
- Regmi
  - Microbiome Work
    - Make script to get from raw data to QZAs
    - Compile all params I'm gonna need
    - Make a doc to import data into:
      - QIIME2
      - Phyloseq
      -biopython
      
- gg-catalog
  - better formatted table so that the clarity is better.
  - what ammino acids are being processed in each segment
    - valine is processed in the duodenum but not the jejunum
  - gene network of all keggs in one network for each tissue
  - go into the literature; gene catalogs for a biological process in an organism.
      - Need to compare/remove the common genes/processes 

 
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation

### Git Commits

#### Lab notebook

```bash
8c197c1 - Benjamin Lorentz, Thu Aug 31 09:48:32 2023 -0400 : add page for Thursday
```

#### bird-anxiety

```bash
f23c805 - Benjamin Lorentz, Thu Aug 31 16:48:24 2023 -0400 : update slurm driver to recusively copy
2d7dcd6 - Benjamin Lorentz, Thu Aug 31 16:23:20 2023 -0400 : update slurm driver script
6c4100d - Benjamin Lorentz, Thu Aug 31 16:21:12 2023 -0400 : add 01_import_seqs_to_qza, slurm driver
830ae2e - Benjamin Lorentz, Thu Aug 31 15:57:08 2023 -0400 : Add data/README.md and move mappingfiles
```
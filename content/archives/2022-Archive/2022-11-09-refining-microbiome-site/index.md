---
title: Refining Microbiome Site
author: Ben Lorentz
date: '2022-11-09'
slug: refining-microbiome-site
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segement
    - they may have done some of this heavy lifting for us.
- site for microbiome
  - fix paragraph links
  - add doi links to citation pages
- continue reading jones
- Visualize Ampliseq
  - add example params and slurm for ampliseq into ampliseq-vis repos
- Run Visualize Ampliseq
  - on low med high richness samples
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Try to run DESeq2’s GLM/LRT on shaile’s design

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca


I want to refine the citation files to use the obsidian linking format and that there is a DOI for each citation. Following that we have to digest the Tillocca data, then either 1) dig into their supplementals, 2) look at each richness for visualize ampliseq and make some observations, 3) Implemenet DESeq2 on Shailes' data.

### Notes from Citation Cleanup 

I was able to fix all existing links and have plan to import the 4ish papers that do not have cross references yet, these papers are:

- fronk (imported)
- hooper (imported)
- oakley (imported)
- qin (read but not much to be used for chicken)
- tilocca (imported)
- zou

I've imported the first three papers, Oakley talks about the specific taxa Megamonas, Helicobacter, and Campylobacter who produce SCFAs and how they might act as hydrogen sinks. This lead me down a littel bit of a rabbit hole finding Sergant, it seems like in 2014 there was a couple papers looking at the chicken ceca and how SCFA is present and utilized. I think this will be a small cove to look into over the course of this study. 

I feel like I need to spend some time summarizing the quotes I've collected into my own words, but also the first real step is just figuring out who is present, we must stay focused on that. **Right now the focus is importing the papers.**

We also need to remove the paper notes section...

### Term Paper 

Kallisto results 

```bash

../data/kallisto/
├── ceca
│   ├── SRR8265548
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265549
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265550
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265591
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265621
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265622
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265623
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265624
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265625
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265626
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265627
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265628
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265629
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   └── SRR8265630
│       ├── abundance.h5
│       ├── abundance.tsv
│       └── run_info.json
├── duodenum
│   ├── SRR8265557
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265558
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265559
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265560
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265561
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265562
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265633
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265634
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265635
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265636
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265637
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265638
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265639
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   └── SRR8265640
│       ├── abundance.h5
│       ├── abundance.tsv
│       └── run_info.json
├── ileum
│   ├── SRR8265592
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265593
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265594
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265595
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265596
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265597
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265598
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265599
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265600
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265653
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265654
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265659
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   └── SRR8265660
│       ├── abundance.h5
│       ├── abundance.tsv
│       └── run_info.json
├── jejunum
│   ├── SRR8265631
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265632
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265651
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265652
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265655
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265656
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   ├── SRR8265657
│   │   ├── abundance.h5
│   │   ├── abundance.tsv
│   │   └── run_info.json
│   └── SRR8265658
│       ├── abundance.h5
│       ├── abundance.tsv
│       └── run_info.json
└── liver
    ├── SRR8265553
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265554
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265555
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265556
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265611
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265612
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265613
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265614
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265615
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265616
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265617
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265618
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    ├── SRR8265619
    │   ├── abundance.h5
    │   ├── abundance.tsv
    │   └── run_info.json
    └── SRR8265620
        ├── abundance.h5
        ├── abundance.tsv
        └── run_info.json

68 directories, 189 files

```

### Todos for Tomorrow:

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segement
    - they may have done some of this heavy lifting for us.
- site for microbiome
  - ingest Zou
- continue reading jones
- Visualize Ampliseq
  - add example params and slurm for ampliseq into ampliseq-vis repos
- Run Visualize Ampliseq
  - on low med high richness samples
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Try to run DESeq2’s GLM/LRT on shaile’s design

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

### Git Commits

#### Lab Notebook

```bash
de3e3b2 - Benjamin Lorentz, Wed Nov 9 12:02:10 2022 -0500 : updated note
44d5fe9 - Benjamin Lorentz, Wed Nov 9 11:58:53 2022 -0500 : updates before lunch
b4b473e - Benjamin Lorentz, Wed Nov 9 08:34:56 2022 -0500 : added page for wednesday
```

#### Host Microbe Interaction

```bash
e8abd60 - Benjamin Lorentz, Wed Nov 9 16:58:21 2022 -0500 : ingested all but zou
8d8cba4 - Benjamin Lorentz, Wed Nov 9 15:08:36 2022 -0500 : halfway through tilocca
00b0748 - Benjamin Lorentz, Wed Nov 9 14:01:09 2022 -0500 : added oakley and roles of scfas
bd1ea52 - Benjamin Lorentz, Wed Nov 9 12:01:10 2022 -0500 : had to add header to sergant
c5fb3ee - Benjamin Lorentz, Wed Nov 9 11:59:25 2022 -0500 : ingesting fronk and hooper
2281fc3 - Benjamin Lorentz, Wed Nov 9 09:33:18 2022 -0500 : updated reference and cross-refernce links
```

#### Term Paper

```bash
4834a46 - Benjamin Lorentz, Wed Nov 9 08:29:08 2022 -0500 : needed to separate liver and bracket
```
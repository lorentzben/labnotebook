---
title: DESeq2 Results
author: Ben Lorentz
date: '2022-12-01'
slug: deseq2-results
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Run DESeq2 analysis on htseq-count table (STALE)
- Write Results Section for Term Paper
- Visualize Ampliseq (STALE)
  - examine slurm run 15474870

### Gene 8940 Term paper

#### HTSeq Results

Chunk 1 of the day: I scp'd the tsv files off of the teach cluster and peaked into one using head. I then started implementing some logic to add them together into a count matrix.


#### DESeq2 analysis

Chunk 2 of the day: I was able to join the counts into a count matrix and re-run some of the DESeq2 code that I had written previously. I am looking at modifying the filtering parameters to fit what the authors had written.

Chunk 3: modify code to follow author's parameters of |log2FC| > 1.5 and pvalue <= 0.05

(fold-change (FC) > 1.5 and p-value ≤ 0.05) 

author jejunum: 836 
my jejunum: 33
my jejunum p-adj: 17

their ceca: 142
my ceca: 331
my ceca p-adj: 130

their duodenum: 77
my duodenum: 151
my duodenum p-adj: 6

their liver:  73
my liver: 683
my liver p-adj: 240

their ileum: 54
my ileum: 398
my ileum p-adj: 201

The only thing that might be off is they say that they modified the STAR results with samtools before HTSeq, so one option is that sorting by name makes a difference for HTSeq but I'm not sure that's the case.

We can join these tables to the supplementals and see the shared genes, and then pick a subset of most DEs Genes to run through david analysis, that were not part of the paper's analysis.

An addition is that we could also make significance tables with the more stringent cutoffs, but I think we should just first get some initial results. 

TODO: Confirm Metadata is not malformed
- make sure that when the metadata is loaded (kallisto, sleuth, DESeq2) that the SRR line up to the tissue and FCR
  - I crossed check the 
- run a spearman correlation on L2FC to cross check kallisto/sleuth res to HTSeq/DESeq2 results.
- if anything other than defaults make sure to label

#### Sleuth and DESeq2 correlations

- generate full count tables for each tissue from Sleuth

  I updated the various sleuth scripts to save the results and whole tables to disk
  slurm:33125
  revision: b7ca8eec37a0ae8703e21645e91e6c3bc6067cfe
  this suceeded, however I need to fix the naming
  
- generate full count tables for each tissue from DESeq2
  - make sure these files get saved in the correct dir.
  
- link gene id's to transcript ids
- run spearman's correlation on log2 fc based on gene ID


#### Results

What's the story?

What did they observe (what kind of pathways were enriched or depleted), what did I observe, what does this tell us?

Who are the most differentially expressed genes from my analysis that were not intersected with their analysis? Look at them through DAVID or find the Gene ontology and see if it is similar methods to the results they observed. 


### Todos for Tomorrow:

- Term paper
  - generate full count tables for each tissue from Sleuth
  - generate full count tables for each tissue from DESeq2
  - link gene id's to transcript ids
  - run spearman's correlation on log2 fc based on gene ID
  - Write Results Section for Term Paper
  - Weekly update
- Visualize Ampliseq (STALE)
  - examine slurm run 15474870
  
  
### Git commits

#### Lab Notebook

```bash
f49eda7 - Benjamin Lorentz, Thu Dec 1 11:41:13 2022 -0500 : add thoughts and results comparing other authors work and mine
781b09e - Benjamin Lorentz, Thu Dec 1 09:20:01 2022 -0500 : page for thursday
f6722f8 - Benjamin Lorentz, Thu Dec 1 09:16:30 2022 -0500 : update git ignore
5c38078 - Benjamin Lorentz, Wed Nov 30 17:10:03 2022 -0500 : last notes about work for Wednesday
```

#### Gene 8940 Term paper

```bash
b7ca8ee - Benjamin Lorentz, Thu Dec 1 16:36:30 2022 -0500 : update all sleuth wt to save full table to disk
fbfd7ae - Benjamin Lorentz, Thu Dec 1 11:39:40 2022 -0500 : deseq2 analysis with researchers parameters
9f80a20 - Benjamin Lorentz, Thu Dec 1 09:55:29 2022 -0500 : preliminary logic to make a count matrix
```
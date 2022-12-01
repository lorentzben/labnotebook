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

(fold-change (FC) > 1.5 and p-value ≤ 0.05) 

author jejunum: 836 
my jejunum: 33

their ceca: 142
my ceca: 331

their duodenum: 77
my duodenum: 151

their liver:  73
my liver: 683

their ileum: 54
my ileum: 398

The only thing that might be off is they say that they modified the STAR results with samtools before HTSeq, so one option is that sorting by name makes a difference for HTSeq but I'm not sure that's the case.

We can join these tables to the supplementals and see the shared genes, and then pick a subset of most DEs Genes to run through david analysis, that were not part of the paper's analysis.

An addition is that we could also make significance tables with the more stringent cutoffs, but I think we should just first get some inital results. 

#### DAVID analysis

#### Results

What's the story?

What did they observe (what kind of pathways were enriched or depleated), what did I observe, what does this tell us?

Who are the most differentially expressed genes from my analysis that were not intersected with their analysis? Look at them through DAVID or find the Gene ontology and see if it is similar methods to the results they observed. 

### Visualize Ampliseq

I need to examine this today


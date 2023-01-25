---
title: 'Zhang Relative Abundance'
date: 2023-01-25T15:37:37Z
draft: false
meta_img: "images/image.png"
tags:
  - "metagenome assembled genome"
  - "MAGs"
  - "zhang"
  - "relative abundance"
  - nextflow
description: "Description for the page"
---

### Todos for Tomorrow

- gg-catalog
  - Zhang
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Summarize info for meeting with Aggrey

### gg-catalog

#### Zhang

from the Huang Paper


Taxonomic assignments of protein sequences were made on the basis of DIAMOND (v0.8.28.90 diamond blastp --evalue 10 --max-target-seqs 250) alignment against the NCBI-NR database by CARMA3 (carma --classify-blast --type p --database p) [76, 77]. A number of 64,332 genes (0.71%) classified as eukaryota but not fungi were excluded from the non-redundant gene set, and the final chicken gut gene catalog includes 9,037,241 genes.

To calculate of relative gene abundance, the clean reads from each sample were aligned against the gene catalog by BWA-MEM with the criteria of alignment length ≥ 50 bp and identity > 95%. Sequenced-based abundance profiling was performed as previously described [81]. Phylum, genus, species, KO, and OG relative abundances were calculated by summing the abundance of the respective genes belonging to each category per sample, based on the taxonomic assignments, KO and OG annotations, respectively. The relative gene abundance profile was also summarized into KEGG and eggNOG functional profiles for the functional analysis. The gene relative abundance profiles and sequences of integrated gene catalog (IGC) of human gut microbiome [16], and the reference gene catalog of the pig gut metagenome [17], were downloaded and analyzed by the same KEGG and eggNOG functional annotation pipeline in our study.


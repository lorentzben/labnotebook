---
title: Star and Diagnosing Ampliseq
author: Ben Lorentz
date: '2022-11-16'
slug: star-and-diagnosing-ampliseq
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Tomorrow:

- Run the kallisto wt on updated kallisto results
- Run the data through DESeq after samtools(?) or alignment..
- Update Visualize ampliseq to use the correct channel
- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- Re-Run the low med high analyses
  - Run Visualize Ampliseq
    - on low med high richness samples
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca


### Term Paper

Today I want to run Sleuth WT on the Kallisto with the correct index. I also want to examine the results from Star and see if we can pass it into HTSeq and then make a count table for DESeq2 or another data structure

### Visualize Ampliseq

nf-core/ampliseq keeps hanging on one last job. I want to clean up the work dir and the assets dir and then re-start the analysis of just the low samples to see if is a code or a resource issue. 

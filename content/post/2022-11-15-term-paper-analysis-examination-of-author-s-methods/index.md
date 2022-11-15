---
title: Term Paper Analysis & Examination of Author's Methods
author: Ben Lorentz
date: '2022-11-15'
slug: term-paper-analysis-examination-of-author-s-methods
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- talk to Casey in person about analysis and how to write the words part about a flub
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

First order of today is to collect Sleuth results from the teaching cluster, then do a quick analysis of the members identified and how they are related to the results the author found (from supp tables 6-10). Then follow the analysis from class using Hisat2. Then seeing if we can emmulate their results. We should also make sure we are taking some good notes. 

Then we need to update the visualize ampliseq pipeline to include the correct channels. 

### Term Paper 

I have collected the supplamentatry tables 6-10 from the original analysis. I have also collected my results that parallels the authors analysis using Kallisto and Sleuth. I think I want to spend the time to start the HISAT2 and DESeq2 analysis and then try to join the gene lists to see who is left on each side. This way I can talk to Dr. Bergman about who is missing and the methods of analysis. 

I am a little confused as the methods for DEG in the old way, we use HISat2 to align and get sam -> bam files, but then how does hiseq2 know... we just feed the samfile and then the GTF file with the annotations.

I want to build a [Kallisto specific index](https://github.com/pachterlab/kallisto-transcriptome-indices) to see if that provides different results.






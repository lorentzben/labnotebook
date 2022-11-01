---
title: How does GLM work for Deseq2 type analysis
author: Ben Lorentz
date: '2022-11-01'
slug: how-does-glm-work-for-deseq2-type-analysis
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:
- Term Paper
  - Collect reference genome and annotations
- continue reading jones
- Visualize Ampliseq
  - Refine chunk 06
  - add example params and slurm for ampliseq into ampliseq-vis repos
- nf-core/Ampliseq
  - compare low, medium, high richness results
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Shaile’s compare flip/flop and reply to his email

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters


Today I want to check out the multi qc results for my term-paper analysis, as well as understand how to run a GLM type model for DE data to be able to get back to Shailes.


### Multi-QC

The mulitqc document looks pretty good. The reads are about 200bps long, and quality for the reverse reads does drop off however based on [this article](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-016-0956-2) it sounds like you don't need to trim data, since the pseudo aligners will soft-mask the low-quality or unmapped data. 

### GLM for DESeq2 type analysis

This might be the approach to look into...

Using this design is similar to adding an interaction term, in that it models multiple condition effects which can be easily extracted with results. Suppose we have two factors genotype (with values I, II, and III) and condition (with values A and B), and we want to extract the condition effect specifically for each genotype. We could use the following approach to obtain, e.g. the condition effect for genotype I:

```R
dds$group <- factor(paste0(dds$genotype, dds$condition))
design(dds) <- ~ group
dds <- DESeq(dds)
resultsNames(dds)
results(dds, contrast=c("group", "IB", "IA"))
```

- https://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html#interactions

This [thread](https://support.bioconductor.org/p/90738/) seems like it might be helpful in shaile's experimental design. 

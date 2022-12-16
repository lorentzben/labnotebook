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


I had a really good talk with Dr. Bergman today during class about this DE stuff. He said personally he hasn't done that intense of a project design but pointed me towards [Daniel Hall](https://www.stat.uga.edu/directory/people/daniel-hall) and [Paul Schliekelman](https://www.stat.uga.edu/directory/people/paul-schliekelman) who he said may have contacts I could meet with to discuss GLM/LRT type modeling and seeing how to make that work. 

I also found the [Time series section of the DESeq2 program](http://bioconductor.org/packages/devel/bioc/vignettes/DESeq2/inst/doc/DESeq2.html#time-series-experiments) which wasn't super helpful other than outlining that the LRT methodology will only show pertubations in genes across all of the time periods it won't tell you which ones. From the docs "The test determines if the increased likelihood of the data using the extra terms in the full model is more than expected if those extra terms are truly zero." so if you use it with interaction of time:treatment and you receive significant p-values then that interaction is evidence of Differential expression.

The next tutorial I found was the [RNA Seq tutorial](http://master.bioconductor.org/packages/release/workflows/vignettes/rnaseqGene/inst/doc/rnaseqGene.html#time-course-experiments) I'm not too sure how useful this one really is, but it supposedly showcases time course experimentation. 

[This person](https://support.bioconductor.org/p/9137492/#9137696) organized a reproducible example, though theirs have unbalanced samples and only 2 treatments so it still might not be what I want but I want to have it documented. 

[This Person](https://support.bioconductor.org/p/105497/) They examined using 9 pairwise comparsions (for each time point) and cites [this one](https://support.bioconductor.org/p/95493/#95570) which will give you differential expression profile over time across genotype AND genes that show any difference across time " average fold change in expression due to genotype across all time points". I'm not 100% certain if I understand exactly what they mean, but I think it is the first will tell you if at any time point one genotype is being expressed closer to the reference/other than it has been previously. The second comparison will be genes varying by time. 

I think stare at [these graphs](https://hbctraining.github.io/DGE_workshop_salmon_online/lessons/08b_time_course_analyses.html) for a little bit and then you might get it. Also respond to Dr. Bergman and maybe ask him if he thinks you're on the right track and then possibly reach out to the stats people. 


### Todos for Tomorrow:
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
  - after touch base with Dr. Bergman Reach out

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
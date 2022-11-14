---
title: Shailes Deseq2 analysis
author: Ben Lorentz
date: '2022-11-14'
slug: shailes-deseq2-analysis
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Check what Casey said in slack (if the uncorrected p-vals and FC had the same number of hits)
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

- Try to run DESeq2’s GLM/LRT on shaile’s design

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

I was able to build a docker image that includes DESeq2, I need to update the docker image to run R-studio (comment out the cmd at the end). Then try to implement the GLM code with contrasts.

Next try to implement Dr. Bergman's Suggestions to see if the methods match the paper (closely). 

Next Review the ampliseq run to see if there is still issues with the diversity analysis. I think the next best solution would be to use core metric out for chunk 10. 
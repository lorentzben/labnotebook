---
title: Project Check in and Examining Ampliseq Results
author: Ben Lorentz
date: '2022-11-02'
slug: project-check-in-and-examining-ampliseq-results
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Todos for Today:
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

- Try to run DESeq2's GLM/LRT on shaile's design
- Learn a little more about GLM in R

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters


I think we should spend like 2 sections of a pom on general GLM and then if we aren't getting far then we can pivot to examining the results from ampliseq, and report 06/ the rest in that batch. Then we can work on outlining the project description for my term paper. 

### Notes on Broliers

"Conventional broiler (meat) chickens reach a final weight of 6.6 lbs (3kg) in approximately ***40-44 days***. Across their lifetime, these fast-growing birds gain an average of 68-75 g per day, with daily gain increasing with age (Aviagen, 2022; Cobb, 2022)." - https://www.poultry-welfare-extension.com/uploads/2/5/6/3/25631086/pec_newsletter_nov22__1_.pdf

### General GLM in R

"GLM in R is a class of regression models that supports non-normal distributions and can be implemented in R through glm() function that takes various parameters, and allowing user to apply various regression models like logistic, poission etc., and that the model works well with a variable which depicts a non-constant variance, with three important components viz. random, systematic, and link component making the GLM model, and R programming allowing seamless flexibility to the user in the implementation of the concept." - https://www.educba.com/glm-in-r/

I think that [this thread](https://www.seqanswers.com/forum/bioinformatics/bioinformatics-aa/42269-deseq2-model-matrix-formula) might explain how to compare difference in groups in tissue compared to general difference in groups. 

I went and got three books:
  - Linear Mixed Models West Welch and Galecki 2007
  - Using Multivariate Statistics Tabachnick and Fidell 1996
  - Optimum Design for Multi-Factor Models Schwabe 1996
  
We'll see if there's anything really helpful in them.


### Ben Jackwood

Ben stopped by to ask about trying to align a Gene HAT2 or GCS1 to an Eimeria Maxima reference genome, but the genome was only in contigs so when he tried to just aligh the sequence to the whole genome it took forever/wouldn't finsh. I suggested he blast his query sequence against the reference genome and he recieved 2 high-quality hits. He pulled those regions out and used MAFFT and Clustalw to align the query sequence to the reference and was able to get some okay alignments but the repetitive elements make it a little difficult to line up well. I suggested he could also try BWA-aligner if he wanted to get into cli tools. 


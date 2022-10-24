---
title: Project decision for GENE 8940E
author: Ben Lorentz
date: '2022-10-24'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Set up google scholar alert for: *Done*
  - broiler microbiome
  - layer microbiome
  - genetics gallus
  - rna seq poultry
  - multi-omics poultry
  - 16s rRNA and poultry
  - shotgun sequencing poultry
  - host-microbiome interaction and poultry.

- Watch lecture for class Tuesday. *Done*
- Look into genomic type project for class (see project description) *In Process*
  - Where did they suggest we get data from for Dr. Bensasson and Dr. Leebens-Mack's Class
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
  
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running
- Look into classes for the Spring semester
- What are we talking about with Shailes tomorrow


I set up a Daily alert using [Stork](https://www.storkapp.me/) so that I can scan really quickly and see if there are any papers that look liek they are worth reviewing. A second option could be setting up an [EBSCO alert](https://connect.ebsco.com/s/article/How-to-Use-Journal-Alerts?language=en_US) if I don't like the types of results I am getting. 

I collected 7 papers so far to read and see what information I can collect.

### Term Project Selection

Project Idea: Find a DE analysis in poultry that used the Bowtie or old form analysis and re-analyse it using kallisto and see what the technical variation looks like. 

I found two papers one looking at genetic markers (SNP calling) and transcript data that would be good for re-analysis. The researchers used QIIME1 and DESeq2 and Hisat (previous generation analysis methods) so re-analyzing to see if there is any improvement or insight could be very interesting to me. 

I want to check the integrity of the data from [this study](https://doi.org/10.1038/s41522-019-0096-3) to ensure that it seems like a smart idea for analysis. 

I set up the repository called [gene8940-term-paper](https://github.com/lorentzben/gene8940-term-paper) to track progress on this project. The first step is interactively collecting the data, then following steps will be automated. 

### Papers For Today

#### Sheets et. al. 2022 

This paper seems like a decent overview of comparing Illieal and Cecal microbiome differences over 48 days and comparing between slow growing and fast growing broilers. I do have some concerns about the effects they stated they observed especially that the only big difference between lines was at day 7 and then the lines seemed somewhat similar?
My notes are here: [Sheets et al 2022](sheets)
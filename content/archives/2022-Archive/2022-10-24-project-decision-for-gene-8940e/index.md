---
title: Project decision for GENE 8940E
author: Ben Lorentz
date: '2022-10-24'
slug: ['projectDecision']
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

My goal for the end of today is to get a multiqc report for the data, and/or at least the RNA-seq data. 

Submitted slurm job 31700 with revision ab880413e59a475be610cfccc381731b31faddbc to fastq-dump the files. Will followup with multiqc tomorrow after organizing fastqs. 

### Papers For Today

#### Sheets et. al. 2022 

This paper seems like a decent overview of comparing Illieal and Cecal microbiome differences over 48 days and comparing between slow growing and fast growing broilers. I do have some concerns about the effects they stated they observed especially that the only big difference between lines was at day 7 and then the lines seemed somewhat similar?
My notes are here: [Sheets et al 2022](/2022/10/24/sheets-et-al-2022/).

#### Jones Multi Omics 

This paper is much longer since it is a disseration. I made it about halfway through and I think I will like some of the modeling they will discuss but I am running out of time for today so I'm gonna take it home or pick it up tomorrow.


### Todos for Tomorrow:

- Meet Dr. Bergman and talk about paper/data
- Generate metadata/mappign file for chosen dataset
- Run multiqc on chosen dataset
- What are we talking about with Shailes tomorrow

--- 

- continue reading jones
- Look into classes for the Spring semester
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running



### Git Commits

#### Lab Notebook

```bash
7b27cfb - Benjamin Lorentz, Mon Oct 24 15:52:49 2022 -0400 : update paper link again
cb15122 - Benjamin Lorentz, Mon Oct 24 15:50:49 2022 -0400 : try to better rename link
c19fc4f - Benjamin Lorentz, Mon Oct 24 15:49:15 2022 -0400 : try to put papers in a specific dir
104c31b - Benjamin Lorentz, Mon Oct 24 15:39:43 2022 -0400 : have to get the date correct
2fdb512 - Benjamin Lorentz, Mon Oct 24 15:38:14 2022 -0400 : update link for paper
1aa8f50 - Benjamin Lorentz, Mon Oct 24 15:36:56 2022 -0400 : need to close quotes
a5811ee - Benjamin Lorentz, Mon Oct 24 15:34:29 2022 -0400 : move permalink to bottom
492614a - Benjamin Lorentz, Mon Oct 24 15:30:56 2022 -0400 : added slugs
f261150 - Benjamin Lorentz, Mon Oct 24 15:24:00 2022 -0400 : change permalink
3ad495a - Benjamin Lorentz, Mon Oct 24 15:21:22 2022 -0400 : try this
e083a62 - Benjamin Lorentz, Mon Oct 24 15:19:19 2022 -0400 : trying a different link
ac4471e - Benjamin Lorentz, Mon Oct 24 15:09:16 2022 -0400 : added a page for the paper I read today
9c8f21e - Benjamin Lorentz, Mon Oct 24 12:01:26 2022 -0400 : notes up to lunch
346e007 - Benjamin Lorentz, Mon Oct 24 08:55:51 2022 -0400 : notes about paper alerts
ff5d1b5 - Benjamin Lorentz, Mon Oct 24 08:33:41 2022 -0400 : added page and todos for monday
```

#### gene8940-term-paper

```bash
ab88041 - Benjamin Joseph Lorentz, Mon Oct 24 16:43:42 2022 -0400 : dos2unix
328a018 - Benjamin Lorentz, Mon Oct 24 16:43:13 2022 -0400 : added slurm script
aea8616 - Benjamin Lorentz, Mon Oct 24 16:41:51 2022 -0400 : change wd and comment out prefetch
3c3be61 - Benjamin Lorentz, Mon Oct 24 13:59:22 2022 -0400 : skeleton to download data
4f48159 - Ben Lorentz, Mon Oct 24 13:21:09 2022 -0400 : Initial commit
```
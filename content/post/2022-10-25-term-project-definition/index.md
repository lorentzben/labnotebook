---
title: Term Project Definition
author: Ben Lorentz
date: '2022-10-25'
slug: term-project-definition
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---



### Todos for Today:
- Meet Dr. Bergman and talk about paper/data
- Generate metadata/mapping file for chosen data set
- Run multiqc on chosen dataset
- What are we talking about with Shailes tomorrow

- continue reading jones
- Look into classes for the Spring semester
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running


### Run Multi-QC 

I submitted slurm job 31797 with revision 76979fde3bf3d5fdc3cf9ce8202eb53ef1a05a46 to run multiqc on the directory of raw data. The next step will be to map the reads to the metadata to extract the rna seq data. 

We needed to include the fastqc analysis before multiqc. I updated the script and submitted job 31798 with revision  01d911204d964a68dfabf48fa36750d4272edfd2. We need to tell fastqc the name of the files, which we did and submitted job 31799 with revision 489435eca3c1f3461137b0d09ae4db99b35be750. 
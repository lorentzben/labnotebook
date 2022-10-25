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
- Meet Dr. Bergman and talk about paper/data *Done*
- Generate metadata/mapping file for chosen data set
- Run multiqc on chosen dataset *Doing*
- What are we talking about with Shailes tomorrow
- lecture for Thursday.

- continue reading jones
- send regmi the paper *Done*
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

I wanted to also only run Multi-QC on the RNA-seq data as opposed to all of the reads together. To re-download and perform this analysis I submitted slurm job 31820 with revision 6e562f8cf2008eb4c90f75b8cc0e450e62ea094a.


### Meeting with Dr. Bergman

I want to start with the RNA-seq data from [this paper](https://www.nature.com/articles/s41522-019-0096-3#Sec2) to confirm their findings with updated tools. 

Just RNA seq is good, there are like 6 tissues. 2 tissues with 2 treatments. Mileage is in the analysis design. Keep the comparisons simple. Compare intra tissue high vs low. It feels good to feel validated in my choices for my analysis. 

### Making Metadata for Term paper analysis

- the separate data locations is frustrating. I needed to download the ["summary"](https://github.com/lorentzben/gene8940-term-paper/blob/main/bioproj_metadata.csv) and ["runinfo"](https://github.com/lorentzben/gene8940-term-paper/blob/main/SraRunInfo.csv) sheets from the bioproject site. We need to join the tables by the columns (Sample Accession,sample). We'll write a script to build it but also save the metadata file to the repo. There was some by-hand modification we needed to do, so the final formatted metadata is stored in the metadata dir. 
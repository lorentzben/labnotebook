---
title: Summarizing Information in Host Microbiome
author: Ben Lorentz
date: '2022-11-10'
slug: summarizing-information-in-host-microbiome
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segement
    - they may have done some of this heavy lifting for us.
- site for microbiome
  - ingest Zou
- continue reading jones
- Visualize Ampliseq
  - add example params and slurm for ampliseq into ampliseq-vis repos
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

Today I want to finish ingesting the documents and then summarize each page's information. I know we will be working on my term paper later today during class time. I should also at least download Shailes' data to see what it looks like. Finally we should look at the results from visualize ampliseq 2. 

### Host Microbiome Interaction

I added some summaries in 

Ceca:

Ceca are the transition point between the small and large intestine. Fermentation of carbohydrates is an important process in the ceca with one of the major byproducts being short chain fatty acids (SCFAs). Genes related to glycosyl hydrolase are commonly present. [source](https://lorentz-host-microbe-interaction.netlify.app/segments/ceca/)

Small Intestine:

The most protein degradation and digestion happens in the small intestine, especially the duodenum and jejunum. Some of the active enzymes that cleve protien are trypsin, chymotrypsin, carboxypeptidase and proelastase. These split off ammino acids are absorbed in the small intestine.  In the duodeunm the environment changes from acidic to alkaline with the addition of bile and excretions from the pancrease. Most of the absorption occurs in the jejunum due to its large size. When passing into the Ileum water and minerals are primarily absorbed, less digestive and AA absorption is observed in the ileum. [source](https://lorentz-host-microbe-interaction.netlify.app/segments/small-intestine-duodneumjejunumileum/)

### Term paper progress

I have a directory of Kallisto results that is separated by tissue type. My next step is to generate a report for each tissue to compare which genes are differentially expressed.

I am going to make 5 different rscripts (one for each tissue) and then a driver slurm script.
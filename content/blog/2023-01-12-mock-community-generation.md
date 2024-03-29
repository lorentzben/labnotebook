---
title: 'Mock Community Generation'
date: 2023-01-12T13:07:51Z
draft: false
meta_img: "images/image.png"
tags:
  - "mock microbial"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Today:

- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Examine some papers collected

### Generate Mock Community

Jeff Gordon seems like one of the pioneers in [gut microbiome research](https://gordonlab.wustl.edu). 
His (selected) Research Questions:
  - What are the genomic and metabolic foundations of our relationships with beneficial gut microbes? 
  - Can we intentionally and durably change the properties of our gut microbial communities (microbiota) to improve health?
How the lab answers those questions:
  - sequencing of gut microbial community DNA as well as the genomes of cultured microbial (primarily bacterial) members of the human gut community, 
  - whole genome transposon mutagenesis of cultured human gut bacterial strains to identify fitness determinants in vitro and in gnotobiotic animal models,
  - RNA-Seq and targeted mass spectrometry-based analyses of the responses of members of the microbiota to dietary and other perturbations applied to our gnotobiotic animal models
  - assays of metabolic flux, energy balance, innate and adaptive immune responses, bone biology, and CNS metabolism/functional connectivity in our preclinical models
  
From [Uchicago news](https://news.uchicago.edu/explainer/how-microbiome-affects-human-health-explained): 

One big problem with microbiome research:

"All of this research might give the impression that if disruptions of the microbiome lead to disease, one could treat those same diseases by restoring a “healthy” microbiome. That’s the ultimate goal, but many of the early links between the microbiome and health are just correlations—that is, researchers catalogued differences the microbiome of healthy people and those with a disease, but don’t yet understand the details. We still have much to learn about the specific mechanisms and types of microbes that lead to these disruptions."

From [Poultry World](https://www.poultryworld.net/health-nutrition/core-metagenomic-functions-of-the-poultry-microbiome/):

"Nitrogen utilisation pathways control the degradation and biosynthesis of peptides. Amino acids synthesised by the microbiome can be absorbed by the bird to increase effective protein availability. In animal production, adverse protein fermentation may generate excess ammonia, biogenic amines, and nitrogenous toxins that degrade barrier function, trigger inflammation, reduce welfare and increase environmental impact."

Huang et. al. 2018

There is a ftp:// ftp.agis.org.cn/~fanwei/Chicken_gut_metagenome ftp server that houses the gene catalog of all the genes from the chicken observed.

Big questions:
  - Who is there?
    - do they have a tax table in the supps?
    - can we classify their genes/seqs better than them? (better than diamond to NCBI-NR database)
    - can we extract 16s sequences from the raw reads and run those through a pipeline?
  - What are they doing?
    - Okay great we have a gene table what kind of processes are generally occuring
    - Is there any host-microbial interaction going on?
    - what genes are involved with nitrogen metabolism in the foregut? and what are involved in the hindgut?
    - can we look for those genes in HE/LE birds or another phenotype?
  
Zhang et. al. 2022

This paper has an overview of the MAGs that have been assembled based on multiple papers, they could be helpful to answer some of those big questions. 

### Todos for Tomorrow:

- Go Back to the Original question from Aggrey (from 8-22-22)
  - Explained to Dr. Aggrey my progress on papers
  - He suggested I begin by characterizing the taxa present in each gut segment
  - Then see what functional data we have for those and see what substrates will make it to the end 
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Examine some papers collected

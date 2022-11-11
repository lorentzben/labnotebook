---
title: Shailes DESeq2 analysis
author: 'Ben Lorentz'
date: '2022-11-11'
slug: shailes-deseq2-analysis
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- write weely update for Gene 8940
- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segement
    - they may have done some of this heavy lifting for us.
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

- rebuild docker image to include deseq2 
- Try to run DESeq2’s GLM/LRT on shaile’s design

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

Priories, today I want to rebuild the shailes picrust docker container and implement the DESeq2 differential expression methods. Then while that's building I want to update my github issue for the week (I should look at my notes from this site to see if there is any good information to include). Then I want to examine the Stork documents that I have received this week. 

### Making Shailes' Docker container 2.0.0

I also [made a github repo](https://github.com/lorentzben/my_dockerfiles/) for my dockerfiles so they are under some kind of version control. 

I am making a new [vanilla 4.2.2 dockerfile](https://github.com/lorentzben/my_dockerfiles/blob/main/r_4.2.2_vanilla/Dockerfile) and waiting for it to build. The image is located [here](https://hub.docker.com/repository/docker/lorentzb/r_vanilla). 

### Term Paper Update

I made a [comment for this weeks update](https://github.com/lorentzben/GENE8940/issues/6) outlining how much progress I have completed and linking to those files. It includes some notes like I sent in the post from yesterday. 
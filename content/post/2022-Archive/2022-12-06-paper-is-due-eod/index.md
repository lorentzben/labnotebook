---
title: Paper is due EOD
author: Ben Lorentz
date: '2022-12-06'
slug: paper-is-due-eod
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Term paper
  - Write Results Section
  - Write Methods Section 
  - format tables/graphics
  - write intro
- Visualize Ampliseq (STALE)
  - examine slurm run 15474870
- Host microbiome interaction
  - new paper
  
### Term Paper

#### Script 9

slurm: 33307
revision: 4b9aef9ab290f43203e0179dccede30eaa678cc9

```bash

```

#### Writing Methods

I need to go through the methods section and script by script state what they are doing and version numbers and revisions.

I also ned to state what parameters differ than the default.

#### Writing results

how many genes were in authors, how many were in sleuth, how many were in deseq2?

go through each result and outline where they are and what the significance is. 

I needed to re-generate the q-value tables

slurm: 33317
revision: a432323b8db4287dadba46ffa3d5b08fa53d1046


#### What I would expand on or improve

I want to make a table highlighting the number of genes and how many common genes were found and how many were lost

There is a possibility the metadata on NCBI was uploaded incorrectly. One way I could examine to see if this is the case is to run a PCA on the DEGs to see if the samples from each alleged tissue cluster together, and therefore 

### Visualize Ampliseq.

TBD

### Git commits

#### Lab Notebook

```bash
9e7ef67 - Benjamin Lorentz, Tue Dec 6 08:39:45 2022 -0500 : add page for tuesday
fc00583 - Ben Lorentz, Mon Dec 5 22:08:41 2022 -0500 : more updates from monday night
123bb3a - Ben Lorentz, Mon Dec 5 20:43:42 2022 -0500 : updated after notes about slurm run
0f10858 - Ben Lorentz, Mon Dec 5 20:18:26 2022 -0500 : testing update
```

#### Gene 8940 

```bash
1613507 - Benjamin Lorentz, Tue Dec 6 16:25:08 2022 -0500 : final version of paper
b42a97e - Benjamin Lorentz, Tue Dec 6 16:15:30 2022 -0500 : updated citations
823114a - Benjamin Lorentz, Tue Dec 6 16:14:49 2022 -0500 : introduction written
6e34035 - Benjamin Lorentz, Tue Dec 6 15:44:25 2022 -0500 : added conclusions
dc93ca9 - Benjamin Lorentz, Tue Dec 6 15:23:32 2022 -0500 : all tables incorporated
7bfe68c - Benjamin Joseph Lorentz, Tue Dec 6 15:01:38 2022 -0500 : add spearman results
f666bb0 - Benjamin Lorentz, Tue Dec 6 14:47:39 2022 -0500 : fix filtering on deseq, and add updates to deseq2 results
1961e5d - Benjamin Joseph Lorentz, Tue Dec 6 14:47:11 2022 -0500 : add determine strand
93dc005 - Benjamin Joseph Lorentz, Tue Dec 6 14:14:17 2022 -0500 : add deseq2 res
97a2b48 - Benjamin Lorentz, Tue Dec 6 13:53:28 2022 -0500 : update star result comparison
a6df648 - Benjamin Lorentz, Tue Dec 6 13:45:53 2022 -0500 : sleuth results written
02bf44c - Benjamin Joseph Lorentz, Tue Dec 6 13:23:27 2022 -0500 : Merge branch 'main' of github.com:lorentzben/gene8940-term-paper into main
1c7313e - Benjamin Joseph Lorentz, Tue Dec 6 13:23:11 2022 -0500 : added sleuth results
b18b30c - Benjamin Lorentz, Tue Dec 6 12:21:05 2022 -0500 : added kallisto table
a432323 - Benjamin Joseph Lorentz, Tue Dec 6 11:47:56 2022 -0500 : add python3 conda env file
b181a5b - Benjamin Lorentz, Tue Dec 6 11:47:16 2022 -0500 : add script to generate kallisto results table
5291cd3 - Benjamin Joseph Lorentz, Tue Dec 6 11:46:29 2022 -0500 : add table for kallisto results
7e86561 - Benjamin Joseph Lorentz, Tue Dec 6 11:11:34 2022 -0500 : add multi-qc report
9769a3e - Benjamin Lorentz, Tue Dec 6 11:10:41 2022 -0500 : save paper status
75f67bc - Benjamin Lorentz, Tue Dec 6 10:58:47 2022 -0500 : updates to the methods section, starting the results
4b9aef9 - Benjamin Lorentz, Tue Dec 6 08:23:28 2022 -0500 : fix filepath
69de085 - Ben Lorentz, Mon Dec 5 22:05:15 2022 -0500 : add some notes on scripts 9 and 10
9a87607 - Ben Lorentz, Mon Dec 5 21:52:01 2022 -0500 : Fix paren in 9
224f78b - Ben Lorentz, Mon Dec 5 21:46:30 2022 -0500 : Descriptive updates
bc02e59 - Ben Lorentz, Mon Dec 5 20:47:01 2022 -0500 : clean up dir
```
  
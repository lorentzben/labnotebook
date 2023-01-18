---
title: 'Examining MAGs'
date: 2023-01-18T15:25:13Z
draft: false
meta_img: "images/image.png"
tags:
  - "metagenome assembled genome"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today:

- Examine all MAGs uncovered
  - Summarize major players in each segment
    - try to join tables from each of these studies from 2023-01-13
  - Summarize gene content in each segment
  - Figure out how to present this to Dr. Aggrey
- Go Back to the Original question from Aggrey (from 8-22-22)
  - Explained to Dr. Aggrey my progress on papers
  - He suggested I begin by characterizing the taxa present in each gut segment
  - Then see what functional data we have for those and see what substrates will make it to the end 
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Examine some papers collected

### gg-catalog

I setup a repo for storing code and results called [gg-catalog](https://github.com/lorentzben/gg-catalog). I started development of a docker container for r-development but phyloseq was not installing in r version 4.2.2 so I might have to downgrade or install on a unix version of docker, stay tuned.

But I wanted to use rocker/verse as my base and include packages:

- renv (for dockerfiler)
- tidyverse
- phyloseq

### Todos for tomorrow

- gg-catalog
  - finish building docker image
  - read in Zhang table
  - create relative abundance table
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Git Commits

#### Lab Notebook

```bash
aa82797 - Benjamin Lorentz, Wed Jan 18 10:26:14 2023 -0500 : added page for wednesday
```

#### gg-catalog

```bash
095966d - Benjamin Lorentz, Wed Jan 18 11:50:02 2023 -0500 : more formatting
36f4f48 - Benjamin Lorentz, Wed Jan 18 11:49:30 2023 -0500 : readme formating
6c96f4d - Benjamin Lorentz, Wed Jan 18 11:49:07 2023 -0500 : update readme
9fb5f7f - Benjamin Lorentz, Wed Jan 18 11:48:35 2023 -0500 : updated readme
aecafd9 - Ben Lorentz, Wed Jan 18 11:19:56 2023 -0500 : Initial commit
```

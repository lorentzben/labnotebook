---
title: 'First MAG Table'
date: 2023-01-19T13:33:32Z
draft: false
meta_img: "images/image.png"
tags:
  - "metagenome assembled genome"
  - "MAGs"
  - "zhang"
description: "Description for the page"
---

### Todos for today

- gg-catalog
  - read in Zhang table
  - create relative abundance table
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### gg-catalog

I have a first docker image built from last night, the first step will be to load it up and see if it is good off the bat or if there are changes I need to make. Then I can start with the Zhang table. 

Zhang has 2 different summary tables ANI95 and ANI99 which are species and strain specific respectively. This begs the question: **Do we need species or strain specificity?** Aka what level can the other databases tell us?

I want to change the taxonomy column into a split taxonomy column, this either means finding a parse taxonomy function or writing my own version. 

I have a parser function set up currently, the next step is to separate the table out into tissues.

** What did the authors distinguish as rectum? ** 

We should pivot to the strain specific ANI99 even with this we only have: 

  Duodenum	8
  jejunum	19
  Ileum	25
  Cecum	167
  Rectum	242

We have the tables formed for each of the tissues right now. I want to see if I can pull them in as a phyloseq object or something.

I think the next step will be to examine the Huang 2018 data. There exist some 'ratio' tables, I want to look at their results to see the takeaways from there and methods used to get to this point. 

Next [people to examine](/blog/2023-01-13-core-microbiomes):

Short read catalogs: 
- Huang 2018 ~9 million genes from 495 chicken from 7 farms
- Glendinning 2020 469 MAGS from 24 chickens
- Segura-Wang 2021 155 MAGS from 751 chicken
- Gilroy 2021 5,595 MAGS from 632 chicken
- Feng 12,339 MAGs integrating 799 chicken samples from 10 countries

### Todos for tomorrow

- gg-catalog
  - examine the Huang table
    - examine methods
    - examine results
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Git Commits

#### Lab Notebook

```bash
88850c9 - Benjamin Lorentz, Thu Jan 19 12:03:17 2023 -0500 : updates before lunch
d2245ba - Benjamin Lorentz, Thu Jan 19 08:36:30 2023 -0500 : page for thursday
24ea347 - Benjamin Lorentz, Wed Jan 18 17:13:16 2023 -0500 : added notes for wednesday
```

#### gg-catalog

```bash
6379997 - Benjamin Lorentz, Thu Jan 19 16:09:17 2023 -0500 : updated 01_zhang and added output
2828ca3 - Benjamin Lorentz, Thu Jan 19 16:05:41 2023 -0500 : update 01_zhang
49f2e94 - Benjamin Lorentz, Thu Jan 19 12:01:30 2023 -0500 : add 01_zhang and data
17f6ce3 - Ben Lorentz, Wed Jan 18 20:55:43 2023 -0500 : added dockerfile
```
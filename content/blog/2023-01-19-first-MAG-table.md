---
title: 'First MAG Table'
date: 2023-01-19T13:33:32Z
draft: false
meta_img: "images/image.png"
tags:
  - "metagenome assembled genome"
  - "MAGs"
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


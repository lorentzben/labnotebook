---
title: 'Continue Kegg Tables'
date: 2023-08-01T12:39:54Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat 6315"
  - "microbiome-review"
  - "kegg ontology network"
  - "gg-catalog"
description: "Description for the page"
---

### Todos for Today

- gg-catalog
  - Fix broken for loop
  - select just the relative abundance table and check average
  - Make Tissue, then Pathway, then gene specific tables
  - Select top 25 most abundant genes from these tables
 
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday

- STAT 6315
  - Take exam 3 on Thursday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation

### gg-catalog

Need to edit 04 to just to select the relative abundance table.


Need to edit the for loop tomorrow to fix functionality.


For loop and kegg dict

TODO, rebuild docker to include collections.

Right now, I have a table where the key is kegg ontologies, each column is a relative abunance sample of those ontologies, and then the last column is a frequency count of the genes that fit into that ontology to be able to maybe point to who is changing. Is this the best approach?

An alternative I can approach is by selecting for keggs of interest in the gene table examining the genes; This gives us the benefit of knowing the DNA segement the gene came from but the drawback of not including relative abundance data which although a coarse selector might be helpful.

For my first approach I want to work with the relative abundance data. 


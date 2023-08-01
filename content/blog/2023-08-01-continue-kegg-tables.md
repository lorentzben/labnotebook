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

I finished the overall analysis, but it is not what we talked about at the last meeting, so I am going to rebuild the analysis to exactly what we talked about.

currently, we have average relative abundance by tissue, this is the main thing we are working off of. Next step is to filter these Rabundances by pathways and while doing that keep track of the genes that hit off of those keggs in the pathways and then we will be able to build up the whole table i think. 

TODO functionalize the kegg_gene_names dict and more info tables.

### Todos for Tomorrow

- gg-catalog
  - functionalize the dictionary generation and then the turning that into a more info table
  - apply it to each tissue and pathway combination
  - Select top 25 most abundant genes from these tables
  
 
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday

- STAT 6315
  - Take exam 3 on Thursday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation

### Git Commits

#### Lab Notebook

```bash
bf0ff40 - Benjamin Lorentz, Tue Aug 1 12:18:00 2023 -0400 : added notes before lunch
17f1f83 - Benjamin Lorentz, Tue Aug 1 08:41:43 2023 -0400 : added page for tuesday
2f5f107 - Benjamin Lorentz, Mon Jul 31 17:06:44 2023 -0400 : final notes for monday
```

#### gg-catalog

```bash
af4808f - Benjamin Lorentz, Tue Aug 1 16:54:31 2023 -0400 : update 04
7a5c214 - Benjamin Lorentz, Tue Aug 1 14:44:36 2023 -0400 : update 04 kegg git tables
fe16146 - Benjamin Lorentz, Tue Aug 1 12:14:32 2023 -0400 : update 04
a350b1d - Benjamin Lorentz, Tue Aug 1 11:38:02 2023 -0400 : update 04
de641fc - Benjamin Lorentz, Mon Jul 31 17:04:38 2023 -0400 : restructuring 04
```

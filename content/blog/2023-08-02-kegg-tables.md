---
title: 'Kegg Tables'
date: 2023-08-02T13:38:30Z
draft: false
meta_img: "images/image.png"
tags:
  - "microbiome-review"
  - "kegg ontology network"
  - "gg-catalog"
description: "Description for the page"
---

### Todos for Today

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
  
### gg-catalog

currently, we have average relative abundance by tissue, this is the main thing we are working off of. Next step is to filter these Rabundances by pathways and while doing that keep track of the genes that hit off of those keggs in the pathways and then we will be able to build up the whole table i think. 

TODO functionalize the kegg_gene_names dict and more info tables.

generate_kegg_gene_list(duo_average_df, protein_digestion_and_absorption, kegg_gene)

gastric_acid_secretion
pancreatic_acid_secretion
valine_leucine_isoleucine
tyrosine_metabolism
tryptophan_metabolism 
alanine_aspartate_glutamate 
nitrogen_metabolism 


jejunum_protein_gene_list <- generate_kegg_gene_list(jejunum_average_df, protein_digestion_and_absorption, kegg_gene)
jejunum_protein_more_info <- generate_more_info_table(data.frame(jejunum_protein_gene_list[1]),jejunum_protein_gene_list[2],"../data/huang-analysis/jejunum-protein-digestion-and-absorption.tsv")

I was able to generate a table for the Duodenum. The other 4 tissues are next. I am also curious if there is a better way to improve legibility when printing (since I know Dr. Aggrey likes to print) but that can be a tomorrow question (after the exam of course.))

### Todos for Tomorrow

- STAT 6315
  - Take exam 3
  
- gg-catalog
  - generate the Other 4 tables
 
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
  
### Git Commits

#### Lab Notebook

```bash
2c34d45 - Benjamin Lorentz, Wed Aug 2 14:52:12 2023 -0400 : update 04
8c86b45 - Benjamin Lorentz, Wed Aug 2 11:53:46 2023 -0400 : update 04
af4808f - Benjamin Lorentz, Tue Aug 1 16:54:31 2023 -0400 : update 04
```

#### gg-catalog

```bash
1f0d67a - Benjamin Lorentz, Wed Aug 2 13:20:34 2023 -0400 : notes pre lunch
08767ca - Benjamin Lorentz, Wed Aug 2 09:57:40 2023 -0400 : add page for wednesday
11f329a - Benjamin Lorentz, Tue Aug 1 16:56:20 2023 -0400 : final notes for tuesday
```
---
title: 'Other Tissues Gene Abundace'
date: 2023-06-22T13:26:47Z
draft: false
meta_img: "images/image.png"
tags:
  - "huang"
  - "kegg"
  - "gene network"
description: "Description for the page"
---

### Todos for Today

- STAT 6315
  - review homeworks as they come back 
  - get ready for Exam Friday at 12pm
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Generate a gene network 
    - Can I link my data like the Keggscape
      - yes you can, does it mean anything though?
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### gg-catalog

#### Generate Gene Network 

Next to examine Duodenum:

Subsample table code:

```R
library(tidyverse)


#select just gene names from kegg table so we can join on them later

kegg_tab <- read_table("../output/huang/kegg-gene-abundance.tsv")
kegg_simp <- str_split(kegg_tab$kegg_gene,":",simplify=T)
kegg_simp <- kegg_simp[,1]

# reassing gene names to 
kegg_tab$simple_kegg <- kegg_simp

#select cols with ceca in the 5th english letter

duo_samp <- kegg_tab[,str_sub(colnames(kegg_tab),5,5) == "D"]

n_samp <- dim(duo_samp)[2]

abund <- rowSums(duo_samp)

abund <- abund/n_samp

duo_average_table <- cbind(kegg_tab$ListOfKOs, kegg_tab$simple_kegg,abund)

duo_average_df <- data.frame(duo_average_table)
colnames(duo_average_df) <- c("kegg", "gene", "abundance")


write_tsv(duo_average_df,"../output/huang/duo-average-gene-abundance.tsv")

```
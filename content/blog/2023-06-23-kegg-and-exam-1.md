---
title: 'Kegg and Exam 1'
date: 2023-06-23T12:58:41Z
draft: false
meta_img: "images/image.png"
tags:
  - "huang"
  - "kegg"
  - "gene network"
  - "stat6315"
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
  - Update n in the table above
  - Implications of the networks generated
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Stat 6315

#### Exam 1 review questions

I am examining the review videos for exam 1

Assumptions we need to check for hypothesis testing: 

- independence: randomly selected 
- normality of phat: 
  - n*p > 15 n*1-p > 15
  - binomial no

Describe sampling dist 

- mean = p
- SD = sqrt(p 1-p/n) 
- Shape = np > 15 n(1-p) > 15 approx normally distributed 

Formula to calculate z score:

x-mu/stdev 

### gg-catalog

#### update n in the table from 6/22

from the readme:

5th English letter:
D	Duodeum
J	Jejunum
I	Ileum
C	Ceceum
R	Colorectum

| Tissue |	Min (average abundance)	| Max (average abundance) |
| --- | --- | --- | 
| Duodeum (n= 99) | 4.468E-10 | 	0.002938 |
| Jejunum (n= 99) |	3.84895E-10 |	0.00066612 |
| Ileum (n= 99) |	1.11E-09 |	0.000412775 |
| Ceceum (n= 99) |	1.23E-10 |	0.000370778 |
| Colorectum (n= 99) |	4.60E-10 |	0.000376139 |

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
```

#### What are the implications?

Nitrogen Metabolism 

- similar abundances of K01501 nitrilase

Protein Digestion

- higher abundance of K14211 elastin in Duodenum

Tryptophan Metabolism

- acetyl-CoA C-acetyltransferase K00626  
- amidase K01426 

My next stop was going to be find photogenically linked data and see what the abundances of these genes does.

I need to understand how Kegg points to the sequence and says, YUP that is doing this process etc. Then we might be able to look at what is happening in the microbiomes. 


### Todos for Next Week

- STAT 6315
  - lectures for homework 4
  - lectures for homework 5
  - lectures for homework 6
  - lectures for homework 7
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Implications of the networks generated
  - How does KEGG work?
  - Show Aggrey the charts and ask him what he thinks
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  - Some kind of machine learning classifier to determine major players in a phenotypic outcome.

### Git Commits

#### Lab notebook

```bash
e9d2a0d - Benjamin Lorentz, Fri Jun 23 11:31:55 2023 -0400 : add notes for exam1
c737ba1 - Benjamin Lorentz, Fri Jun 23 09:02:27 2023 -0400 : add page for friday
13e2c8a - Benjamin Lorentz, Thu Jun 22 17:03:16 2023 -0400 : final notes for thursday
```
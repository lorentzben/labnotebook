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


from the readme:

5th English letter:
D	Duodeum
J	Jejunum
I	Ileum
C	Ceceum
R	Colorectum

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

Nitrogen metabolism | Yes
Protein Digestion and Absorption | No
Tryptophan metabolism | Yes
Tyrosine Metabolism | Yes
Valine Leucine Isoleucine Degredation | Yes

Examine Jejunum

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

jeju_samp <- kegg_tab[,str_sub(colnames(kegg_tab),5,5) == "J"]

n_samp <- dim(jeju_samp)[2]

abund <- rowSums(jeju_samp)

abund <- abund/n_samp

jeju_average_table <- cbind(kegg_tab$ListOfKOs, kegg_tab$simple_kegg,abund)

jeju_average_df <- data.frame(jeju_average_table)
colnames(jeju_average_df) <- c("kegg", "gene", "abundance")


write_tsv(jeju_average_df,"../output/huang/jeju-average-gene-abundance.tsv")

```

We should be saving these as SVGs not pngs

Nitrogen metabolism | Yes
Protein Digestion and Absorption | No
Tryptophan metabolism | Yes
Tyrosine Metabolism | Yes
Valine Leucine Isoleucine Degredation | Yes

Examine Ileum

```R
library(tidyverse)


#select just gene names from kegg table so we can join on them later

kegg_tab <- read_table("../output/huang/kegg-gene-abundance.tsv")
kegg_simp <- str_split(kegg_tab$kegg_gene,":",simplify=T)
kegg_simp <- kegg_simp[,1]

# reassing gene names to 
kegg_tab$simple_kegg <- kegg_simp

#select cols with ceca in the 5th english letter

ileum_samp <- kegg_tab[,str_sub(colnames(kegg_tab),5,5) == "I"]

n_samp <- dim(ileum_samp)[2]

abund <- rowSums(ileum_samp)

abund <- abund/n_samp

ileum_average_table <- cbind(kegg_tab$ListOfKOs, kegg_tab$simple_kegg,abund)

ileum_average_df <- data.frame(ileum_average_table)
colnames(ileum_average_df) <- c("kegg", "gene", "abundance")


write_tsv(ileum_average_df,"../output/huang/ileum-average-gene-abundance.tsv")

```

Nitrogen metabolism | Yes
Protein Digestion and Absorption | No
Tryptophan metabolism | Yes
Tyrosine Metabolism | Yes
Valine Leucine Isoleucine Degredation | Yes

Examine Colorectum

```R
library(tidyverse)


#select just gene names from kegg table so we can join on them later

kegg_tab <- read_table("../output/huang/kegg-gene-abundance.tsv")
kegg_simp <- str_split(kegg_tab$kegg_gene,":",simplify=T)
kegg_simp <- kegg_simp[,1]

# reassing gene names to 
kegg_tab$simple_kegg <- kegg_simp

#select cols with ceca in the 5th english letter

rect_samp <- kegg_tab[,str_sub(colnames(kegg_tab),5,5) == "R"]

n_samp <- dim(rect_samp)[2]

abund <- rowSums(rect_samp)

abund <- abund/n_samp

rect_average_table <- cbind(kegg_tab$ListOfKOs, kegg_tab$simple_kegg,abund)

rect_average_df <- data.frame(rect_average_table)
colnames(rect_average_df) <- c("kegg", "gene", "abundance")


write_tsv(rect_average_df,"../output/huang/rect-average-gene-abundance.tsv")

```

Remake the ceca

Remake the duodenum

To be able to compare legends we need to know the min and max abundance of all keggs

| Tissue |	Min (average abundance)	| Max (average abundance) |
| --- | --- | --- | 
| Duodeum (n=) | 4.468E-10 | 	0.002938 |
| Jejunum (n=) |	3.84895E-10 |	0.00066612 |
| Ileum (n=) |	1.11E-09 |	0.000412775 |
| Ceceum (n=) |	1.23E-10 |	0.000370778 |
| Colorectum (n=) |	4.60E-10 |	0.000376139 |

### Todos for Tomorrow

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
  
### Git Commits

#### Lab notebook

```bash
0c8f188 - Benjamin Lorentz, Thu Jun 22 12:00:05 2023 -0400 : notes before lunch
c93207b - Benjamin Lorentz, Thu Jun 22 11:28:17 2023 -0400 : duodeum and jejunum
1c35535 - Benjamin Lorentz, Thu Jun 22 09:28:29 2023 -0400 : add page for Thursday
```

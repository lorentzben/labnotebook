---
title: 'Welcome Back'
date: 2023-06-21T13:46:20Z
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
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### gg-catalog


#### Copying the tutorial

From 6/8/23:

based on this one https://github.com/idekerlab/KEGGscape/wiki/How-to-duplicate-the-process-in-F1000research-article

using the docker image rocker/tidyverse:4.2

setting up the environment for the analysis

```bash

wget http://rest.kegg.jp/get/eco00260/kgml -O eco00260.xml

git clone https://github.com/bmbolstad/preprocessCore.git
cd preprocessCore
R CMD INSTALL --configure-args="--disable-threading"  .
```

pre-processing the gene expression data

```R

install.packages("BiocManager")
library(BiocManager)
BiocManager::install(c("genefilter", "ecoliLeucine"))

library("ecoliLeucine")
library("genefilter")
data("ecoliLeucine")
eset = rma(ecoliLeucine)
r = rowttests(eset, eset$strain)
filtered = r[r$p.value < 0.05,]
write.csv(filtered, file="ttest.csv")
```

 joining the kegg pathway and t-test matrix

my version which joins on the kegg gene name:

```python3

import csv
import re

ttest_re = re.compile("b[0-9]{4}")
lines = []

with open('ttest.csv') as ttest:
    ttestreader = csv.reader(ttest)
    for ttestrow in ttestreader:
        ttest_match = ttest_re.findall(ttestrow[0])
        if len(ttest_match) > 0:
            bnumber = ttest_match[0]
            bnumber_re = re.compile(bnumber)
            with open('keggnode.csv') as kegg:
                keggreader = csv.reader(kegg)
                for keggrow in keggreader:
                    kegg_match = bnumber_re.findall(keggrow[1])
                    if len(kegg_match) > 0:
                        lines.append(','.join(ttestrow) + ',"' + keggrow[4] + '"\n')

ttest4pathway = open('ttest4pathway.csv', 'w')

ttestheader = open('ttest.csv').readline().strip()
keggheader = open('keggnode.csv').readline().split(',')[4]

ttest4pathway.write(ttestheader + ',' + keggheader + '\n')
ttest4pathway.writelines(set(lines))
ttest4pathway.close()
```

my version which joins on the kegg gene name:

```python3

import csv
import re

ttest_re = re.compile("b[0-9]{4}")
lines = []

with open('ttest.csv') as ttest:
    ttestreader = csv.reader(ttest)
    for ttestrow in ttestreader:
        ttest_match = ttest_re.findall(ttestrow[0])
        if len(ttest_match) > 0:
            bnumber = ttest_match[0]
            bnumber_re = re.compile(bnumber)
            with open('keggnode.csv') as kegg:
                keggreader = csv.reader(kegg)
                for keggrow in keggreader:
                    kegg_match = bnumber_re.findall(keggrow[1])
                    if len(kegg_match) > 0:
                        lines.append(','.join(ttestrow) + ',"' + keggrow[5] + '"\n')

ttest4pathway = open('ttest5pathway.csv', 'w')

ttestheader = open('ttest.csv').readline().strip()
keggheader = open('keggnode.csv').readline().split(',')[5]

ttest4pathway.write(ttestheader + ',' + keggheader + '\n')
ttest4pathway.writelines(set(lines))
ttest4pathway.close()
```

I was able to fix the parsing script to use the proper gene names

Once in cytoscape:

- Load the network xml from file
- Import the table into an unassigned table and then merge on kegg symbols
- set the kegg style
- modify the fill color to set as p.value and gradient
- reverse the color gradient so the more significant the pvalue the darker the red.

#### Can I link my data like Keggscape?

First I need to pick a kegg network to overlay data on, so we picked gga00910 as the network of interest. Then we need to select which tissues are interesting. 

Start Ceca

from the readme:

5th English letter:
D	Duodeum
J	Jejunum
I	Ileum
C	Ceceum
R	Colorectum

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

ceca_samp <- kegg_tab[,str_sub(colnames(kegg_tab),5,5) == "C"]

n_samp <- dim(ceca_samp)[2]

abund <- rowSums(ceca_samp)

abund <- abund/n_samp

ceca_average_table <- cbind(kegg_tab$ListOfKOs, kegg_tab$simple_kegg,abund)

ceca_average_df <- data.frame(ceca_average_table)
colnames(ceca_average_df) <- c("kegg", "gene", "abundance")


write_tsv(ceca_average_df,"../output/huang/ceca-average-gene-abundance.tsv")

```

Nitrogen metabolism does not have anything that merges
Protein Digestion and Absorption also does not have anything that merges
Tryptophan metabolism does have abundance data associated 
Tyrosine Metabolism does have abundance data associated
Valine Leucine Isoleucine Degredation has abundance data associated with the map

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


### Todos for Tomorrow

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
  
### Git Commit

#### Lab Notebook

```bash
2906f91 - Benjamin Lorentz, Wed Jun 21 12:05:08 2023 -0400 : notes before lunch
cea20cf - Benjamin Lorentz, Wed Jun 21 10:01:39 2023 -0400 : added content for wednesday
37149ae - Benjamin Lorentz, Wed Jun 21 09:59:29 2023 -0400 : add page for Wednesday
```

#### gg-catalog

```bash
```


---
title: 'Kegg Networking'
date: 2023-06-07T13:40:13Z
draft: false
meta_img: "images/image.png"
tags:
  - "huang"
  - "kegg"
  - "gene network"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Generate a gene network 
    - Do the Keggscape followup from above
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.

### gg-catalog

#### Merging abundances with the data from KEGG

We have KO numbers in the kegg map data, and then we have ko numbers with the abundance data so can we join on then and maybe make an abundance map based on each tissue? (which would require subsetting out the columns based on tissue)

#### Cytoscape Kegg Tutorial

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
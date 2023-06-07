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
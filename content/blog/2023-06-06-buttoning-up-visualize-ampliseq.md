---
title: 'Buttoning Up Visualize Ampliseq'
date: 2023-06-06T13:23:54Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "Mock"
  - "Module"
  - "huang"
  - "kegg"
  - "gene network"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Update Tags for Visualize Ampliseq
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.

### Ade

#### Check out current version of ampliseq

cycle 4 rev: f97e241535c9f7702eeddf9350db760e65172279
visualize ampliseq rev: 33997cdb315d22eaddb6d464542f6e56ffacc3b4 
slurm job: 23272564

```bash
Completed at: 05-Jun-2023 17:01:57
Duration    : 1h 19m 9s
CPU hours   : 68.0 (95.4% cached)
Succeeded   : 11
Cached      : 33
```

This looks good to me, we have the params printed in the slurm file I merged it into 2.1.0

### gg-catalog

#### Where did we leave off?

The last file I was working on was gg-catalog/code/03_huang_examine.rmd

in the notebook page 2023-03-16-examine-keggs I said that I saved a table to file I have to look for that. I will start by repeating the steps on the server?

There are 277 keggs of interest from the kegg ontology database. 
There are 12890 keggs in the huang list
when intersecting them we have 192

we now have a dataframe that the columns are the keggs and the rows are abundances 

#### KEGGscape

We can use cytoscape to open KEGG pathways and then maybe we can link the gene abundance data possibly?

Try to follow [this](https://github.com/idekerlab/KEGGscape/wiki/How-to-duplicate-the-process-in-F1000research-article) duplication maybe that is something?

Previously I was ctrl-f ing the kegg ontologys present in my data and trying to find them in the kegg pathway from cytoscape, maybe this is an approach.

### Todos for Tomorrow

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

### Git Commits

#### Lab Notebook

```bash
2430933 - Benjamin Lorentz, Tue Jun 6 09:28:04 2023 -0400 : added page for Tuesday
d884d91 - Benjamin Lorentz, Mon Jun 5 17:05:23 2023 -0400 : final notes for Monday
```

#### gg-catalog

```bash
212c761 - Benjamin Lorentz, Tue Jun 6 16:18:16 2023 -0400 : updated 03 to save table
```

#### Visualize Ampliseq

```bash
1176707 - Benjamin Lorentz, Tue Jun 6 10:38:18 2023 -0400 : Merge branch 'srs' of github.com:lorentzben/visualize-ampliseq into srs
038c75b - Benjamin Lorentz, Mon Jun 5 15:24:48 2023 -0400 : update visualize-ampliseq.nf
3fb3a65 - Benjamin Lorentz, Fri Jun 2 15:12:43 2023 -0400 : update lefse.nf
c06377a - Benjamin Lorentz, Fri Jun 2 13:22:26 2023 -0400 : update 12_report.Rmd
87b2118 - Benjamin Lorentz, Fri Jun 2 12:12:13 2023 -0400 : update 12_report.md
32d7894 - Benjamin Lorentz, Fri Jun 2 11:09:49 2023 -0400 : update 12_report.md
6a015ce - Benjamin Lorentz, Thu Jun 1 15:58:50 2023 -0400 : update generate biom for graphlan \n - move vars to correct place
0ec6f74 - Benjamin Lorentz, Thu Jun 1 15:13:37 2023 -0400 : update generatebiomforgraphlan
3bc28cf - Benjamin Lorentz, Thu Jun 1 14:08:18 2023 -0400 : update generatebiomgraphlan and visualize-ampliseq
0e163d7 - Benjamin Lorentz, Tue May 30 16:08:08 2023 -0400 : remove row names from contam script
e8817bc - Benjamin Lorentz, Tue May 30 14:28:06 2023 -0400 : update contam_script
26f6349 - Benjamin Lorentz, Tue May 30 14:12:14 2023 -0400 : update modules.conf
cbe576d - Benjamin Lorentz, Tue May 30 10:45:11 2023 -0400 : update filternegativecontrol
:...skipping...
1176707 - Benjamin Lorentz, Tue Jun 6 10:38:18 2023 -0400 : Merge branch 'srs' of github.com:lorentzben/visualize-ampliseq into srs
038c75b - Benjamin Lorentz, Mon Jun 5 15:24:48 2023 -0400 : update visualize-ampliseq.nf
3fb3a65 - Benjamin Lorentz, Fri Jun 2 15:12:43 2023 -0400 : update lefse.nf
c06377a - Benjamin Lorentz, Fri Jun 2 13:22:26 2023 -0400 : update 12_report.Rmd
87b2118 - Benjamin Lorentz, Fri Jun 2 12:12:13 2023 -0400 : update 12_report.md
32d7894 - Benjamin Lorentz, Fri Jun 2 11:09:49 2023 -0400 : update 12_report.md
6a015ce - Benjamin Lorentz, Thu Jun 1 15:58:50 2023 -0400 : update generate biom for graphlan \n - move vars to correct place      
0ec6f74 - Benjamin Lorentz, Thu Jun 1 15:13:37 2023 -0400 : update generatebiomforgraphlan
3bc28cf - Benjamin Lorentz, Thu Jun 1 14:08:18 2023 -0400 : update generatebiomgraphlan and visualize-ampliseq
0e163d7 - Benjamin Lorentz, Tue May 30 16:08:08 2023 -0400 : remove row names from contam script
e8817bc - Benjamin Lorentz, Tue May 30 14:28:06 2023 -0400 : update contam_script
26f6349 - Benjamin Lorentz, Tue May 30 14:12:14 2023 -0400 : update modules.conf
cbe576d - Benjamin Lorentz, Tue May 30 10:45:11 2023 -0400 : update filternegativecontrol
be72aec - Benjamin Lorentz, Tue May 30 10:17:59 2023 -0400 : update contam scripts
a03909c - Benjamin Lorentz, Wed May 24 13:46:51 2023 -0400 : remove links for report 01
```
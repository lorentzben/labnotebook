---
title: Third time's the charm (term paper)
author: Ben Lorentz
date: '2022-11-29'
slug: third-time-s-the-charm-term-paper
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Examine htseq-count results slurm 33056
  - do we have to use --stranded reverse; yes.
- rebuild the supplemental tables 1-5 with my results
- Run DESeq2 analysis on htseq-count table
- Visualize Ampliseq
  - examine slurm run 15474870
  
### Term Paper

#### HTSeq results

Slurm Job 33056 suceeded completely. Comparing the results the reverse stranded results look remarkably similar to the unstranded analysis. I will continue with the reverse following the results from the check-strand.py script.

#### Deseq2 

I installed deseq2 and added it to the renv.lock file and pushed this up to github so it is saved. I have set up a skeleton for the script since we have to do some column header modifications before joining and analyzing each tissue individually. ( We could also look at a multi-leveled analysis so we don't have to split the table into separate minitables )

#### STAR supplemental tables

#### Visualize Ampliseq


### Git Commits

#### Lab Notebook

```bash

```

#### Term Paper

```bash


```

#### Visualize Ampliseq

```bash


```

#### Host Microbiome Interaction

```bash

```
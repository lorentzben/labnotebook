---
title: Wrapping Up Term Paper
author: Ben Lorentz
date: '2022-12-05'
slug: wrapping-up-term-paper
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

For some reason my notes from work over the weekend were not saved, but here is a log of my git commits and I will put the slurm run from the last execution since I will probably want that. 

```bash
4865839 - Ben Lorentz, Sat Dec 3 21:01:53 2022 -0500 : misspelled iluem sleuth
3a69f2c - Ben Lorentz, Sat Dec 3 20:28:49 2022 -0500 : remove exact
4efc640 - Ben Lorentz, Sat Dec 3 20:06:23 2022 -0500 : remove supp replace with deseq
95f8875 - Ben Lorentz, Sat Dec 3 19:36:22 2022 -0500 : exact false in  case a warn gives issues
95e7681 - Ben Lorentz, Sat Dec 3 19:33:06 2022 -0500 : remove write csv for correlations
0216447 - Ben Lorentz, Sat Dec 3 19:12:25 2022 -0500 : cast to as.numeric
fec81c4 - Ben Lorentz, Sat Dec 3 18:48:53 2022 -0500 : remove extra paren
266dace - Ben Lorentz, Sat Dec 3 18:29:29 2022 -0500 : is.na needed to be two calls not one
616706d - Ben Lorentz, Sat Dec 3 18:10:24 2022 -0500 : updated to completes for all the tables
6578946 - Ben Lorentz, Sat Dec 3 17:34:34 2022 -0500 : remove the multi return and not found
9b828bd - Ben Lorentz, Sat Dec 3 17:16:17 2022 -0500 : added spearman corr
5b5aa9b - Ben Lorentz, Sat Dec 3 17:09:51 2022 -0500 : removed ceca intermediate
accd223 - Ben Lorentz, Sat Dec 3 17:07:50 2022 -0500 : using function now
d7530e7 - Ben Lorentz, Sat Dec 3 14:09:02 2022 -0500 : added in a diagnostic print and na.omit
9cb97da - Ben Lorentz, Sat Dec 3 13:49:51 2022 -0500 : test of ceca fold table
bjl34716@DESKTOP-0NR359U:/mnt/f/gene8940-term-paper$ git log --since=3.days --pretty=format:"%h - %an, %ad : %s"
4865839 - Ben Lorentz, Sat Dec 3 21:01:53 2022 -0500 : misspelled iluem sleuth
3a69f2c - Ben Lorentz, Sat Dec 3 20:28:49 2022 -0500 : remove exact
4efc640 - Ben Lorentz, Sat Dec 3 20:06:23 2022 -0500 : remove supp replace with deseq
95f8875 - Ben Lorentz, Sat Dec 3 19:36:22 2022 -0500 : exact false in  case a warn gives issues
95e7681 - Ben Lorentz, Sat Dec 3 19:33:06 2022 -0500 : remove write csv for correlations
0216447 - Ben Lorentz, Sat Dec 3 19:12:25 2022 -0500 : cast to as.numeric
fec81c4 - Ben Lorentz, Sat Dec 3 18:48:53 2022 -0500 : remove extra paren
266dace - Ben Lorentz, Sat Dec 3 18:29:29 2022 -0500 : is.na needed to be two calls not one
616706d - Ben Lorentz, Sat Dec 3 18:10:24 2022 -0500 : updated to completes for all the tables
6578946 - Ben Lorentz, Sat Dec 3 17:34:34 2022 -0500 : remove the multi return and not found
9b828bd - Ben Lorentz, Sat Dec 3 17:16:17 2022 -0500 : added spearman corr
5b5aa9b - Ben Lorentz, Sat Dec 3 17:09:51 2022 -0500 : removed ceca intermediate
accd223 - Ben Lorentz, Sat Dec 3 17:07:50 2022 -0500 : using function now
d7530e7 - Ben Lorentz, Sat Dec 3 14:09:02 2022 -0500 : added in a diagnostic print and na.omit
9cb97da - Ben Lorentz, Sat Dec 3 13:49:51 2022 -0500 : test of ceca fold table
6a5f5e2 - Ben Lorentz, Fri Dec 2 21:03:17 2022 -0500 : use the right script in slurm script
393ef86 - Ben Lorentz, Fri Dec 2 20:57:52 2022 -0500 : try to run just ceca through
```

### Todos for Today:

- Term paper
  - check if gene expression is normally distributed.
  - check the authors supp table L2FC corr with my results.
  - Write Results Section for Term Paper
- Visualize Ampliseq (STALE)
  - examine slurm run 15474870
  
### Term Paper

#### Check for Normality

#### Cross check authors sig genes with my results in kallisto and Sleuth

#### Writing Methods

#### Writing results

#### What I would expand on or improve

### Visualize Ampliseq.
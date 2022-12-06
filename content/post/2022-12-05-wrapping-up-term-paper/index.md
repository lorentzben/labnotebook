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

The data is not normally distributed so the spearmans corr is correct.

```r
data:  as.numeric(ceca$deseq_log2FoldChange)
A = 11.192, p-value < 2.2e-16

> ad.test(as.numeric(ceca$sleuth_log2FoldChange))

        Anderson-Darling normality test

data:  as.numeric(ceca$sleuth_log2FoldChange)
A = 347.36, p-value < 2.2e-16

data:  as.numeric(duo$deseq_log2FoldChange)
A = 266.24, p-value < 2.2e-16

> ad.test(as.numeric(duo$sleuth_log2FoldChange))

        Anderson-Darling normality test

data:  as.numeric(duo$sleuth_log2FoldChange)
A = 36.808, p-value < 2.2e-16

ad.test(as.numeric(ile$deseq_log2FoldChange))

        Anderson-Darling normality test

data:  as.numeric(ile$deseq_log2FoldChange)
A = 277.99, p-value < 2.2e-16

> ad.test(as.numeric(ile$sleuth_log2FoldChange))

        Anderson-Darling normality test

data:  as.numeric(ile$sleuth_log2FoldChange)
A = 134.07, p-value < 2.2e-16

ad.test(as.numeric(jeju$deseq_log2FoldChange))

        Anderson-Darling normality test

data:  as.numeric(jeju$deseq_log2FoldChange)
A = 171.04, p-value < 2.2e-16

> ad.test(as.numeric(jeju$sleuth_log2FoldChange))

        Anderson-Darling normality test

data:  as.numeric(jeju$sleuth_log2FoldChange)
A = 136.92, p-value < 2.2e-16

 ad.test(as.numeric(liver$sleuth_log2FoldChange))

        Anderson-Darling normality test

data:  as.numeric(liver$sleuth_log2FoldChange)
A = 20.121, p-value < 2.2e-16

> ad.test(as.numeric(liver$deseq_log2FoldChange))

        Anderson-Darling normality test

data:  as.numeric(liver$deseq_log2FoldChange)
A = 580.6, p-value < 2.2e-16
```

#### Cross check authors sig genes with my results in kallisto and Sleuth

I went line by line for the merging and importing of data, but it keeps getting killed on my laptop so we are migrating to the server.

slurm: 33274
revision: 5adfc4bad6894229ed7ec443391600ae6184ca44

```bash
> colname(sleuth_table) <- c("tissue","R^2","Pvalue")
Error in colname(sleuth_table) <- c("tissue", "R^2", "Pvalue") :
  could not find function "colname<-"
Execution halted
```

I need to update to colnames instead of colname

slurm:33276
revision: a9d95453735de01b197b872bc977872ce69d04e1

```bash
> print(sleuth_table)
     tissue     R^2 Pvalue
[1,] "ceca"     "0" "1"
[2,] "duodenum" "0" "1"
[3,] "ileum"    "0" "1"
[4,] "jejunum"  "0" "1"
[5,] "liver"    "0" "0.999999999999851"
```

I need to do this for deseq2, save to file and do same for the 9 script. 

slurm: 33278
revision: ad83431ab69dcb64a593e92f1dfad99241503c13

```bash
> print(sleuth_table)
     tissue     R^2 Pvalue
[1,] "ceca"     "0" "1"
[2,] "duodenum" "0" "1"
[3,] "ileum"    "0" "1"
[4,] "jejunum"  "0" "1"
[5,] "liver"    "0" "0.999999999999851"

> print(deseq_table)
     tissue     R^2 Pvalue
[1,] "ceca"     "0" "1"
[2,] "duodenum" "0" "1"
[3,] "ileum"    "0" "1"
[4,] "jejunum"  "0" "1"
[5,] "liver"    "0" "0.999999999999851"

 head ../spearman/supplemental_deseq_correlation_table.csv
"tissue","R^2","Pvalue"
"ceca","0","1"
"duodenum","0","1"
"ileum","0","1"
"jejunum","0","1"
"liver","0","0.999999999999851"

head ../spearman/supplemental_sleuth_correlation_table.csv
"tissue","R^2","Pvalue"
"ceca","0","1"
"duodenum","0","1"
"ileum","0","1"
"jejunum","0","1"
"liver","0","0.999999999999851"
```
This was successful.

#### Updating script 9 

Time to make them for each of the tissues comparing sleuth and deseq 2 (script 9). 

I made my changes and updated the script

slurm: 33283
revision: ba7437e9e580ab541f2c6f734fe995fc36ceca47

```bash
did not git pull.....
```

slurm: 33296
revision: ba7437e9e580ab541f2c6f734fe995fc36ceca47

```bash
> ceca_corr_est <- as.numeric(cor.test(as.numeric(complete_ceca_fold_table$sleuth_log2FoldChange), as.numeric(complete_ceca_fold_tabl$
Error: unexpected ')' in "ceca_corr_est <- as.numeric(cor.test(as.numeric(complete_ceca_fold_table$sleuth_log2FoldChange), as.numeric$
Execution halted

```

I had broken parens (one extra for the correlation calc)

slurm: 33304
revision: 9a8760744be5833e2e06fbfb7850fe810061d703

```bash
```

#### Confirm Metadata is formed

I re-downloaded the files and they seem the same. We can write up a little confirmation script when we get home if we are still feeling unsure. We might not do this. 

#### Writing Methods

I need to go through each script and document what files go in and which files are output with a dir listing, I think I covered most of this when I put the input and output in the scripts but we must work this into the paper too. I also need to make sure to state the parameters that differed from the default

#### Writing results

how many genes were in authors, how many were in sleuth, how many were in deseq2?

confirm one last time, from NCBI root, that I made the metadata correctly.

I want to make a table highlighting the number of genes and how many common genes were found and how many were lost

#### What I would expand on or improve

There is a possibility the metadata on NCBI was uploaded incorrectly. One way I could examine to see if this is the case is to run a PCA on the DEGs to see if the samples from each alleged tissue cluster together, and therefore 

### Visualize Ampliseq.

TBD

### Todos for Tomorrow:

- Term paper
  - Write Methods Section 
  - Write Results Section
  - format tables/graphics
	  - make a count table of genes from sleuth+deseq -> merged -> merged with author supps
  - write intro
- Visualize Ampliseq (STALE)
  - examine slurm run 15474870
- Host microbiome interaction
  - new paper
  
  
### Git Commits

#### Lab Notebook

```bash
672ae62 - Benjamin Lorentz, Mon Dec 5 09:10:05 2022 -0500 : initial commit for monday
f9d1929 - Benjamin Lorentz, Mon Dec 5 08:59:41 2022 -0500 : clean up dir
```

#### Term Paper

```bash
ba7437e - Benjamin Lorentz, Mon Dec 5 16:00:22 2022 -0500 : updates to script 9
ad83431 - Benjamin Lorentz, Mon Dec 5 14:53:39 2022 -0500 : finish out correlation script for supplementals
a9d9545 - Benjamin Lorentz, Mon Dec 5 14:35:22 2022 -0500 : colnames instead of colname
5adfc4b - Benjamin Lorentz, Mon Dec 5 14:28:28 2022 -0500 : add slurm script
579c002 - Benjamin Lorentz, Mon Dec 5 11:59:36 2022 -0500 : skeleton
5416976 - Benjamin Lorentz, Mon Dec 5 10:54:25 2022 -0500 : in progress
```

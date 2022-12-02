---
title: Spearman Correlation of Gene Expression
author: Ben Lorentz
date: '2022-12-02'
slug: spearman-correlation-of-gene-expression
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Term paper
  - confirm that the SRRs remain consistently linked from Kallisto on
  - generate full count tables for each tissue from Sleuth
  - generate full count tables for each tissue from DESeq2
  - link gene id's to transcript ids
  - run spearman's correlation on log2 fc based on gene ID
  - Write Results Section for Term Paper
  - Weekly update
- Visualize Ampliseq (STALE)
  - examine slurm run 15474870
  
  
### Term Paper

I posted this update to github for the week

```md
Project Update for Week 5 week of 11/28.2022

I started the week by getting HTSeq to run successfully with all the bams at once, however the table was not saved to disk by itself it had a whole logfile above which was hard to parse as a tsv or alternative. Based on these inital results I had a feeling that the data was stranded, and I spent some time trying to get guess my lt to install and run, with no success, so I found an alternative package that examines kallisto results and determines strandedness from them, see my lab notebook entry for more details

After determining that the reads are reversely stranded, I started using deseq2 to analyze the HTSeq results that used the proper parameters, (rev: 4673b5b60ad4e04e0889121a95b22f60c59d328d). I am seeing less DEGs than the authors found see lab notebook. I talked to Dr. Bergman in class, and he suggested reviewing the metadata to ensure it is properly formed, I did and it seems valid.

The next step is to get the full results table into a proper format to line up the detected genes and run a correlation on the L2FC to see if they are correlated and then authors results are different, or if there is a bug in my process.
```

#### Make all gene tables

I want to be a little more reproducible in my r-scripting, but to do that I need to update the conda file for the R environment to include renv, but I need to rebuild the conda env. 

I ended up building a docker image since we needed apt packages and I didnt want to figure that out alternatively.

I am running the DESeq2 analysis again:
slurm: 33164
revision: 7655e77377bc13428d66491686caae93480142b1

```bash
singularity run docker://lorentzb/gene8940_r:1.0  --no-save < $SUBDIR/7_deseq2_DGE.r
```

was missing the R

slurm: 33167
revision: 897160ce7c375b9f0270a89f26b9fef628b1b3c5

```bash
Error in read.table(paste0(prefix, "data/", samp), sep = "\t", row.name = 1,  :
  more columns than column names
Execution halted
```
The issue was that it was a warning message that the number of columns didnt line up with the one label offered, so I added an empty field. 

slurm: 33170
revision: 0746e0973ec8d5a8f93916fa94270fb5510544d0

```bash
In file(file, ifelse(append, "a", "w")) :
  cannot open file '/work/gene8940/bjl34716/term_paper/deseq2/high_vs_low_ceca_deseq_p_0.05.csv': No such file or $Execution halted
```

It did not have the proper dir so I added a call in the slurm script to create that dir. 

slurm: 33172
revision: 4303626234c419ee4ee2633ce170eb6cf967e08f

```bash
Error in file(file, ifelse(append, "a", "w")) :
  cannot open the connection
Calls: write.csv -> eval.parent -> eval -> eval -> <Anonymous> -> file
In addition: Warning message:
In file(file, ifelse(append, "a", "w")) :
  cannot open file '/work/gene8940/bjl34716/term_paper/deseq2/high_vs_low_ceca_deseq_p_0.05.csv': No such file or $Execution halted
```

I changed how filenames are passed in

slurm: 33176
revision: 

```bash
Error in file(file, ifelse(append, "a", "w")) :
  cannot open the connection
Calls: write.csv -> eval.parent -> eval -> eval -> <Anonymous> -> file
In addition: Warning message:
In file(file, ifelse(append, "a", "w")) :
  cannot open file '/work/gene8940/bjl34716/term_paper/deseq2/high_vs_low_ceca_deseq_p_0.05.csv': No such file or $
Execution halted
```

I am seeing if the issue was trying to save the files in the work dir.

slurm: 33180
revision: 36b588b6cc3527f623e222313b0684ce299b5211

```bash
succeded
```

I updated sleuth script 3 to use the correct outpath

slurm: 33189
revision: 4004db775623f59d36ed727e858404d135946671

```bash
Error in setwd(resultdir) : cannot change working directory
Execution halted
```

slurm: 33190
revision: 

```bash
LGTM!
```

There were no rownames on the DESeq2 data so we have to rerun it

slurm: 33192
revision: f1efa451c05a50442cc00c7de8b5677ada1310d9

```bash

```

#### Compare gene ids from sleuth and deseq2

#### Run spearman correlation on log2fold change

### Visualize Ampliseq




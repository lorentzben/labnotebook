---
title: Merge 3 gene/transcript tables
author: Ben Lorentz
date: '2022-12-03'
slug: Merge-3-Tables
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Term paper

Merging the tables all at once kept getting a memory overflow error... So I'm thinking about iterating over one of the query lists and then doing a index lookup in the ensemble tabel and then doing a cbind on that row? Will update once I'm in it. 

#### Merging Sleuth & Deseq Results to Ensemble Results

I think I was able to iteratively add rows to a fold table for definitely sleuth but maybe Deseq

slurm: 33210
revision: 9cb97da5b9684965e4a4fff5a63d737e8b9b5ad6

```bash
Error in `[<-.data.frame`(`*tmp*`, line_up_row, , value = list(ensembl_transcript_id = NA_character_,  :
  missing values are not allowed in subscripted assignments of data frames
Calls: [<- -> [<-.data.frame
In addition: There were 50 or more warnings (use warnings() to see the first 50)
Execution halted
```

I added in a diagnostic print and a na.omit in the bind

slurm: 33211
revision:  d7530e79aaa35fccded8af19b3ce013ecac5a95e

```bash
seemed like slurm 7 actually got submitted
```

I will replace N/As in the deseq p-adj to "NA" strings so that they get passed through, since we only really need the corrs from the l2fcs. 

In Sleuth Num of N/As:
- target_ids : 0
- log2FC: 4705
- lfcSE: 4705
- pvalue: 4705
- p_adj: 4705

In Deseq num of N/As:
- gene: 0
- log2FC: 1452
- lfcSE: 1452
- pvalue: 1452
- p_adj: 1452

Dim of ceca_transcipt_res: 16396     4
Dim of ceca_gene_res: 17953     4
Dim of genes_lined_up: 17954     4


#### Implementing Pearsons Corr

slurm: 33215
revision: 9b828bdaa084d46e5b348589b1ab521dcdc7e8f3

```bash
Error in return(fold_table, tissue) : 
  multi-argument returns are not permitted
Calls: combine_tables
Execution halted

```

removed the multi return

slurm: 33216
revision: 6578946a3b899edc3c5f91411c06161ab27046a2

```bash
Error in cor.test.default(ceca_fold_table$sleuth_log2FoldChange, ceca_fold_table$deseq_log2FoldChange,  $
  'y' must be a numeric vector
Calls: cor.test -> cor.test.default
Execution halted
```

Some of the sleuth rows do not have a value for deseq2

slurm: 33218
revision: 616706dcbbe8cbe6fcc8b55b5f653ec99761a27c

```bash
Error in is.na(ceca_fold_table$sleuth_log2FoldChange, ceca_fold_table$deseq_log2FoldChange) :
  2 arguments passed to 'is.na' which requires 1
Calls: [ -> [.data.frame
Execution halted

```

slurm: 33219
revision: 266dace8e002cf055d9f826215ead86bf5b34c11

```bash
Error: unexpected ')' in "complete_ceca_fold_table <- ceca_fold_table[sum(is.na(ceca_fold_table$sleuth_l$
Execution halted
```

slurm: 33220
revision: fec81c43959504ef907f0c3cc99c9bd63e14da85

```bash
Error in cor.test.default(complete_ceca_fold_table$sleuth_log2FoldChange,  : 
  'y' must be a numeric vector
Calls: cor.test -> cor.test.default
Execution halted

```

slurm: 33222
revision: 021644796fd139cf39bd67e38f7b05fbc12480d8

```bash
Warning message:
In cor.test.default(as.numeric(complete_ceca_fold_table$sleuth_log2FoldChange),  :
  Cannot compute exact p-value with ties
> write.csv(ceca_corr,paste0(outdir,"ceca_corr.csv"))
Error in as.data.frame.default(x[[i]], optional = TRUE, stringsAsFactors = stringsAsFactors) :
  cannot coerce class ‘"htest"’ to a data.frame
Calls: write.csv ... data.frame -> as.data.frame -> as.data.frame.default
Execution halted

```


slurm: 33223
revision: 95e7681a3f32166f5921cf4338e98db4af5e9dce


```bash
supp not found
```

slurm: 33224
revision: 4efc640fa90a2156c618eaa9cd9d9fc038171c4c

```bash
Error in cor.test.default(as.numeric(complete_ceca_fold_table$sleuth_log2FoldChange),  :
  object 'False' not found
Calls: cor.test -> cor.test.default
Execution halted
```

slurm: 33226
revision: 3a69f2c07bbbdc3aebbe4f9143f86bc5f5c686e4


```bash
misspelled ileum
```

slurm: 33229
revision: 486583951bed8af52b31fdd79eedbd512330b88a

```bash
sucessful!
```

### Git Commits

#### Lab Notebook

```bash

```

#### Term Paper
```bash


```
---
title: visualize ampliseq, unzip diversity matricies
author: Ben Lorentz
date: '2022-11-22'
slug: visualize-ampliseq-unzip-diversity-matricies
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Check in on Medium Richness analysis
- Run the data through DESeq after samtools(?) or alignment.
- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- Re-Run the low med high analyses
  - Run Visualize Ampliseq
    - on low med high richness samples
- re-watch the lecture for ChIP-seq
- Check in on classifier still running

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca


### Visualize Ampliseq


### Term Paper

#### HTSeq results

HTSeq finished successfully but since I did not write the table out to file, I have to manually attach the filenames to the counts. To fix this in the future I piped the data out to file and saved the bam filenames to file too.

Based on what I am seeing from bam counts to outputs, I believe the data is stranded so I am re-running htseq-counts again with the stranded flag

slurm:  32753
revision: dd319da5bdaa3f8c6cc8df47163d5caadd734e10

```bash

```


#### Star results compared to HTSeq

Bam Results From Star

```bash
SRR8265548Aligned.sortedByCoord.out.bam
7274162
SRR8265549Aligned.sortedByCoord.out.bam
9482888
SRR8265550Aligned.sortedByCoord.out.bam
7228413
SRR8265553Aligned.sortedByCoord.out.bam
7136724
SRR8265554Aligned.sortedByCoord.out.bam
9900991
SRR8265555Aligned.sortedByCoord.out.bam
20676948
SRR8265556Aligned.sortedByCoord.out.bam
15694760
SRR8265557Aligned.sortedByCoord.out.bam
8685256
SRR8265558Aligned.sortedByCoord.out.bam
11889495
SRR8265559Aligned.sortedByCoord.out.bam
6031697
SRR8265560Aligned.sortedByCoord.out.bam
5558186
SRR8265561Aligned.sortedByCoord.out.bam
11561222
SRR8265562Aligned.sortedByCoord.out.bam
10065574
SRR8265591Aligned.sortedByCoord.out.bam
13040996
SRR8265592Aligned.sortedByCoord.out.bam
4809951
SRR8265593Aligned.sortedByCoord.out.bam
7785741
SRR8265594Aligned.sortedByCoord.out.bam
8385284
SRR8265595Aligned.sortedByCoord.out.bam
9720168
SRR8265596Aligned.sortedByCoord.out.bam
9891482
SRR8265597Aligned.sortedByCoord.out.bam
9933836
SRR8265598Aligned.sortedByCoord.out.bam
9653543
SRR8265599Aligned.sortedByCoord.out.bam
8093441
SRR8265600Aligned.sortedByCoord.out.bam
8877748
SRR8265611Aligned.sortedByCoord.out.bam
6816258
SRR8265612Aligned.sortedByCoord.out.bam
9937460
SRR8265613Aligned.sortedByCoord.out.bam
12440752
SRR8265614Aligned.sortedByCoord.out.bam
9004846
SRR8265615Aligned.sortedByCoord.out.bam
11907341
SRR8265616Aligned.sortedByCoord.out.bam
6698072
SRR8265617Aligned.sortedByCoord.out.bam
3872268
SRR8265618Aligned.sortedByCoord.out.bam
6195834
SRR8265619Aligned.sortedByCoord.out.bam
9070427
SRR8265620Aligned.sortedByCoord.out.bam
18142520
SRR8265621Aligned.sortedByCoord.out.bam
5902484
SRR8265622Aligned.sortedByCoord.out.bam
10836800
SRR8265623Aligned.sortedByCoord.out.bam
16012002
SRR8265624Aligned.sortedByCoord.out.bam
7923908
SRR8265625Aligned.sortedByCoord.out.bam
15870276
SRR8265626Aligned.sortedByCoord.out.bam
9375276
SRR8265627Aligned.sortedByCoord.out.bam
5459306
SRR8265628Aligned.sortedByCoord.out.bam
7737658
SRR8265629Aligned.sortedByCoord.out.bam
11066160
SRR8265630Aligned.sortedByCoord.out.bam
7556032
SRR8265631Aligned.sortedByCoord.out.bam
7411850
SRR8265632Aligned.sortedByCoord.out.bam
10960368
SRR8265633Aligned.sortedByCoord.out.bam
14104963
SRR8265634Aligned.sortedByCoord.out.bam
17144132
SRR8265635Aligned.sortedByCoord.out.bam
11380361
SRR8265636Aligned.sortedByCoord.out.bam
9473475
SRR8265637Aligned.sortedByCoord.out.bam
5879663
SRR8265638Aligned.sortedByCoord.out.bam
6828362
SRR8265639Aligned.sortedByCoord.out.bam
11390710
SRR8265640Aligned.sortedByCoord.out.bam
16151774
SRR8265651Aligned.sortedByCoord.out.bam
8309784
SRR8265652Aligned.sortedByCoord.out.bam
9212919
SRR8265653Aligned.sortedByCoord.out.bam
10723092
SRR8265654Aligned.sortedByCoord.out.bam
9444480
SRR8265656Aligned.sortedByCoord.out.bam
7882818
SRR8265657Aligned.sortedByCoord.out.bam
9130718
SRR8265659Aligned.sortedByCoord.out.bam
8636059
SRR8265660Aligned.sortedByCoord.out.bam
12945730
```

Sum of aligned counts in HTSeq

```bash

```


### Classifier

The classifier timed out after 30 days, is there a way we can speed up the process with more cores?

### Todos for Next Week:

- Examine htseq-count results slurm 32753
  - do we have to use --stranded reverse
- Run DESeq2 analysis on htseq-count table
- Visualize Ampliseq
  - Add a method to extract the tables from the qza objects
  - pipe these tables into new method

---

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- re-watch the lecture for ChIP-seq

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca



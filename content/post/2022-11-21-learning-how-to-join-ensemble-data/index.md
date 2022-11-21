---
title: Learning How to Join Ensemble Data
author: Ben Lorentz
date: '2022-11-21'
slug: learning-how-to-join-ensemble-data
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Figure out if we can compare GALG and GALT in any meaningful way
- Check in on Medium Richness analysis
- re run HTSeq and quantify 
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

### Term paper 

#### Can we join GALG and GALT?

Is there a way to turn these into gene names? I think [this website](https://www.biotools.fr/chicken/ensembl_symbol_converter) might be helpful, there might be a cli tool to do the same thing. I found [this tool](https://rdrr.io/bioc/BUSpaRse/man/transcript2gene.html) named "BUSpaRse" which looks like it does the same thing. 

It's weird, querying Ensemble does not give us any results

I added this note to my gene 8940 repo:

```

Update for week 4 week of 11/21/2022

I am currently running HTSeq on the sorted bam results from STAR to follow the methods that the authors followed in the paper.

Parallel to this process, I am trying to join my kallisto/sleuth results to the results reported in the supplemental materials in this paper. My current issue is that in the kallisto results, I have Ensembl transcript IDs (ex. "ENSGALT00000007105.3"). However the paper has reported Ensemble gene IDs (ex. "ENSGALG00000015448") I am having issues joining transcript id's to genes. I have found biotools.fr which can turn gene IDs to gene names (ex. "ENSGALG00000004108 CCAR1") however this tool does not convert transcripts to gene names.

I have also been looking into biomaRt, however when querying with ggallus_gene_ensembl and ensemble_gene_id, I receive 0 results for gene names, and transcript ids also provide 0 hits.

I would be open to input into how to make these gene and transcript IDs equivalent (hopefully without having to manually search each ID's and joining by hand)

```

#### STAR results

Did the first sample go through star this time?

Number of raw reads:

```bash
$ ls *_1* | wc -l
63

$ ls *_1*

SRR8265548_1.fastq.gz  SRR8265591_1.fastq.gz  SRR8265614_1.fastq.gz  SRR8265627_1.fastq.gz  SRR8265640_1.fastq.gz
SRR8265549_1.fastq.gz  SRR8265592_1.fastq.gz  SRR8265615_1.fastq.gz  SRR8265628_1.fastq.gz  SRR8265651_1.fastq.gz
SRR8265550_1.fastq.gz  SRR8265593_1.fastq.gz  SRR8265616_1.fastq.gz  SRR8265629_1.fastq.gz  SRR8265652_1.fastq.gz
SRR8265553_1.fastq.gz  SRR8265594_1.fastq.gz  SRR8265617_1.fastq.gz  SRR8265630_1.fastq.gz  SRR8265653_1.fastq.gz
SRR8265554_1.fastq.gz  SRR8265595_1.fastq.gz  SRR8265618_1.fastq.gz  SRR8265631_1.fastq.gz  SRR8265654_1.fastq.gz
SRR8265555_1.fastq.gz  SRR8265596_1.fastq.gz  SRR8265619_1.fastq.gz  SRR8265632_1.fastq.gz  SRR8265655_1.fastq.gz
SRR8265556_1.fastq.gz  SRR8265597_1.fastq.gz  SRR8265620_1.fastq.gz  SRR8265633_1.fastq.gz  SRR8265656_1.fastq.gz
SRR8265557_1.fastq.gz  SRR8265598_1.fastq.gz  SRR8265621_1.fastq.gz  SRR8265634_1.fastq.gz  SRR8265657_1.fastq.gz
SRR8265558_1.fastq.gz  SRR8265599_1.fastq.gz  SRR8265622_1.fastq.gz  SRR8265635_1.fastq.gz  SRR8265658_1.fastq.gz
SRR8265559_1.fastq.gz  SRR8265600_1.fastq.gz  SRR8265623_1.fastq.gz  SRR8265636_1.fastq.gz  SRR8265659_1.fastq.gz
SRR8265560_1.fastq.gz  SRR8265611_1.fastq.gz  SRR8265624_1.fastq.gz  SRR8265637_1.fastq.gz  SRR8265660_1.fastq.gz
SRR8265561_1.fastq.gz  SRR8265612_1.fastq.gz  SRR8265625_1.fastq.gz  SRR8265638_1.fastq.gz
SRR8265562_1.fastq.gz  SRR8265613_1.fastq.gz  SRR8265626_1.fastq.gz  SRR8265639_1.fastq.gz
```

Number of bam files: 

```bash
$ ls bam_files/*.final.out | wc -l
63

$ ls bam_files/*Aligned.sortedByCoord.out.bam

bam_files/SRR8265548Aligned.sortedByCoord.out.bam  bam_files/SRR8265620Aligned.sortedByCoord.out.bam
bam_files/SRR8265549Aligned.sortedByCoord.out.bam  bam_files/SRR8265621Aligned.sortedByCoord.out.bam
bam_files/SRR8265550Aligned.sortedByCoord.out.bam  bam_files/SRR8265622Aligned.sortedByCoord.out.bam
bam_files/SRR8265553Aligned.sortedByCoord.out.bam  bam_files/SRR8265623Aligned.sortedByCoord.out.bam
bam_files/SRR8265554Aligned.sortedByCoord.out.bam  bam_files/SRR8265624Aligned.sortedByCoord.out.bam
bam_files/SRR8265555Aligned.sortedByCoord.out.bam  bam_files/SRR8265625Aligned.sortedByCoord.out.bam
bam_files/SRR8265556Aligned.sortedByCoord.out.bam  bam_files/SRR8265626Aligned.sortedByCoord.out.bam
bam_files/SRR8265557Aligned.sortedByCoord.out.bam  bam_files/SRR8265627Aligned.sortedByCoord.out.bam
bam_files/SRR8265558Aligned.sortedByCoord.out.bam  bam_files/SRR8265628Aligned.sortedByCoord.out.bam
bam_files/SRR8265559Aligned.sortedByCoord.out.bam  bam_files/SRR8265629Aligned.sortedByCoord.out.bam
bam_files/SRR8265560Aligned.sortedByCoord.out.bam  bam_files/SRR8265630Aligned.sortedByCoord.out.bam
bam_files/SRR8265561Aligned.sortedByCoord.out.bam  bam_files/SRR8265631Aligned.sortedByCoord.out.bam
bam_files/SRR8265562Aligned.sortedByCoord.out.bam  bam_files/SRR8265632Aligned.sortedByCoord.out.bam
bam_files/SRR8265591Aligned.sortedByCoord.out.bam  bam_files/SRR8265633Aligned.sortedByCoord.out.bam
bam_files/SRR8265592Aligned.sortedByCoord.out.bam  bam_files/SRR8265634Aligned.sortedByCoord.out.bam
bam_files/SRR8265593Aligned.sortedByCoord.out.bam  bam_files/SRR8265635Aligned.sortedByCoord.out.bam
bam_files/SRR8265594Aligned.sortedByCoord.out.bam  bam_files/SRR8265636Aligned.sortedByCoord.out.bam
bam_files/SRR8265595Aligned.sortedByCoord.out.bam  bam_files/SRR8265637Aligned.sortedByCoord.out.bam
bam_files/SRR8265596Aligned.sortedByCoord.out.bam  bam_files/SRR8265638Aligned.sortedByCoord.out.bam
bam_files/SRR8265597Aligned.sortedByCoord.out.bam  bam_files/SRR8265639Aligned.sortedByCoord.out.bam
bam_files/SRR8265598Aligned.sortedByCoord.out.bam  bam_files/SRR8265640Aligned.sortedByCoord.out.bam
bam_files/SRR8265599Aligned.sortedByCoord.out.bam  bam_files/SRR8265651Aligned.sortedByCoord.out.bam
bam_files/SRR8265600Aligned.sortedByCoord.out.bam  bam_files/SRR8265652Aligned.sortedByCoord.out.bam
bam_files/SRR8265611Aligned.sortedByCoord.out.bam  bam_files/SRR8265653Aligned.sortedByCoord.out.bam
bam_files/SRR8265612Aligned.sortedByCoord.out.bam  bam_files/SRR8265654Aligned.sortedByCoord.out.bam
bam_files/SRR8265613Aligned.sortedByCoord.out.bam  bam_files/SRR8265655Aligned.sortedByCoord.out.bam
bam_files/SRR8265614Aligned.sortedByCoord.out.bam  bam_files/SRR8265656Aligned.sortedByCoord.out.bam
bam_files/SRR8265615Aligned.sortedByCoord.out.bam  bam_files/SRR8265657Aligned.sortedByCoord.out.bam
bam_files/SRR8265616Aligned.sortedByCoord.out.bam  bam_files/SRR8265658Aligned.sortedByCoord.out.bam
bam_files/SRR8265617Aligned.sortedByCoord.out.bam  bam_files/SRR8265659Aligned.sortedByCoord.out.bam
bam_files/SRR8265618Aligned.sortedByCoord.out.bam  bam_files/SRR8265660Aligned.sortedByCoord.out.bam
bam_files/SRR8265619Aligned.sortedByCoord.out.bam
```

Based on this I am comfortable running HTSeq I submitted the script to 
slurm: 32728
revision: 2464f13c2d19d1978eadd1846aeef9d93a59ce02

```bash

```


### Visualize Ampliseq

#### Check in Medium Richness Analysis 

### Host Microbiome Analysis




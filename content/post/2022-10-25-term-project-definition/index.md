---
title: Term Project Definition
author: Ben Lorentz
date: '2022-10-25'
slug: term-project-definition
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---


### Todos for Today:
- Meet Dr. Bergman and talk about paper/data *Done*
- Generate metadata/mapping file for chosen data set
- Run multiqc on chosen dataset *Doing*
- What are we talking about with Shailes tomorrow
- lecture for Thursday. 
- continue reading jones
- send regmi the paper *Done*
- Look into classes for the Spring semester
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running


### Run Multi-QC 

I submitted slurm job 31797 with revision 76979fde3bf3d5fdc3cf9ce8202eb53ef1a05a46 to run multiqc on the directory of raw data. The next step will be to map the reads to the metadata to extract the rna seq data. 

We needed to include the fastqc analysis before multiqc. I updated the script and submitted job 31798 with revision  01d911204d964a68dfabf48fa36750d4272edfd2. We need to tell fastqc the name of the files, which we did and submitted job 31799 with revision 489435eca3c1f3461137b0d09ae4db99b35be750. 

I wanted to also only run Multi-QC on the RNA-seq data as opposed to all of the reads together. To re-download and perform this analysis I submitted slurm job 31820 with revision 6e562f8cf2008eb4c90f75b8cc0e450e62ea094a.


### Meeting with Dr. Bergman

I want to start with the RNA-seq data from [this paper](https://www.nature.com/articles/s41522-019-0096-3#Sec2) to confirm their findings with updated tools. 

Just RNA seq is good, there are like 6 tissues. 2 tissues with 2 treatments. Mileage is in the analysis design. Keep the comparisons simple. Compare intra tissue high vs low. It feels good to feel validated in my choices for my analysis. 

### Making Metadata for Term paper analysis

- the separate data locations is frustrating. I needed to download the ["summary"](https://github.com/lorentzben/gene8940-term-paper/blob/main/bioproj_metadata.csv) and ["runinfo"](https://github.com/lorentzben/gene8940-term-paper/blob/main/SraRunInfo.csv) sheets from the bioproject site. We need to join the tables by the columns (Sample Accession,sample). We'll write a script to build it but also save the metadata file to the repo. There was some by-hand modification we needed to do, so the final formatted metadata is stored in the metadata dir. 
I also found the reference genome I think they used for the analysis which we'll need for the analysis. The annotations for this genome looks like [this](http://ftp.ensembl.org/pub/release-84/gff3/gallus_gallus/) I think. Is there a better reason to use NCBI refseq genome or keep with ensembl, and the genome version doesn't match so is that an issue?

### Class notes

We are talking about RNA seq today. Sounds like we are getting to the end of new material. Why use IGV when we can look at data through CLI. Next homework due Thursday. Slides for RNA Seq demo on Sleuth. New Video for Thursday. Next week class is optional, but need update log each week with new material. 

If you have a good reference genome and its a good one, transcript discover will be better. You don't need as much coverage as opposed to a Denovo to make sure you're getting all the splice forms. 

Sleuth and DESeq2 are very similar methods. Normalization, is needed to be able to compare DE. TMP is more stable across samples. RLE relative log expression. If you have good quality reference genome with annotation of transcripts. 

### Meeting with Shailes

Shailes wants to do the three-class comparison. Which will yield the intercept, the challenge and then challenge + BMD. I believe I have notes as to how to make that work, I think the hardest part will be making the model matrix and then obviously the interpretation. I helped Shailes set up an analysis with 3 factors (control, challenge, challenge+BMD). He wanted to be able to compare challenge and challenge+BMD so I suggested flipping control and challenge+BMD and using the treatment+BMD as the intercept/baseline and then see if the same significant pathways come out then you can compare the two challenges. I asked him to let me know the results of the flip/flop.


### Todos for Tomorrow:

- lecture for Thursday. 
- continue reading jones
- Look into classes for the Spring semester
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running
- Collect reference genome and annotations. 
- Shaile's compare flip/flop

### Github Commits

#### Lab Notebook

```bash
08c27f2 - Benjamin Lorentz, Tue Oct 25 11:44:06 2022 -0400 : more notes on metadata generation
da66a0e - Benjamin Lorentz, Tue Oct 25 08:49:18 2022 -0400 : added post for tuesday
```

#### gene8940-term-paper

```bash
0b512be - Benjamin Lorentz, Tue Oct 25 14:28:03 2022 -0400 : updated readme
ed836c5 - Benjamin Lorentz, Tue Oct 25 11:53:00 2022 -0400 : update readme
6e562f8 - Benjamin Lorentz, Tue Oct 25 11:38:42 2022 -0400 : modify script 0 for correct path
55fbbc3 - Benjamin Lorentz, Tue Oct 25 11:28:16 2022 -0400 : modify accession list to only include RNA-seq data
108229a - Benjamin Lorentz, Tue Oct 25 11:27:40 2022 -0400 : add complete metadata file
ba1c2ee - Benjamin Lorentz, Tue Oct 25 10:42:46 2022 -0400 : directory mods
d403d80 - Benjamin Lorentz, Tue Oct 25 10:37:24 2022 -0400 : need to include the run info
489435e - Benjamin Lorentz, Tue Oct 25 08:47:24 2022 -0400 : Need to tell fastqc the name of the files
01d9112 - Benjamin Lorentz, Tue Oct 25 08:44:32 2022 -0400 : Needed to include fastqc analysis
76979fd - Benjamin Joseph Lorentz, Tue Oct 25 08:35:20 2022 -0400 : dos2unix
d6c06e4 - Benjamin Lorentz, Tue Oct 25 08:34:57 2022 -0400 : added script to run multiqc
```
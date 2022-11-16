---
title: Term Paper Analysis & Examination of Author's Methods
author: Ben Lorentz
date: '2022-11-15'
slug: term-paper-analysis-examination-of-author-s-methods
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- talk to Casey in person about analysis and how to write the words part about a flub
- Run the data through DESeq after samtools(?) or alignment..
- Update Visualize ampliseq to use the correct channel
- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- Re-Run the low med high analyses
  - Run Visualize Ampliseq
    - on low med high richness samples
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

First order of today is to collect Sleuth results from the teaching cluster, then do a quick analysis of the members identified and how they are related to the results the author found (from supp tables 6-10). Then follow the analysis from class using Hisat2. Then seeing if we can emmulate their results. We should also make sure we are taking some good notes. 

Then we need to update the visualize ampliseq pipeline to include the correct channels. 

### Term Paper 

I have collected the supplementary tables 6-10 from the original analysis. I have also collected my results that parallels the authors analysis using Kallisto and Sleuth. I think I want to spend the time to start the HISAT2 and DESeq2 analysis and then try to join the gene lists to see who is left on each side. This way I can talk to Dr. Bergman about who is missing and the methods of analysis. 

I am a little confused as the methods for DEG in the old way, we use HISat2 to align and get sam -> bam files, but then how does hiseq2 know... we just feed the samfile and then the GTF file with the annotations.

I want to build a [Kallisto specific index](https://github.com/pachterlab/kallisto-transcriptome-indices) to see if that provides different results.

We need to collect the GFF and genome files from ensemble

We need to pivot twice, 1. We need to build a kallisto specific index using the CDNA and then re-run the kallisto/sleuth methods
  I want to run kallisto initally and then with the Wald test
  
I have downloaded the correct cDNA and have started the kallisto analysis with the slurm job number of 32574
it successfully finished, I am going to run sleuth now slurm job 32577.

```bash
Execution halted
```
There was still no significant results from the origial kallisto run. 

2. We need to setup star to make the alignment, HTSeq and then DESeq2, we just need to find out if we need to concat the chromosomes or use the top-level file.

I submitted the script to run star including making an index slurm job number 32575

```bash
        STAR --runThreadN 8 --runMode genomeGenerate --genomeDir /home/bjl34716/gene8940-term-paper/data/galgal4 --genomeFasta$        STAR version: 2.7.10b   compiled: 2022-11-01T09:53:26-04:00 :/home/dobin/data/STAR/STARcode/STAR.master/source
Nov 15 15:37:21 ..... started STAR run
Nov 15 15:37:21 ... starting to generate Genome files
Nov 15 15:37:49 ..... processing annotations GTF
!!!!! WARNING: --genomeSAindexNbases 14 is too large for the genome size=1046932099, which may cause seg-fault at the mapping $Nov 15 15:38:10 ... starting to sort Suffix Array. This may take a long time...
Nov 15 15:38:30 ... sorting Suffix Array chunks and saving them to disk...
Nov 15 15:48:40 ... loading chunks from disk, packing SA...
Nov 15 15:49:23 ... finished generating suffix array
Nov 15 15:49:23 ... generating Suffix Array index
Nov 15 15:51:51 ... completed Suffix Array index
Nov 15 15:51:52 ..... inserting junctions into the genome indices
Nov 15 15:53:43 ... writing Genome to disk ...
Nov 15 15:54:28 ... writing Suffix Array to disk ...
Nov 15 15:55:44 ... writing SAindex to disk
Nov 15 15:56:00 ..... finished successfully

EXITING because of fatal PARAMETER error: --outSAMtype SAM can cannot be combined with SortedByCoordinate or any other options
SOLUTION: re-run STAR with with '--outSAMtype SAM' only, or with --outSAMtype BAM Unsorted|SortedByCoordinate

Nov 15 15:56:01 ...... FATAL ERROR, exiting
```

fixed the sam to bams job number 32576

```bash
 
```

I think we will have to determine if the data was stranded or unstranded by using [Guess my lt](https://github.com/NBISweden/GUESSmyLT) since [htseq](https://htseq.readthedocs.io/en/master/htseqcount.html) calls for a stranded or unstranded parameter (the other option is to just run the data through and see if half of my results get thrown away, but I think it would be better to do it correctly)


### Todos for Tomorrow:

- Run the kallisto wt on updated kallisto results
- Run the data through DESeq after samtools(?) or alignment..
- Update Visualize ampliseq to use the correct channel
- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- Re-Run the low med high analyses
  - Run Visualize Ampliseq
    - on low med high richness samples
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

### Git Commits

#### Lab Notebook

```bash
977c2db - Benjamin Lorentz, Tue Nov 15 11:39:31 2022 -0500 : added notes before lunch
bc8ed22 - Benjamin Lorentz, Tue Nov 15 08:51:35 2022 -0500 : added post for tuesday
```

#### Gene 8940 Term Paper

```bash
487c1fd - Benjamin Lorentz, Tue Nov 15 16:25:26 2022 -0500 : added notes to 5 run htseq
54d7c9d - Benjamin Joseph Lorentz, Tue Nov 15 16:12:55 2022 -0500 : added htseq file
43f21c7 - Benjamin Lorentz, Tue Nov 15 16:00:51 2022 -0500 : change bash header
db4d430 - Benjamin Lorentz, Tue Nov 15 16:00:23 2022 -0500 : bam files not sam
33525f7 - Benjamin Lorentz, Tue Nov 15 15:59:30 2022 -0500 : modify script to generate BAM sorted by coordiante
1d1be85 - Benjamin Lorentz, Tue Nov 15 15:36:38 2022 -0500 : rename 4 and update it to use star
5def118 - Benjamin Lorentz, Tue Nov 15 15:24:15 2022 -0500 : update the collection script
5d5df4b - Benjamin Joseph Lorentz, Tue Nov 15 15:18:47 2022 -0500 : added star yaml file
4c16a18 - Benjamin Lorentz, Tue Nov 15 15:16:43 2022 -0500 : added a sleuth script to generate files from original sleuth analysis
44cb386 - Benjamin Lorentz, Tue Nov 15 15:12:39 2022 -0500 : remove the hisat file
0719288 - Benjamin Lorentz, Tue Nov 15 15:09:51 2022 -0500 : use the correct (84) releases for all data
82b15d3 - Benjamin Lorentz, Tue Nov 15 14:03:45 2022 -0500 : remove the for loop which is not needed
90b26ca - Benjamin Lorentz, Tue Nov 15 14:02:51 2022 -0500 : fixed the script to not use the chromosome files
7a38418 - Benjamin Lorentz, Tue Nov 15 13:35:10 2022 -0500 : whole separate variable
4ea7eec - Benjamin Lorentz, Tue Nov 15 13:32:25 2022 -0500 : remove braces
cc79527 - Benjamin Lorentz, Tue Nov 15 13:30:19 2022 -0500 : connect the gff3 to the stub
d31ff50 - Benjamin Lorentz, Tue Nov 15 13:27:03 2022 -0500 : move the stub to the end
fc8b739 - Benjamin Lorentz, Tue Nov 15 13:24:24 2022 -0500 : move the filename to the curl command
2675873 - Benjamin Lorentz, Tue Nov 15 13:20:55 2022 -0500 : added commands to download the reference genome
e665e24 - Benjamin Lorentz, Tue Nov 15 11:38:14 2022 -0500 : added first hisat command
9da5c9c - Benjamin Joseph Lorentz, Tue Nov 15 10:48:52 2022 -0500 : added hisat yaml
4aba9ba - Benjamin Lorentz, Tue Nov 15 09:44:36 2022 -0500 : added supplemental tables
989eca5 - Benjamin Lorentz, Tue Nov 15 09:25:26 2022 -0500 : incorrectly named ileum out
```

### Visualize Ampliseq

I removed the nextflow cache on the server and added the channel for the COREMETRIC distances to go into report 10 since I don't think that nf-core/ampliseq includes that.

I will confirm this by slurm run 15376557
nextflow run reverent_wing
revision 9636db01247bfdbb9777794d2e1270b18933ad64 

```bash


```

To check if it truly finishes correctly I should remove "/work/sealab/bjl34716/ampliseq-benchmarking/low_richness/" and then run it again since the cache should just copy everything over really easily. 

The task "NFCORE_AMPLISEQ:AMPLISEQ:QIIME2_ANCOM:QIIME2_ANCOM_ASV" has been running for 30 minutes, but previously it ran in 6 minutes, the queue is very full right now so I will let it run overnight and check in tomorrow. 
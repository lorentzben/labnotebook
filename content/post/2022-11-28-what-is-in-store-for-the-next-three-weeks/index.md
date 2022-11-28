---
title: What is in store for the next three weeks?
author: Ben Lorentz
date: '2022-11-28'
slug: what-is-in-store-for-the-next-three-weeks
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Examine htseq-count results slurm 32753
  - do we have to use --stranded reverse
- rebuild the supplemental tables 1-5 with my results
- Run DESeq2 analysis on htseq-count table
- Visualize Ampliseq
  - examine slurm run 15474870
  

### Todos for the next 3 weeks

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


### Term Paper

#### HTSeq Results

My stranded run of HTSeq finished, the first 10 samples were:

```bash
__no_feature	 837,913 	 1,438,667 	 820,673 	 596,775 	 804,096 	 1,617,511 	 1,242,342 	 1,018,854 	 981,628 	 445,457 
__ambiguous	 53,450 	 48,773 	 46,669 	 50,376 	 87,731 	 203,050 	 177,131 	 196,491 	 111,786 	 129,193 
__too_low_aQual	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   
__not_aligned	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   
__alignment_not_unique	 89,387 	 85,359 	 88,898 	 53,845 	 64,953 	 169,247 	 126,048 	 105,992 	 123,139 	 59,342 
										
features identified	 2,502,453 	 3,045,008 	 2,510,114 	 2,779,690 	 3,889,834 	 8,069,813 	 6,098,785 	 2,797,380 	 4,531,590 	 2,209,577 

__no_feature	 3,323,458 	 4,451,168 	 3,318,584 	 3,372,089 	 4,695,139 	 9,650,167 	 7,293,153 	 3,658,924 	 5,504,214 	 2,638,871 
__ambiguous	 673 	 867 	 607 	 633 	 2,619 	 4,612 	 2,625 	 5,197 	 1,691 	 1,277 
__too_low_aQual	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   
__not_aligned	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   
__alignment_not_unique	 89,387 	 85,359 	 88,898 	 53,845 	 64,953 	 169,247 	 126,048 	 105,992 	 123,139 	 59,342 
										
features identified	 69,685 	 80,413 	 58,265 	 54,119 	 83,903 	 235,595 	 222,480 	 348,604 	 119,099 	 144,079 
```

I think the last thing I want to do is to run stranded reversed and confirm. A third option is:

```bash
Important: For paired-end reads, although position-sorted BAM files are supported, unsorted BAM files (i.e. in which the two reads of the pair are in consecutive lines of the BAM file) are highly recommended for htseq-count. If you are having trouble or unexpected results, sort your BAM file by name and try again.

Most of my RNA-Seq reads are counted as ``__no_feature``. What could have gone wrong?
Common causes include: - The --stranded option was set wrongly. Use a genome browser (e.g., IGV) to check. - The GTF file uses coordinates from another reference assembly as the SAM file. - The chromosome names differ between GTF and SAM file (e.g., chr1 in one file and jsut 1 in the other).
```

There is another stranded package called [RSeQC](https://github.com/MonashBioinformaticsPlatform/RSeQC#quick-start), I am going to try to collect this and install on the teach cluster.

![IGV Image](https://lorentznotebook.netlify.app/2022-11-28-what-is-in-store-for-the-next-three-weeks/IGV_SRR8265630.png)

#### STAR Results and Supps 1-5

#### DESeq 2 Analysis


### Visualize Ampliseq

### Host Microbiome Interaction

I read Bergen 2009 and ingested it into the repo, it is more related to pigs and humans. I read more of the jones paper. 


### Git Commits

#### Gene 8940 Term Paper

```bash

```

#### Host Microbiome Interaction

```bash

```

#### Visualize Ampliseq

```bash

```


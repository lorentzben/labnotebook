---
title: Shailes DESeq2 analysis
author: 'Ben Lorentz'
date: '2022-11-11'
slug: shailes-deseq2-analysis
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- write weely update for Gene 8940
- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segement
    - they may have done some of this heavy lifting for us.
- continue reading jones
- Run Visualize Ampliseq
  - on low med high richness samples
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- rebuild docker image to include deseq2 
- Try to run DESeq2’s GLM/LRT on shaile’s design

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

Priories, today I want to rebuild the shailes picrust docker container and implement the DESeq2 differential expression methods. Then while that's building I want to update my github issue for the week (I should look at my notes from this site to see if there is any good information to include). Then I want to examine the Stork documents that I have received this week. 

### Making Shailes' Docker container 2.0.0

I also [made a github repo](https://github.com/lorentzben/my_dockerfiles/) for my dockerfiles so they are under some kind of version control. 

I am making a new [vanilla 4.2.2 dockerfile](https://github.com/lorentzben/my_dockerfiles/blob/main/r_4.2.2_vanilla/Dockerfile) and waiting for it to build. The image is located [here](https://hub.docker.com/repository/docker/lorentzb/r_vanilla). 

There was a collision when trying to install pasilla in R v4.2.2 so I am downgrading it to r_vanilla:4.2.0 and trying to re-generate the renv.lock file again by hand but we may have to try this at home on the mac. 


### Term Paper Update

I made a [comment for this weeks update](https://github.com/lorentzben/GENE8940/issues/6) outlining how much progress I have completed and linking to those files. It includes some notes like I sent in the post from yesterday. 

### Visualize Ampliseq

Apparently we exceeded the disk quota for the work filesystem? I don't think this is true since it is 500gbs, but I am investigating. Right now I am working on how to pair the visualize ampliseq run to the ampliseq run. 

revision: 1f39bad70bed17a198443807f9809c16ab7fce58
nextflow run: goofy_wilson
slurm: 15316335

Issues were that metadata was not being copied, this was fixed with a filename correction. 

revision: 8ad64777ea327a3fd93239a6c19b0c849a52fd57
nextflow run:
slurm: 15316370

The issue this time was the param metadata path was incorrect. 

revision:a41c11691afeadb8f9fd6ac0272dfd97e6ed8b1c
nextflow run: agitated_lalande
slurm: 15316383

```bash
Command error:
  
  
  processing file: 10_report.Rmd
  Quitting from lines 39-55 (10_report.Rmd) 
  Error in file(file, "rt") : cannot open the connection
  Calls: <Anonymous> ... withVisible -> eval -> eval -> read.csv -> read.table -> file
  In addition: Warning messages:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: In file(file, "rt") :
    cannot open file 'results/qiime2/diversity/beta_diversity/weighted_unifrac_distance_matrix-condition/raw_data.tsv': No such file or directory
  Execution halted
  
  
  processing file: 10_report.Rmd
  Quitting from lines 39-55 (10_report.Rmd) 
  Error in file(file, "rt") : cannot open the connection
  Calls: <Anonymous> ... withVisible -> eval -> eval -> read.csv -> read.table -> file
  In addition: Warning messages:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: In file(file, "rt") :
    cannot open file 'results/qiime2/diversity/beta_diversity/weighted_unifrac_distance_matrix-condition/raw_data.tsv': No such file or directory
  Execution halted

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/28/e9e70014dd9555693b511dc37fcb5a
```

It looks like ampliseq didn't generate the diversity boxplots, it just skipped over them ...
So now I'm going to have to re-run the analysis:

revision: a41c11691afeadb8f9fd6ac0272dfd97e6ed8b1c
slurm: 15317815
nextflow: shrivelled_murdock

We might have to use the core metric channel to get the diversity matrices for report 10.

### Todos for Next Week:

- Check what Casey said in slack (if the uncorrected p-vals and FC had the same number of hits)
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

- rebuild docker image to include deseq2 
- Try to run DESeq2’s GLM/LRT on shaile’s design

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca


### Git Commits

#### Lab Notebook

```bash
0337848 - Benjamin Lorentz, Fri Nov 11 09:47:18 2022 -0500 : added notes from term paper comment and dockerfile update
52c8fb4 - Benjamin Lorentz, Fri Nov 11 08:52:10 2022 -0500 : added post for friday
1d811de - Benjamin Lorentz, Thu Nov 10 17:05:06 2022 -0500 : final notes for thursday
```

#### Shailes Picrust2

```bash
c4b21a5 - Benjamin Lorentz, Fri Nov 11 16:25:50 2022 -0500 : comment out pasilla
56e79cf - Benjamin Lorentz, Thu Nov 10 16:58:40 2022 -0500 : new note,need to update docker to include deseq2
```

#### Docker

```bash
c770d7d - Benjamin Lorentz, Fri Nov 11 09:37:26 2022 -0500 : update 4.2.2 to correct base image
e6bb073 - Benjamin Lorentz, Fri Nov 11 09:06:20 2022 -0500 : init commit
```

#### Ampliseq-Benchmarking

```bash
a41c116 - Benjamin Lorentz, Fri Nov 11 11:55:03 2022 -0500 : needed to fix params
8ad6477 - Benjamin Lorentz, Fri Nov 11 11:52:19 2022 -0500 : the lines after params were not being included, and need tsv
1f39bad - Benjamin Lorentz, Fri Nov 11 11:49:34 2022 -0500 : add exact paths and checks to see if files been copied
e3be76c - Benjamin Lorentz, Fri Nov 11 11:44:12 2022 -0500 : don't try to copy to the workdir (quota issue)
c9661d5 - Benjamin Lorentz, Fri Nov 11 11:39:17 2022 -0500 : add with tower to monitor
1abd686 - Benjamin Lorentz, Fri Nov 11 11:37:14 2022 -0500 : added yaml and visuals
```
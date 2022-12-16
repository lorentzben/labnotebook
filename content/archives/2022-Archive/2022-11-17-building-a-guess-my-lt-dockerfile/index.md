---
title: Building a Guess my lt dockerfile
author: Ben Lorentz
date: '2022-11-17'
slug: building-a-guess-my-lt-dockerfile
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Run the data through DESeq after samtools(?) or alignment..
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

#### Low richness 

Is still running 22 hours later 

#### Medium richness

Ampliseq finished but cp did not complete:

```bash
cp: cannot create regular file ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/med_richness/.’: No such file or directory

Specified params file does not exists: /home/bjl34716/nf_dev/ampliseq-benchmarking/med_rich/med_rich_viz_params.yaml
```

I fixed the path which was due to a verbose and a shortened name based on if you were in /work or /scratch and added the yaml for parameters for the visualize ampliseq.

I resubmitted this job to slurm 15402092
and revision: bdda4a29e60e076a1121acc03e40484ba89ab1cf
I didn't catch the resume in time so it is repeating the analysis. 

```bash
cp: cannot create regular file ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/.’:  No such file or directory
```

I set up the script to just copy the files and then stop maybe we can then have it call another slurm script. 

slurm job: 15405881
rev: 614f711d091933a0644437547513b119a03c0bfd
```bash
cp: cannot create regular file ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/.’: No such file or directory
```

I needed to check if the result dir was copied not if the parent exists...

slurm 15411844
rev b79b98d7ad57d9d3ca328cf69c380d0ffefb60ed

```bash
succeeded
```
### Term Paper

#### Docker Image Construction

I want to start with python:3.9.15 as my base docker image, if that doesn't have underlying linux to install the other packages then I may have to pivot to another ubuntu image. 

I have an image that includes all the dependencies except for samtools. 

Samtools is being a real pain, so I may see about just building a conda env in the docker too.

I don't think I am able to get this dockerfile to build. We can come back to this later but for right now I think it would be better to just run the HTSeq with the unstranded analysis and see if we end up throwing away half the data. 

I have spent a whole day trying to figure this out and now we need to pivot. I am leaving the analysis run on my computer overnight but I still think I want to continue. 

#### HTSeq run

I submitted the first edition of the script to slurm job 32642 with revision cefb0ed75b1993f018a0169cadfbdd58dd125bb2

```bash
100000 GFF lines processed.
200000 GFF lines processed.
300000 GFF lines processed.
400000 GFF lines processed.
445496 GFF lines processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
```

I updated the script to tell the program that the files are sorted by position or coordinates. 

slurm job: 32644
revision: 1d4b5bdc79653d784073882ec2092dfc09b3d29d
```bash
100000 GFF lines processed.
200000 GFF lines processed.
300000 GFF lines processed.
400000 GFF lines processed.
445496 GFF lines processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
0 SAM alignments  processed.
```

It says that the program would understand if the files are sam or bam files but it still is looking for sams so I will explicitly tell it. 

slurm: 32645
rev: 2464f13c2d19d1978eadd1846aeef9d93a59ce02

```bash

```
Script has been running for 18 minutes so I will check in on it tomorrow.

### Host Microbe Interaction

Ingest 3 papers from last night, (likely into this site as opposed to host microbe)


### Todos for Tomorrow:

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

### Git Commits 

#### Lab Notebook

```bash
f8a0390 - Benjamin Lorentz, Thu Nov 17 09:36:47 2022 -0500 : page for thursday
38d044f - Ben Lorentz, Wed Nov 16 20:30:39 2022 -0500 : added note about medium richness
62686ab - Benjamin Lorentz, Wed Nov 16 16:42:18 2022 -0500 : move some questions to big qs
7d85603 - Benjamin Lorentz, Wed Nov 16 16:40:04 2022 -0500 : updated the git logfile
e227cf9 - Benjamin Lorentz, Wed Nov 16 16:37:53 2022 -0500 : update cheatsheet and page for wednesday
```

#### Term Paper

```bash
cefb0ed - Benjamin Lorentz, Thu Nov 17 16:24:05 2022 -0500 : fix filename for gtf file in 5
1079cb9 - Benjamin Lorentz, Thu Nov 17 16:19:05 2022 -0500 : remove dockerfile, we will use their version
4d69929 - Benjamin Lorentz, Thu Nov 17 13:55:52 2022 -0500 : does not build yet, samtools issue
7d4de9c - Benjamin Lorentz, Thu Nov 17 12:07:42 2022 -0500 : trinity is installed too
64923de - Benjamin Lorentz, Thu Nov 17 11:48:47 2022 -0500 : bowtie2 is included
4822433 - Benjamin Lorentz, Thu Nov 17 11:18:00 2022 -0500 : image now includes BUSCO
c6ee760 - Benjamin Lorentz, Thu Nov 17 11:13:17 2022 -0500 : added half a dockerfile for guess my lt
```

#### Ampliseq-benchmark

```bash
614f711 - Benjamin Lorentz, Thu Nov 17 13:25:55 2022 -0500 : stop at copying all the files
bdda4a2 - Benjamin Lorentz, Thu Nov 17 09:34:22 2022 -0500 : forgot to add the -resume
0c15c72 - Benjamin Lorentz, Thu Nov 17 09:31:37 2022 -0500 : add params for visualize ampliseq and fix paths in slurm
06c5605 - Ben Lorentz, Wed Nov 16 20:27:14 2022 -0500 : add visualize amplise to medium and skip ancom
```
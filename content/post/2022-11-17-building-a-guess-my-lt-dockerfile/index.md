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

```
### Term Paper

build a docker image from scratch for GuessMyLt

### Host Microbe Interaction

Ingest 3 papers from last night, (likely into this site as opposed to host microbe)
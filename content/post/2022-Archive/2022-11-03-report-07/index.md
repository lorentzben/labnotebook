---
title: Report 07
author: Ben Lorentz
date: '2022-11-03'
slug: report-07
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- continue reading jones
- Visualize Ampliseq
  - check png files for PCoA
  - Build chunk 07
  - add example params and slurm for ampliseq into ampliseq-vis repos
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Try to run DESeq2’s GLM/LRT on shaile’s design
- Learn a little more about GLM in R

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters

Today I want to get some good momentum with visualize ampliseq. I know that I will slow down when class time comes, especially since I must finish my project proposal today during class. If there is overflow time too then I can also start my analysis of one of the tissues. I have a feeling that the analysis will be pretty straight forward to run, the long part will be making sense out of my results. I think two types of result will be good to examine. 1: Did I recover the same number/type of DEG as the original paper? 2: What trends do my DEG point to?

### Visualize Ampliseq

One current issue is that report_04_*.log is stored in the report_gen_file dir in the projectDir, I've tried to delete it in the script and tried to not generate those files but it did not work, current solution is rm -rf ~/.nextflow/assets/lorentzben/visualize-ampliseq . 

I was able to implement report 07 rarefaction charts.

I am working on implementing report 08, the first attempt failed due to OOM error but is restarting.
- Report 08 has completed successfully. 

#### Report 09

is successfully implemented. I'm not sure why 08 is timing out due to memory and why it is not caching? Okay nevermind for this run it decided to cache...

#### Report 10

Implemented, had to add the ioi as part of the filepath for reading in beta div tables. All Looks good. 


### Notes on term project

A really neat project that someone is working with has a bunch of strains of Sars-cov2 and wants to do both denovo assembly and Reference based denovo assemebly - Ryan Sweeny


### Todos for Tomorrow:

- continue reading jones
- Visualize Ampliseq
  - add example params and slurm for ampliseq into ampliseq-vis repos
  - Report chunk 11-14
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Try to run DESeq2’s GLM/LRT on shaile’s design
- Learn a little more about GLM in R

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters

### Git Commits

#### Lab Notebook

```bash
39ae21f - Benjamin Lorentz, Thu Nov 3 11:46:29 2022 -0400 : notes before lunch
c4f1db4 - Benjamin Lorentz, Thu Nov 3 08:32:52 2022 -0400 : added page for thursday
b50665c - Benjamin Lorentz, Wed Nov 2 17:01:52 2022 -0400 : final notes for friday
```

#### gene8940-term paper

```bash
ff0b6b5 - Benjamin Lorentz, Thu Nov 3 14:28:40 2022 -0400 : add metadata gen and update readme
```

#### lorentzben/visualize-ampliseq

```bash
480367a - Benjamin Lorentz, Thu Nov 3 16:42:37 2022 -0400 : added report 10
2272ff8 - Benjamin Lorentz, Thu Nov 3 16:21:13 2022 -0400 : it was added to the 09 not 08
f7bab04 - Benjamin Lorentz, Thu Nov 3 16:00:10 2022 -0400 : added process label med for 08
d90fc8f - Benjamin Lorentz, Thu Nov 3 15:17:36 2022 -0400 : fix the report 09 filename
e642f8e - Benjamin Lorentz, Thu Nov 3 15:14:08 2022 -0400 : forgot the .out
7dc31af - Benjamin Lorentz, Thu Nov 3 15:10:18 2022 -0400 : updated paths in 09 and main
019bb9d - Benjamin Lorentz, Thu Nov 3 11:23:26 2022 -0400 : update path for rooted tree in 08
01a2a39 - Benjamin Lorentz, Thu Nov 3 11:17:20 2022 -0400 : use the correct ordered ioi
af239b2 - Benjamin Lorentz, Thu Nov 3 11:09:34 2022 -0400 : use the correct metadata channel
0e3b1a8 - Benjamin Lorentz, Thu Nov 3 11:07:05 2022 -0400 : add report 08
a4642bc - Benjamin Lorentz, Thu Nov 3 10:36:40 2022 -0400 : added keep_tex false to report 04 head
e1cf7d8 - Benjamin Lorentz, Thu Nov 3 10:27:21 2022 -0400 : put quotes around the glob
7c5d672 - Benjamin Lorentz, Thu Nov 3 10:06:18 2022 -0400 : add a line to delete the 04 logfile in the projectdir
53e343d - Benjamin Lorentz, Thu Nov 3 10:04:24 2022 -0400 : need to update path in report 07
90c7770 - Benjamin Lorentz, Thu Nov 3 09:57:17 2022 -0400 : forgot a comma
f33da65 - Benjamin Lorentz, Thu Nov 3 09:52:51 2022 -0400 : needed to include the report in the input channel
35866ca - Benjamin Lorentz, Thu Nov 3 09:45:14 2022 -0400 : add output dir so that visualize-ampliseq will pull
0bebe2f - Benjamin Lorentz, Thu Nov 3 09:34:14 2022 -0400 : need to include the report file
851dbd9 - Benjamin Lorentz, Thu Nov 3 09:27:51 2022 -0400 : added report 07 logic for rarefaction
```


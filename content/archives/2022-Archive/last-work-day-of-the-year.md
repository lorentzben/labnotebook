---
title: 'Last Work Day of the Year'
date: 2022-12-16T15:36:23Z
draft: true
meta_img: "images/image.png"
tags:
  - "2022"
  - "rarefaction"
description: "Description for the page"
---

### Todos for Today:

- Visualize Ampliseq
  - run pat schlosses analysis on the non-rarefied data
    - compare my numbers to ampliseqs
  - do we need to run cutadapt?
- Host Microbiome Community
  - finish 
- Open Up Space on the Lacie drive

### Visualize Ampliseq

#### Pat Schloss' analysis

partially based on [this file](https://github.com/riffomonas/distances/commit/52a70390b74b5d3fd4dd9a214927ec1b1424d64f)

I was able to get the code implemented. Now I need to go through and comment at what each step is doing and what that looks like. 

I added my code in and pushed the analysis up to ampliseq-benchmarking

visualize ampliseq rev: a273d37af4099abad339f5e044db64a20b242ec9
ampliseq benchmark rev: 04f95957eee6c93cfd27642381e8a1e7495a582a
slurm sub: 15946978

```bash
the slurm sub was still commented out
```

visualize ampliseq rev: a273d37af4099abad339f5e044db64a20b242ec9
ampliseq benchmark rev: a5470ff9131115f09b331213bd13fe0985d73726
slurm sub: 15947429

```bash
Specified params file does not exists: /home/bjl34716/nf_dev/ampliseq-benchmarking/no_filter/rarefaction_viz_params.yaml
```

visualize ampliseq rev: a273d37af4099abad339f5e044db64a20b242ec9
ampliseq benchmark rev: abc65b579ec9a15022593cfe7745c5d2a484539c
slurm sub: 15947515

```bash
missed more no_filters
```

visualize ampliseq rev: a273d37af4099abad339f5e044db64a20b242ec9
ampliseq benchmark rev: 1673084bdc0089a21c45a9c36c123efa90db100d
slurm sub: 15947603

```bash
```

If this runs sucessfully: the next step is to add the [conditional](https://bioinformatics.stackexchange.com/questions/15739/use-conditional-in-workflow-in-nextflow-dsl2) use of the user submitted cutoff. This needs to get passed into the core metric block.

TODOs

- Check if user submitted cutoff?
- pass cutoff (user or otherwise) into the core-metric
- ensure all diversity files downstream are from the newly generated core-metric
  - search for results/diversity and change to emit etc. 
  
### Todos for Next Year:

- Visualize Ampliseq
  - Check if user submitted cutoff?
  - pass cutoff (user or otherwise) into the core-metric
  - ensure all diversity files downstream are from the newly generated core-metric
    - search for results/diversity and change to emit etc.
- Generate a Mock community M&M or other and validate pipelines
- Open Up Space on the Lacie drive

### Git Commits

#### Lab Notebook
 
```bash
771ed07 - Benjamin Lorentz, Fri Dec 16 10:54:53 2022 -0500 : add page for today
1e819b6 - Benjamin Lorentz, Fri Dec 16 10:32:34 2022 -0500 : needed to render
5ff3b9c - Benjamin Lorentz, Fri Dec 16 10:30:23 2022 -0500 : test of rmd
a8a3937 - Benjamin Lorentz, Fri Dec 16 10:22:03 2022 -0500 : removed layouts
f6ea06a - Benjamin Lorentz, Fri Dec 16 10:19:31 2022 -0500 : update archives
9eb32cf - Benjamin Lorentz, Fri Dec 16 10:16:05 2022 -0500 : this is a test blogpost
38d2c74 - Benjamin Lorentz, Fri Dec 16 10:13:13 2022 -0500 : added a test post
89d7c53 - Benjamin Lorentz, Fri Dec 16 10:06:08 2022 -0500 : add index.md for papers
a056e75 - Benjamin Lorentz, Fri Dec 16 10:04:00 2022 -0500 : add _index.md files
35e3ded - Benjamin Lorentz, Fri Dec 16 09:56:30 2022 -0500 : add archives header
b25fa18 - Benjamin Lorentz, Fri Dec 16 09:53:19 2022 -0500 : move the archive folder to just the content
483eecb - Benjamin Lorentz, Fri Dec 16 09:49:35 2022 -0500 : create 2022 archive
7b07543 - Benjamin Lorentz, Thu Dec 15 16:49:59 2022 -0500 : final notes for thursday
```

#### Visualize Ampliseq

```bash
a273d37 - Benjamin Lorentz, Fri Dec 16 15:52:38 2022 -0500 : update dockerfile for entry in bash
f788b65 - Benjamin Lorentz, Fri Dec 16 15:44:11 2022 -0500 : add rarefaction_report.rmd
374a39e - Benjamin Lorentz, Fri Dec 16 15:05:20 2022 -0500 : updated main.nf
1122049 - Benjamin Lorentz, Thu Dec 15 16:46:30 2022 -0500 : modified Dockerfile
e4f5b0e - Benjamin Lorentz, Thu Dec 15 16:42:27 2022 -0500 : add Dockerfile and renv.lock file
```

#### Ampliseq Benchmark

```bash
a5470ff - Benjamin Lorentz, Fri Dec 16 16:03:35 2022 -0500 : update slurm sub rarefaction
04f9595 - Benjamin Lorentz, Fri Dec 16 15:55:09 2022 -0500 : add files to run a new analysis with the rarefaction code
```

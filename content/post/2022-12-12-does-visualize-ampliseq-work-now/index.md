---
title: Does visualize ampliseq work now?
author: Ben Lorentz
date: '2022-12-12'
slug: does-visualize-ampliseq-work-now
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Visualize Ampliseq 
  - check if slurm 15765674 suceeded
- Host microbiome interaction
  - new paper

### Visualize Ampliseq

#### Check slurm 15765674

It looks like the processes finished sucessfully, have not examined the files myself. 
I added a copy command to save results to the work dir so its persistant

slurm:  15799366
ampliseq benchmark rev: 75dde40467090fc6a70ee502ead05e9473da59a4
visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462

```bash
needed to connect outdir and = 
```

slurm: 15799409
ampliseq benchmark rev: 5adc17db7548ed1b77fe4e74ea21eeff8442507a
visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462

```bash
cp: omitting directory ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness’
```

slurm: 15799425
ampliseq benchmark rev: ba9ed8bfeb65f292452aac075504aeb010d45535
visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462

```bash
we needed to copy over the results dir
```

Instead I'm going to use the outdir slot in parameters.

slurm: 15799470
ampliseq benchmark rev: ba9ed8bfeb65f292452aac075504aeb010d45535
visualize ampliseq rev: 720226a5983a1d5123c98d1915601404acc1788c

```bash
sucess
```

#### Try to run low richness

slurm: 15800228
ampliseq benchmark rev: e21e8783fc99cd11027f2c422cb1769ad6558970
visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462

```bash
Got hung up on ANCOM
```

slurm:
ampliseq benchmark rev: ba383fa8906c2557de7e9c9d3d2c023262960074
visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462

```bash

```


### Tasks for the next 1 week

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


### Host Microbiome Interaction

A good paper to examine is: https://www.sciencedirect.com/science/article/pii/S2001037017301162

### Git Logs

#### Lab Notebook

```bash
718627e - Benjamin Lorentz, Mon Dec 12 08:49:38 2022 -0500 : stub for monday
```

#### Ampliseq Benchmark

```bash
ba383fa - Benjamin Lorentz, Mon Dec 12 15:29:52 2022 -0500 : update low_rich_params
e21e878 - Benjamin Lorentz, Mon Dec 12 11:16:57 2022 -0500 : updated low_rich_viz_params, slurm-sub-low slurm-sub-med
720226a - Benjamin Lorentz, Mon Dec 12 10:48:11 2022 -0500 : update med_rich_params and slurm-sub
ba9ed8b - Benjamin Lorentz, Mon Dec 12 10:24:56 2022 -0500 : update slurm-sub-med.sh
5adc17d - Benjamin Lorentz, Mon Dec 12 10:20:23 2022 -0500 : update slurm-sub-med.sh
75dde40 - Benjamin Lorentz, Mon Dec 12 10:03:03 2022 -0500 : update slurm-sub-med.sh
```




---
title: Implement Report Chunk 4
author: Ben Lorentz
date: '2022-10-18'
slug: ['implement04']
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for today:

- Evaluate Report 03
- Start Report 04
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Update repo for Homework for this week
- Check in on classifier still running

- update WSL2 packages locally

```bash
apt list --upgradable
 
```

### Report 04

The former report 04 
obs shannon simpson  chao1 ace faith_pd 

When copying over reports to someplace I can see them 03 and 04 show 0kb...

here is a run to look into

```bash
[b5/a19225] process > ORDERIOI (1)                         [100%] 1 of 1 ✔
[6f/56aa40] process > REPORT01BARPLOT (1)                  [100%] 1 of 1 ✔
[cb/1204f6] process > REFORMATANDQZATAX (1)                [100%] 1 of 1 ✔
[e2/092e0a] process > GENERATEBIOMFORGRAPHLAN (1)          [100%] 1 of 1 ✔
[e1/1557c3] process > RUNGRAPHLAN (1)                      [100%] 1 of 1 ✔
[dd/fb4cf7] process > REPORT02GRAPHLANPHYLOGENETICTREE (1) [  0%] 0 of 1
[2f/1be993] process > REPORT03HEATMAP (1)                  [  0%] 0 of 1
[e5/497905] process > REPORT04ALPHATABLE (1)               [100%] 1 of 1
```

I had a mistype for mode it was mSode, the issue is still heatmaps isn't being copied over. I first want to see if the report copies over. 

Report 01 also did not include images correctly so I'm thinking of trying to knit them in now that we don't have to deal with the mounting issue, and also do this with report 02:

```bash
knitr::include_graphics("temp.png")
```

update WSL2 packages locally

```bash
apt list --upgradable
 
```

This still wasn't working. I want to go back and see how I made this work with Lefse/Graphlan images in the past.

### Notes from Class

Projects at the beginning of November, and Meetings with Dr. Bergman to discuss ideas.\
Ideas with improvement with methods and results discussion. RNA-seq might be a good idea for a re-implementation project. 

Homework 4 due next week. 

Variant Calling Format and there is Structural Variants 

30x or more coverage for diploid, 25-50x is good enough.

5x process poisson process mean == varience closer to 1x more missed locations. 

sort map and index bam file to reference file. 

SAMTools and BCFtools are focused on varient calling. 

mpileup command takes mapped read compared to reference using quality score what is the likelihood genotype is like reference alternative, or haplotype. 

VCF and BCF aren't the same binary vs human readable as sam vs bam, can save the compressed human-readable version to save data space but still access the results. 

BCFtools vs Zcat to open the mpileup format

You would want to report the call file format. 

Indel and SNP examples, this is something I've got to wrap my head around, what is QTL. 

Evolutionary genetics, medical, QTL. Next mapping to explore gene expression-> chip-seq and methylation. 

### Meeting with Shailes follow-up with ALDEx2 analysis

Where we left off:

we determined that he wants to run a comparision between each daypoint (day-0) control and challenge and then challenge and challenge and BMD

We installed the ALDEx2 package through Bioc::Manager and upgraded the R-installation to 4.2.1

Shailes made the different condition comparison vectors, now we just have to separate them into separate analysis chunks so that the visualization is a little bit easier to see. 

We have to subset the whole dataframe for each comparision but I think we have got a workable comparsion to look at each of the control/treatement or treatment/supplement conditions. 

We talked a little bit about rendering the documents using rmarkdown and then how to plot lefse-like barplots to represent significant pathways. 

He is going to run the code through and see what difference he observes and then we will re-connect to see what the next step is.

### Todos for tomorrow:

- Start Report 05
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Update repo for Homework for this week
- Check in on classifier still running
- Check in on slurm run slurm-14913334.out

- update WSL2 packages locally

### Code Commits 


#### Lab Noteboook

```bash
ae0120f - Benjamin Lorentz, Tue Oct 18 14:04:56 2022 -0400 : added notes from class related to varient calling
a4079e0 - Benjamin Lorentz, Tue Oct 18 11:54:19 2022 -0400 : pre-lunch notes
db0d882 - Benjamin Lorentz, Tue Oct 18 09:00:20 2022 -0400 : new page for Tuesday
```

#### Visualize Ampliseq

```bash
655a382 - Benjamin Lorentz, Tue Oct 18 17:22:59 2022 -0400 : remove the inclusion
41ea133 - Benjamin Lorentz, Tue Oct 18 17:19:43 2022 -0400 : add rstudio root file
9d57060 - Benjamin Lorentz, Tue Oct 18 17:18:37 2022 -0400 : add getwd before
36e289b - Benjamin Lorentz, Tue Oct 18 17:14:09 2022 -0400 : glob filenames
8017990 - Benjamin Lorentz, Tue Oct 18 17:13:13 2022 -0400 : try this
22df195 - Benjamin Lorentz, Tue Oct 18 17:11:09 2022 -0400 : list files 2
623bec2 - Benjamin Lorentz, Tue Oct 18 17:09:26 2022 -0400 : list files
0a56d26 - Benjamin Lorentz, Tue Oct 18 17:07:49 2022 -0400 : remove clean true
fa85a72 - Benjamin Lorentz, Tue Oct 18 17:03:44 2022 -0400 : cp L
9adf7f7 - Benjamin Lorentz, Tue Oct 18 17:01:12 2022 -0400 : update report 02
534ed0a - Benjamin Lorentz, Tue Oct 18 16:44:28 2022 -0400 : can we publish the images to both dirs
55eba01 - Benjamin Lorentz, Tue Oct 18 16:37:39 2022 -0400 : try this
e6045af - Benjamin Lorentz, Tue Oct 18 16:26:40 2022 -0400 : try to include photos again
6929cc5 - Benjamin Lorentz, Tue Oct 18 16:20:17 2022 -0400 : replace Figures with barplots for correct path
8030687 - Benjamin Lorentz, Tue Oct 18 16:17:19 2022 -0400 : use knitr include_graphics
793109c - Benjamin Lorentz, Tue Oct 18 11:37:32 2022 -0400 : it is mode not mSode...
54de462 - Benjamin Lorentz, Tue Oct 18 10:32:54 2022 -0400 : evenness not ace
2b4d178 - Benjamin Lorentz, Tue Oct 18 10:32:07 2022 -0400 : needed to add the results prepend to directories
030e453 - Benjamin Lorentz, Tue Oct 18 10:26:35 2022 -0400 : add report chunk 04

```

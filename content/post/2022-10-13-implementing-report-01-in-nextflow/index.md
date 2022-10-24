---
title: Implementing Report 01 in Nextflow
author: Ben Lorentz
date: '2022-10-13'
slug: ['implement01']
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todo for today:

- Watch lecture for Thursday ***Done***
- Make report 01 work through the nextflow platform. ***Done***
- Start on Report 02
- Check in on classifier still running
- Make up cheat sheet for QIIME2 and Phyloseq

Currently, I have a Rmd file that can render stacked bar plots inside the lorentzb/microbiome_analyst:1.1

Next steps:
- add script into nextflow script
- copy over metadata file 
- copy over item of interest
- Update paths in report 01
- Test full implementation 

I forgot to include the Stacked Bar Charts that collapse all samples into their IoI category so I implemented some lines to do that. 

The way to save the user submitted item of interest is:

```nextflow
file 'item_of_interest.csv'

ioi_ch = Channel.of(params.ioi)
```

The current nextflow script will copy the correct files into the work directory and generate all of the figures. The current issue is related to the knitting program not being able to find these rendered figures. This was related to knitting to PDF. I will leave this issue for the future. I also tested my code in a directory where it was only the result folder from ampliseq to make sure the nextflow pulled script has correct relative paths. 


### Git Commits

#### Lab notebook

```bash
8f03427 - Benjamin Lorentz, Thu Oct 13 14:13:25 2022 -0400 : added chunk about ioi
04e7080 - Benjamin Lorentz, Thu Oct 13 14:05:05 2022 -0400 : updates for thursday
500b1d2 - Benjamin Lorentz, Thu Oct 13 09:39:06 2022 -0400 : outline for Thursday
e8b3108 - Benjamin Lorentz, Wed Oct 12 16:57:24 2022 -0400 : added notes for wednesday
74cba49 - Benjamin Lorentz, Wed Oct 12 16:52:40 2022 -0400 : added notes for wednesday
```

#### Visualize Ampliseq

```bash
a1a3c50 - Benjamin Lorentz, Thu Oct 13 16:19:07 2022 -0400 : add check if exist
5d17a06 - Benjamin Lorentz, Thu Oct 13 16:10:18 2022 -0400 : use projectDir
3f1b007 - Benjamin Lorentz, Thu Oct 13 16:08:45 2022 -0400 : add basedir
b327f9c - Benjamin Lorentz, Thu Oct 13 15:45:24 2022 -0400 : rename figures to barplots
fac9659 - Benjamin Lorentz, Thu Oct 13 15:28:48 2022 -0400 : prevent nested figures in result directory
6e079b9 - Benjamin Lorentz, Thu Oct 13 15:19:19 2022 -0400 : */* and Figures/*
ad07e5d - Benjamin Lorentz, Thu Oct 13 15:13:21 2022 -0400 : change to path Figures
d8c0350 - Benjamin Lorentz, Thu Oct 13 15:03:08 2022 -0400 : change figures to file as opposed to path
dceb6e6 - Benjamin Lorentz, Thu Oct 13 14:50:37 2022 -0400 : do not copy over pdf file
8e2a8fe - Benjamin Lorentz, Thu Oct 13 14:44:57 2022 -0400 : include two output files
8489cea - Benjamin Lorentz, Thu Oct 13 14:37:26 2022 -0400 : try not to generate the pdf file
0ade720 - Benjamin Lorentz, Thu Oct 13 14:13:57 2022 -0400 : removed bash call
96b9885 - Benjamin Lorentz, Thu Oct 13 12:22:43 2022 -0400 : remove echo
d9ccd51 - Benjamin Lorentz, Thu Oct 13 12:15:24 2022 -0400 : try to pass a file
3fe582e - Benjamin Lorentz, Thu Oct 13 12:14:12 2022 -0400 : have to give it ioi
7f4ce5b - Benjamin Lorentz, Thu Oct 13 12:12:58 2022 -0400 : try params.ioi again
33058da - Benjamin Lorentz, Thu Oct 13 12:09:26 2022 -0400 : try to pass my item of interest
074f9eb - Benjamin Lorentz, Thu Oct 13 12:07:43 2022 -0400 : save it as a path
43896ba - Benjamin Lorentz, Thu Oct 13 12:06:47 2022 -0400 : try to save ioi as file
53082ee - Benjamin Lorentz, Thu Oct 13 12:03:36 2022 -0400 : quote params.ioi
0371074 - Benjamin Lorentz, Thu Oct 13 11:56:08 2022 -0400 : pull from params
e00e4ed - Benjamin Lorentz, Thu Oct 13 11:53:58 2022 -0400 : try with triple quotes
7ef7c9d - Benjamin Lorentz, Thu Oct 13 11:52:16 2022 -0400 : quote out the item of interest
2c7e551 - Benjamin Lorentz, Thu Oct 13 11:51:13 2022 -0400 : needed an extra slash?
465c02c - Benjamin Lorentz, Thu Oct 13 11:49:25 2022 -0400 : this wont fix the problem but will cause a new one
ee4a1e3 - Benjamin Lorentz, Thu Oct 13 11:46:04 2022 -0400 : hard code the resultdir
190a1ea - Benjamin Lorentz, Thu Oct 13 11:43:41 2022 -0400 : remove ioi ord
332dece - Benjamin Lorentz, Thu Oct 13 11:39:24 2022 -0400 : use structure similar to ampliseq
a8e20d6 - Benjamin Lorentz, Thu Oct 13 11:30:44 2022 -0400 : remove individual blocks
012c253 - Benjamin Lorentz, Thu Oct 13 11:29:12 2022 -0400 : enable docker and singularity
d23820a - Benjamin Lorentz, Thu Oct 13 11:27:06 2022 -0400 : added docker container to config
6da29aa - Benjamin Lorentz, Thu Oct 13 11:20:23 2022 -0400 : remove docker://
740c607 - Benjamin Lorentz, Thu Oct 13 11:17:20 2022 -0400 : just try to pass the dir in
6c14751 - Benjamin Lorentz, Thu Oct 13 11:16:06 2022 -0400 : order the channels
14ee84b - Benjamin Lorentz, Thu Oct 13 11:13:16 2022 -0400 : change item_of_interst
cb43d34 - Benjamin Lorentz, Thu Oct 13 11:12:32 2022 -0400 : remove 01 from 01-report
f37b51b - Benjamin Lorentz, Thu Oct 13 11:11:43 2022 -0400 : fix the report
39279bd - Benjamin Lorentz, Thu Oct 13 11:10:54 2022 -0400 : try channel of for val
551014f - Benjamin Lorentz, Thu Oct 13 11:09:14 2022 -0400 : reorder
97ce6c2 - Benjamin Lorentz, Thu Oct 13 11:08:04 2022 -0400 : remove the projectDir
13e2827 - Benjamin Lorentz, Thu Oct 13 11:07:19 2022 -0400 : put my channels outside my workflow
962bad9 - Benjamin Lorentz, Thu Oct 13 11:06:09 2022 -0400 : put the project dir into quotes
c4e4d6c - Benjamin Lorentz, Thu Oct 13 11:05:25 2022 -0400 : imply the inputs
44e6ab2 - Benjamin Lorentz, Thu Oct 13 11:03:41 2022 -0400 : add a plus to the string for one report
9c8852e - Benjamin Lorentz, Thu Oct 13 11:02:47 2022 -0400 : words
ce4d724 - Benjamin Lorentz, Thu Oct 13 11:02:10 2022 -0400 : change 01_ to 01-
fa553e3 - Benjamin Lorentz, Thu Oct 13 11:00:23 2022 -0400 : remove prepend
57611a5 - Benjamin Lorentz, Thu Oct 13 10:58:58 2022 -0400 : added first try at paths
cc8b9a6 - Benjamin Lorentz, Thu Oct 13 10:49:03 2022 -0400 : whoops rmd not html
f48f048 - Benjamin Lorentz, Thu Oct 13 10:47:31 2022 -0400 : needed to add the collapsed ioi
f8177e9 - Benjamin Lorentz, Thu Oct 13 09:48:01 2022 -0400 : remove the ordered item of interest
```

### Todo for today:

- Start on Report 02
- Check in on classifier still running
- Make up cheat sheet for QIIME2 and Phyloseq

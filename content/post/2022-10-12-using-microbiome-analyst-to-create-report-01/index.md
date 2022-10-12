---
title: Using Microbiome Analyst to Create Report 01
author: Ben Lorentz
date: '2022-10-12'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todo for today:

- Meet with Shailes at 3pm
  - Look over ALDEx2 code to make sure I can explain what we want to do based on his analysis structure. ***done***
- Build the Report 01 using microbiome analyst now that we have dockerfile ***done***
  - Add in qiime2R to dockerfile if we want to be able to read the qza files (just need to rebuild image as 1.1) ***done*** 
- Watch lecture for Thursday => tomorrow
- Make report 01 work through the nextflow platform. => tomorrow
- Start on Report 02 => tomorrow
- Check in on classifier ***still running***

### Making Report 01: 

I think the best first step is to upload my data to the webserver and make my barplots on there, since I cached the properly formatted tables. Then I can use that code to reproduce it locally and make sure that it looks good. My one last worry is that the package is intended to be used interactively will it break when tried to run through the terminal.

Filtering we must evaluate:

```bash
#Abundance filter (should have been handled by QIIME2)
#mbSet<-ApplyAbundanceFilter(mbSet, "prevalence", 4, 0.2);

#Varience filter (probably should be handled by QIIME2)
#mbSet<-ApplyVarianceFilter(mbSet, "iqr", 0.1)

# Data Normalization (maybe handled by QIIME2)
#mbSet<-PerformNormalization(mbSet, "none", "none", "none")
```

The first two are set to default values and I chose no data normalization. We can compare these parameters to see how the results differ.

I was able to use the package to generate stacked bar plots that did not need to be normalized or filtered (this is a great TODO to evaluate next). The file was able to be rendered too into an HTML file, which really just represents the png files that were made earlier.

Small Tasks:
- compare MbA web to QIIME2 analysis ***done***
- Programmify Item of Interest ***done*** 
  - Possibility of 2 level IoI (future endeavor)


### Meeting with Shailes:

I want to look over my script again to make sure it is commented up nicely. I can offer to just run the analysis for him if he wants to give me his picrust2 data. 

Questions I have:

- do you want the stratified data?
- do you want to do 1:1 or many to 1 comparisons?
- do you want to run the script or would you prefer I did and gave you the code for reproducibility? 

### Github Commits

#### Lorentz Lab Notebook

```bash
beb6ec3 - Benjamin Lorentz, Wed Oct 12 11:24:11 2022 -0400 : notes before lunch
5822422 - Benjamin Lorentz, Wed Oct 12 10:59:39 2022 -0400 : added note about the params for MbA filtering
9f10bc9 - Benjamin Lorentz, Wed Oct 12 08:46:31 2022 -0400 : added skeleton for wednesday
7931538 - Benjamin Lorentz, Tue Oct 11 16:56:25 2022 -0400 : add more headings in
c602907 - Benjamin Lorentz, Tue Oct 11 16:54:34 2022 -0400 : notes for tuesday
```

#### Visualize Ampliseq

```bash
421b687 - Benjamin Lorentz, Wed Oct 12 14:25:11 2022 -0400 : File renders as well as I think It can for right now
0da1622 - Benjamin Lorentz, Wed Oct 12 12:13:06 2022 -0400 : fix tax table and a couple other issues
99e5243 - Benjamin Lorentz, Wed Oct 12 11:23:56 2022 -0400 : added more lines to MbA script want to try run without filtering
b99788b - Benjamin Lorentz, Wed Oct 12 09:51:12 2022 -0400 : re-organize the mba filed
```

#### Shailes Picrust2

```bash
9ef28d1 - Benjamin Lorentz, Wed Oct 12 15:30:36 2022 -0400 : added simple analysis for Shailes
```

### Todo for tomorrow: 

- Watch lecture for Thursday 
- Make report 01 work through the nextflow platform. 
- Start on Report 02 
- Check in on classifier ***still running***
- Make up cheatsheet for QIIME2 and Phyloseq
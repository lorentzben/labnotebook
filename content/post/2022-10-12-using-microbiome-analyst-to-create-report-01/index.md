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
  - Look over ALDEx2 code to make sure I can explain what we want to do based on his analysis structure.
- Build the Report 01 using microbiome analyst now that we have dockerfile
  - Add in qiime2R to dockerfile if we want to be able to read the qza files (just need to rebuild image as 1.1)
- Watch lecture for Thursday
- Make report 01 work through the nextflow platform.
- Start on Report 02
- Check in on classifier

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

### Meeting with Shailes:

I want to look over my script again to make sure it is commented up nicely. I can offer to just run the analysis for him if he wants to give me his picrust2 data. 

Questions I have:

- do you want the stratified data?
- do you want to do 1:1 or many to 1 comparisons?
- do you want to run the script or would you prefer I did and gave you the code for reproducibility? 

### Github Commits

#### Lorentz Lab Notebook

```bash

```


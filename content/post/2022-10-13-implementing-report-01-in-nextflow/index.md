---
title: Implementing Report 01 in Nextflow
author: Ben Lorentz
date: '2022-10-13'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todo for today:

- Watch lecture for Thursday
- Make report 01 work through the nextflow platform.
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

The current nextflow script will copy the correct files into the work directory and generate all of the figures. The current issue is related to the knitting program not being able to find these rendered figures.


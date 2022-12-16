---
title: What is a core microbiome?
author: Ben Lorentz
date: '2022-10-21'
slug: ['coreMicrobiome']
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for today:
- Wrap Up Homework 4 ***Done***
  - Check the BCF tools intermediates
  - Run Mpileup without the quality filter
  - Write up the words part of the section
- Reply to Shailes ***Done***
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- Check in on classifier still running

I feel like I have been putting the Aggrey science review material on the side to work on the pipeline, Jackwood Shailes' works, and coursework. So I think I want to dig into it a little bit today. 

First up though is going to be finishing homework 4 so that I can make sure it is submitted and good to go. 

I also feel like I should look into how ampliseq determines depth and see if that is easy to determine or if it is a large task for next week. 

### Homework 4

I want to make sure that my filtering steps make sense. The first command is the mpileup command, I want to compare the output file with and without the -q 60 flag. This would include reads with a mapping quality lower than 60. 

So the number of lines decreased by about 60,000 features, out of 4 million features so I think that that makes sense. The filter command seems to be pretty straightforward. 

One last thing is to double check Bergman's class notes. Everything looks good from here. 

### Organize the Notes from Class

I want to make sure I have my notes packaged up and onto the NAS so that I don't lose access to them. 
Downloaded and working on uploading to the server. 

### Reply to Shailes

I want to reply to Shailes because I think we can easily run his data through. The one question/issue I have is that I still cannot articulate the significance of the intercept. I want to do ~30 min of reading before I reply so that I feel informed enough to speak on it. 

### What is a core microbiome?

A start was the paper Oakley Chicken Gastrointestinal Microbiome 2014. Though we need to parse the notes from the text now in my obsidian notebook. I want to follow up on this paper to see what has been done since 2014 (nearly 10 years of work).

Questions to explore:
- Multi-Omics Paper
- Who are the major players in chicken gut segments?
- What are they doing there?

I also skimmed the Johnson 2019 paper where they have been talking about using PacBio CCS sequencing to evaluate the whole 16s sequence as an amplicon as opposed to using smaller illumina amplicons, basically stating that using 300bp was an artifact of Illumina sequencing days and we should use the full 1,500bp since we can get high fidelity reads. They also suggested still continuing to use 99% identity OTUs as opposed to ASVs or ESVs because ASVs will inflate sample richness due to SNPs or Indels. They also suggested that using SNPs could have great implications going to strain level, essentially if we use these long reads we have a chance to do sWGS taxonomic assignment without the cost which could be amazing! Definently a good read to dig into for the future.

### Todos for Next Week:
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running


### Git Commits

#### Lab notebook

```bash
4335ccc - Benjamin Lorentz, Fri Oct 21 12:11:55 2022 -0400 : updates before lunch
0bf2380 - Benjamin Lorentz, Fri Oct 21 08:50:21 2022 -0400 : post for friday
516e7f5 - Benjamin Lorentz, Thu Oct 20 16:59:55 2022 -0400 : added notes on homework and from the AI seminar
```

#### GENE8940

```bash
b2ee36c - Ben Lorentz, Fri Oct 21 10:38:07 2022 -0400 : added output files
3e99ad5 - Ben Lorentz, Fri Oct 21 10:22:16 2022 -0400 : Update homework_4.sh
3fd092e - Ben Lorentz, Fri Oct 21 09:48:57 2022 -0400 : Update homework_4.sh
e1a2cff - Ben Lorentz, Fri Oct 21 09:35:36 2022 -0400 : Update homework_4.sh
```
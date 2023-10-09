---
title: 'Dedicate the New Building'
date: 2023-10-06T13:26:10Z
draft: false
meta_img: "images/image.png"
tags:
   - "stat 8200"
   - "regmi-rfid"
description: "Description for the page"
---

### Todos for Today

Dedicate the New Building and take group picture at 10:30am. 

- Class
  - Complete Exam 1
  
- Sweden
  - Edit Partner's Paper
  - Keni's response about UWB for Aggrey
  - Consolidate notes for class
  - read this paper: [https://pubmed.ncbi.nlm.nih.gov/31434210/](https://pubmed.ncbi.nlm.nih.gov/31434210/)
  
- Regmi
  - RFID
    - Build a daily and nightly time budget function
    - Create a plot that shows the average amount of time each bird spends in a zone
    - Statistically Compare the daytime and nighttime proportions.
    - Send to Regmi
  - Microbiome Work
    - Make script to get from raw data to QZAs
    - Compile all params I'm gonna need
    - Make a doc to import data into:
      - QIIME2
      - Phyloseq
      -biopython
  - Heat Stress
    - Re-Run the heat stress analysis to see what the results look like
    - New subset with 9-5/6pm
    - Is there a better way to analyze this type of data
      - What did Lars/Ana/the rest send?
      
- gg-catalog
  - better formatted table so that the clarity is better.
  - what ammino acids are being processed in each segment
    - valine is processed in the duodenum but not the jejunum
  - gene network of all keggs in one network for each tissue
  - go into the literature; gene catalogs for a biological process in an organism.
      - Need to compare/remove the common genes/processes 

 
- Read papers about microbiome analysis

  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation 
  
### Reply to Shailes

He was asking about non-normal data and I asked about if he examined the residual plot. Qiime will let you do a two way anova with [this function](https://docs.qiime2.org/2023.7/plugins/available/longitudinal/anova/). So that could be something to examine. 

### RFID

I need to make a function to generate the day and nights time budgets. 

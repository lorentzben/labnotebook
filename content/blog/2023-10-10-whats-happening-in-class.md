---
title: 'Whats Happening in Class'
date: 2023-10-10T14:13:13Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat 8200"
  - "regmi-rfid"
description: "Description for the page"
---

### Todos for Today

- Reply to Shailes

- Class
  - Lab 5

- Sweden
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

### RFID

We started by trying to iterate through the records in the interval table and see if the start and end dates are the same, but every single one crosses midnight. So we are going to go through each record and split it into day and night time (I think). 

I realized that I can add more information to the interval table. Namely we can keep track of what the previous zone before changing was (you could infer this from the interval table previously, but now it is spelled out clearly).

```{r}
data2$day <- (format(data2$datetime, "%H:%M") > "05:00" & format(data2$datetime, "%H:%M") < "21:59")
night <- data2[data2$day != TRUE,]
night_int <- timeToIntervals(night)

getTimeBudgetProp(night_int)

```

Do we need a new timeToIntervals that is day aware?



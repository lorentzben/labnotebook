---
title: 'Make New Rfid Docker'
date: 2023-10-05T12:54:28Z
draft: false
meta_img: "images/image.png"
tags:
   - "stat 8200"
   - "regmi-rfid"
   - "meet with regmi"
description: "Description for the page"
---

### Todos for Today

- Class
  - Complete Exam 1
  
- Sweden
  - Edit Partner's Paper
  - Keni's response about UWB for Aggrey
  - Consolidate notes for class
  - read this paper: [https://pubmed.ncbi.nlm.nih.gov/31434210/](https://pubmed.ncbi.nlm.nih.gov/31434210/)
  
- Regmi
  - RFID
    - Rebuild Docker image
    - Create a plot that shows the average amount of time each bird spends in a zone
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
  

### RFID analysis
  
  2. Rebuild Docker image
    - updated to lorentzb/rfid:1.2
    
  3. Perform a time budget analysis to see what areas the birds spend the most time on average
    - examine Keni's code and see what we can use and have to adapt
      - I believe that my adaptation is correct now
    - I want to do an overall one and then one based on each day
      - I keep getting a timeout when trying to run the analysis on all the rooms, can I separate them out and then join them later?
      - The implementation looks okay right now. 
      - Do we need to fill gaps etc?
        - No you do not need to 
      - Did Keni use the make tracks and resample function for the UWB data?
        - No they were using the PA FA paradigm, which is what I had rebuilt in the past

    Building the daily time budget function:
     1. We need to slice the tsibble into daily 
      
  4. Examine the social network structure by making an adjacency matrix
    - Define what contact means, when two birds are in the same zone for (x seconds?, or x seconds over the course of study) this could be motivated by behavior papers
    - Step through the room table at at each timepoint if two birds are in the same zone mark a one for their contact in the adjacency matrix
    - Generate a graph from the adjacency matrix
    - Do high energy birds spend time together?
    - Do low energy birds spend time together?
    - Are the time budgets for each activity level different based on the class?
  5. Move functions into resource package to clean up each room code
    
    
### Regmi Microbiome

Where did that analysis leave off?

bird_stress_rev: 14b2391227908c1f594a86f69b278a24e306e475
slurm job: 24491311

```bash
```

### Meet With Regmi 

I wanted to know what time makes sense to start a date for a day analysis. Dr. Regmi thought it was a good idea to do a time budget of separate day and night for each bird. I want to double check that for my time budget I am using the Lagging Zone so we know where the bird was previously not where it's going. Graphically, I think either a 3 line series for each bird or a three box matrix along the series makes the most sense. Does the nighttime proportion differ from the daytime proportions? This could be a difference test.

### Todos for Tomorrow

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
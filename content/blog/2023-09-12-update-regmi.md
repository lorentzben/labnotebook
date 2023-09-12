---
title: 'Update Regmi'
date: 2023-09-12T13:18:59Z
draft: false
meta_img: "images/image.png"
tags:
   - "stat 8200"
   - "regmi-rfid"
   - "bird-stress-analysis"
description: "Description for the page"
---

### Todos for Today

- Sweden
  - Consolidate notes for class
  - Home range analysis for my turkey vulture dataset
  - writeup
  - read this paper: [https://pubmed.ncbi.nlm.nih.gov/31434210/](https://pubmed.ncbi.nlm.nih.gov/31434210/)
  
- Regmi
  - RFID
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

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation  
 
### Sweden

Keni response

Expense log

### RFID analysis

- Keni from Sweden gave me some good ideas about how to approach the RFID data
  1. Clean the data by removing consecutive transitions into the same zone (possibly in a short amount of time. ) DONE
  2. Infill the sampling interval to a regular timeframe
    - make a table of difftime to get the sampling distribution DONE
    - is this 1 sec, 5 sec? what is the current average duration between reads? DONE settled on 5 sec sampling intervals
    
  3. Perform a time budget analysis to see what areas the birds spend the most time on average
    - examine Keni's code and see what we can use and have to adapt
    - I want to do an overall one and then one based on each day 
  4. Examine the social network structure by making an adjacency matrix
    - Define what contact means, when two birds are in the same zone for (x seconds?, or x seconds over the course of study) this could be motivated by behavior papers
    - Step through the room table at at each timepoint if two birds are in the same zone mark a one for their contact in the adjacency matrix
    - Generate a graph from the adjacency matrix
    - Do high energy birds spend time together?
    - Do low energy birds spend time together?
    - Are the time budgets for each activity level different based on the class? 
    
    
### Remi Microbiome

Where did that analysis leave off?

bird_stress_rev: 14b2391227908c1f594a86f69b278a24e306e475
slurm job: 24491311

```bash
```

### Todos for Tomorrow

- Sweden
  - Expense Log
  - Keni's response about UWB for Aggrey
  - Consolidate notes for class
  - Home range analysis for my turkey vulture dataset
  - writeup
  - read this paper: [https://pubmed.ncbi.nlm.nih.gov/31434210/](https://pubmed.ncbi.nlm.nih.gov/31434210/)
  
- Regmi
  - RFID
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

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation  
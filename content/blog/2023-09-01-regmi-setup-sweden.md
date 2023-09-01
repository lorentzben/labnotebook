---
title: 'Regmi Setup Sweden'
date: 2023-09-01T15:14:14Z
draft: false
meta_img: "images/image.png"
tags:
   - "stat 8200"
   - "bird-stress-analysis"
description: "Description for the page"
---

### Todos for Today

- class
  - Complete homework 1 problems
    - re-run early analysis with t-test/aov
  
- other sweden tasks
  - find a copy of Regmi Data to be able to show them
  - Make sure Space on Macbook
  - Make Sure space on essd
  
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
  
### Class

I need to finish Lab 1 and double check Homework 1
I submitted both assignments and we are good to go.

### Sweden Tasks

I cleared up some space on my interal hard drive ~ 40gb and on my work drive ~400 gbs

### Regmi

Meet with Regmi

#### RFID

Regmi wants me to re-generate the duration plots, to look at the time in each zone; I am going to go back into the code and re-make those plots with the average time. He needs the tightened up plots by 9/13 for certain. 

Can we modify the calc_zone_duration function?

get the time spent in zone for each bird for each day
then make a plot of barplots or lines with 3 series, bottom, middle, top
55 or 79 entries

Make an average one for each bird.

#### Heat Stress Turkey

When I get back from Sweden Dr. Regmi wants me to re-perform the heat stress analysis I did previously, but to shift the window of heat stress from 8-4 to 9-5/6 and repeat. 

I also want to take a copy of this data to Sweden and ask if anyone has experience in temporal analysis, the cyclic circadian type data. 

#### Microbiome Data analysis

I double checked what Dr. Regmi wants to do with the data in relation to Hari (sp?). He said that he would be interested in him learning how to process the raw data, I said regmi should look into getting him Sapelo2 access. I am going to put the analysis on the backburner a little bit to be able to focus on some other stuff until I get back. 

bird_stress_rev: f23c805d476c769befdc02c8fc0c1efb56c084aa
slurm job: 24485053

```bash
During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/opt/conda/envs/qiime2-2019.1/lib/python3.6/site-packages/q2cli/tools.py", line 146, in import_data
    view_type=input_format)
  File "/opt/conda/envs/qiime2-2019.1/lib/python3.6/site-packages/qiime2/sdk/result.py", line 203, in import_data
    type_ = qiime2.sdk.parse_type(type_)
  File "/opt/conda/envs/qiime2-2019.1/lib/python3.6/site-packages/qiime2/sdk/util.py", line 82, in parse_type
    " may be needed to define it." % name)
qiime2.sdk.util.UnknownTypeError: Name 'SingleLanePerSamplePairedEndFastqDirFmt' is not a defined QIIME type, a plugin $

An unexpected error has occurred:

  Name 'SingleLanePerSamplePairedEndFastqDirFmt' is not a defined QIIME type, a plugin may be needed to define it.

See above for debug info.
```

bird_stress_rev: 14b2391227908c1f594a86f69b278a24e306e475
slurm job: 24491311

```bash
```
### Todos for Next Week

- class
  - Watch Lectures:
    - Wed
    - Fri
  
- other sweden tasks
  - Coursework while I'm There
  
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
  
  
### Git Commits

#### Lab Notebook

```bash
e6ae2f4 - Benjamin Lorentz, Fri Sep 1 15:07:21 2023 -0400 : add notes after lunch
e73cd60 - Benjamin Lorentz, Fri Sep 1 11:15:44 2023 -0400 : add page for Friday
4ac5033 - Benjamin Lorentz, Thu Aug 31 16:55:00 2023 -0400 : final notes for Thursday
```

#### 2021-bird-stress

```bash
14b2391 - Benjamin Lorentz, Fri Sep 1 15:23:25 2023 -0400 : Update code/01_import_seqs_to_qza.sh
```
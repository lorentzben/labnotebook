---
title: 'Update Regmi Code'
date: 2023-08-17T13:23:44Z
draft: false
meta_img: "images/image.png"
tags:
  - "rfid-tracking"
  - "gg-catalog"
  - "stat 8200"
description: "Description for the page"
---

### Todos for Today


- find stockholm hotels
- other sweden tasks
  - github etc
  
- gg-catalog
  - better formatted table so that the clarity is better.
  - what ammino acids are being processed in each segment
    - valine is processed in the duodenum but not the jejunum
  - gene network of all keggs in one network for each tissue
  - go into the literature; gene catalogs for a biological process in an organism.
      - Need to compare/remove the common genes/processes 
      
- RFID
  - Send Regmi the bird IDs by activity level
  - make a duration table for each bird and how long they spend in low medium and high zones; average each bird across the low med high 
  - combine global transition plots series onto one chart. 
 
- Possibly help Regmi with picrust from previously analyzed projects. 
 
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation

### RFID

Send Regmi the bird IDs by activity level

- Wierdly my all rooms table does not include room 3, so I am re-running the table build to see if there is an issue with that?

make a duration table for each bird and how long they spend in low medium and high zones; average each bird across the low med high 

combine global transition plots series onto one chart. 

Room 3 was commented out of the code....
So now we need to check the cutoffs for the whole room analysis

update lines 978-989 and then check the output table.

why is room 3 not included?

number of ids:
  room 2: 37
  room 3: 31
  room 8: 34
  room 11: 36
  
after each for loop
  room 2: 37
  room 3: 68
  room 8: 102
  room 11: 137
  
IDs selected: 
 

### gg-catalog

Cancel Hotels.
Figure out new plan.

### Todos for Today


- find stockholm hotels
- other sweden tasks
  - github etc
  
- gg-catalog
  - better formatted table so that the clarity is better.
  - what ammino acids are being processed in each segment
    - valine is processed in the duodenum but not the jejunum
  - gene network of all keggs in one network for each tissue
  - go into the literature; gene catalogs for a biological process in an organism.
      - Need to compare/remove the common genes/processes 
      
- RFID
  - Send Regmi the bird IDs by activity 
    - Update the values at line 1007 then send to him
  - make a duration table for each bird and how long they spend in low medium and high zones; average each bird across the low med high 
  - combine global transition plots series onto one chart. 
 
- Possibly help Regmi with picrust from previously analyzed projects. 
 
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation

### Git Commits

#### Lab Notebook

```bash
156eca4 - Benjamin Lorentz, Thu Aug 17 11:46:12 2023 -0400 : updates before lunch
77fb81f - Benjamin Lorentz, Thu Aug 17 09:33:37 2023 -0400 : add page for thursday
```

#### RFID 

```bash
c7683c2 - Benjamin Lorentz, Thu Aug 17 11:38:48 2023 -0400 : update concat all the data set 2
```

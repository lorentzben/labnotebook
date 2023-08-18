---
title: 'Rfid Class Day 2'
date: 2023-08-18T13:54:08Z
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
  
### Stockholm Hotels

### RFID

I want to build a function that will take a XTS object:
  Start at the first datapoint and log the zone and time
  have the second datapoint in a marker
  Log how much time is between the two in the zone

We may have done this in calc_trans_period_duration but I'm not certain so lets compare.

calc_zone_duration(reslist_room_2[[4]]$name, reslist_room_2[[4]]$ID, reslist_room_2[[4]]$xts_obj)
3644

I was able to generate the tables that calculate the duration that each bird spends in a zone

### Todos for Next Week

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
  - combine global transition plots series onto one chart. 
 
- Possibly help Regmi with picrust from previously analyzed projects. 
 
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes
  - Possibly meet Shailes on Monday
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
  

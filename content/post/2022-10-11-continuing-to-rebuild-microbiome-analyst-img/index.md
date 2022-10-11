---
title: Continuing to rebuild microbiome analyst img
author: Ben Lorentz
date: '2022-10-11'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Todos for today:

- reply to Shailes to set up a time to meet ***Meeting tomorrow at 3pm***
- Watch lectures for #14 for class ***Done and class attended***
- Check in on the classifier (though it outran 96hrs so it may take longer) ***(still running)***
- Continue trying to build the microbiome analyst image ***Done***
  - install github version of tax4fun ***Done***
  

For today we were able to build a docker image that contains MicrobiomeAnalystR package and all of its dependencies. The Dockerfile and renv.lock files are both tracked on git to be able to re-generate these files later. Image is at lorentzb/microbiome_analyst:1.0 

Issues I encountered along the way: First there were dependencies from github that had to be collected and then these were not tracked correctly through renv.lock so I had to include their installation in the dockerfiler dockerfile. Sometimes the only way to determine these were missing was by trying to build the dockerfiles and then install the needed library. 

I also cleaned up my homework for class which included evaluating assembly stats from Quast and images from Mummer. By updating the scrip to copy these files to the outdir and comment to github issues. 

Todo for tomorrow:

- Meet with Shailes at 3pm
  - Look over ALDEx2 code to make sure I can explain what we want to do based on his analysis structure. 
- Build the Report 01 using microbiome analyst now that we have dockerfile
  - Add in qiime2R to dockerfile if we want to be able to read the qza files (just need to rebuild image as 1.1)
- Watch lecture for Thursday
- Make report 01 work through the nextflow platform.
- Start on Report 02
- Check in on classifier
  
Git Commits 

#### Lorentz Lab Notebook

```bash
e734c20 - Benjamin Lorentz, Tue Oct 11 09:00:53 2022 -0400 : added post for today
d96dce5 - Benjamin Lorentz, Mon Oct 10 17:27:00 2022 -0400 : final notes for monday
```

#### Visualize Ampliseq

```bash
6f7337d - Benjamin Lorentz, Tue Oct 11 16:39:46 2022 -0400 : added 01_MbA which now imports the data and will make stacked bar chart plotting much faster
6f2bba7 - Benjamin Lorentz, Tue Oct 11 14:44:04 2022 -0400 : added dockerfile and lockfile
```


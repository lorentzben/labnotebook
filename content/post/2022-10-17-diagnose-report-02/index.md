---
title: Diagnose Report 02
author: Ben Lorentz
date: '2022-10-17'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for today:

- Mandatory Cybersecurity Training ***Done***
- Watch lectures for Tuesday's Class ***Done***
- Complete on Report 02 ***Done***
  - compare docker vs singularity ***Done***
  - push microbiome_analyst:1.1 ***Done***
  - mess with file permissions/symlinks ***Done***
- Start Report 03
- Check in on classifier still running
- Make up cheat sheet for QIIME2 and Phyloseq


### Lecture for today

Today's lecture briefly covered variant calling mainly focusing on SNP/indel calling. Dr. Bergman also identified some structural variant calling as a hot and less refined field right now which could be really interesting to look into. Though I'm still not 100% certain what that would look like, but maybe Dr. Aggrey has some more insight into. 
He also pointed out BCFtools and IGV which can export its session to file so that we can reproduce the figures again which is very important for future reproducibility. 

### Run Report 02 with Singularity Profile

My current issue with report 02 is: 

```bash
File phy_trees/NC_image_graph.png not found in resource path
Error: pandoc document conversion failed with error 99

/mnt/c/Users/bjl34716/Documents/my_utils/visualize-ampliseq/work/51/7fbcf40fc1fc1552a127ca823a298c
```

I am going to try to run the pipeline with singularity as opposed to docker to see if the issue with symlinks or dir permissions is needed.

If this doesn't work we'll make a note in report 02 of where to find the PNGs so we can move on. 

```bash
Command exit status:
  2

Command output:
  (empty)

Command error:
  /bin/bash: line 0: cd: /mnt/c/Users/bjl34716/Documents/my_utils/visualize-ampliseq/work/e9/e19388d108a2341747c27ae90aaac0: No such file or directory
  python3: can't open file '.command.sh: [Errno 2] No such file or directory

Work dir:
  /mnt/c/Users/bjl34716/Documents/my_utils/visualize-ampliseq/work/e9/e19388d108a2341747c27ae90aaac0
```

I'm not sure if its my bash header that means that the script cannot find python3.
The issue is actually that singularity cannot mount the c or f drives to the WSL2 system so it gets confused and upset. I reverted back to docker and wrote a note for the graphlan images. I think this solution is okay for now.

*Report 02 works now*

### Generating report 03

The heatmap needed an ordered item of interest, so I am giving it a go at generating it. I keep running into filer symlink permissions which I feel like is WSL2's fault. So what I'm gonna change is trying to run the pipeline on the server to see if it is actual or just my local system.

The server started lagging in a uncomfortable manner so I want to try copying the cec_raw_nf dir into my home folder in WSL2 and see if we dont have to rely on mounting if that makes a difference?

By working on the local linux filesystem it seems like it is able to generate the ordered item of interest. It looks like report 03 is generated. I have to look inside to see if it still looks good. New dir is under "~/my_utils"

### Todos for tomorrow:

- Evaluate Report 03
- Start Report 04
- Look into genomic type project for class (see project description)
- Update repo for Homework for this week
- Check in on classifier still running

### Git Commits

#### Lab Notebook

```bash
6d348b0 - Benjamin Lorentz, Mon Oct 17 12:10:48 2022 -0400 : updated notebook for monday to lunch
58d2459 - Benjamin Lorentz, Mon Oct 17 08:34:15 2022 -0400 : todos for today
58baec7 - Benjamin Lorentz, Mon Oct 17 08:32:48 2022 -0400 : beginning of Monday Notes
```

#### Visualize Ampliseq

```bash
7a58fd7 - Benjamin Lorentz, Mon Oct 17 17:02:34 2022 -0400 : need to copy the pdf version not html
b2bb444 - Benjamin Lorentz, Mon Oct 17 16:52:03 2022 -0400 : update stats for analysis summary
0625ed3 - Benjamin Lorentz, Mon Oct 17 16:43:15 2022 -0400 : update publishdir for report 03
2539bc1 - Benjamin Lorentz, Mon Oct 17 16:30:46 2022 -0400 : and i chose the wrong type of channel
36becc8 - Benjamin Lorentz, Mon Oct 17 16:29:53 2022 -0400 : do not check if it exists
91cd65e - Benjamin Lorentz, Mon Oct 17 16:29:00 2022 -0400 : change file to path
0bfa7c4 - Benjamin Lorentz, Mon Oct 17 16:17:31 2022 -0400 : it doesnt matter to check if it exists or not
0820732 - Benjamin Lorentz, Mon Oct 17 16:07:41 2022 -0400 : add cachedir in the scratch
3e62b66 - Benjamin Lorentz, Mon Oct 17 16:05:53 2022 -0400 : update 03 report
93545a7 - Benjamin Lorentz, Mon Oct 17 16:03:06 2022 -0400 : updated iois to sort
c3d2ea6 - Benjamin Lorentz, Mon Oct 17 15:42:04 2022 -0400 : parameterize metadata
0543528 - Benjamin Lorentz, Mon Oct 17 15:39:06 2022 -0400 : we forgot about our quotes
60a1b64 - Benjamin Lorentz, Mon Oct 17 15:37:36 2022 -0400 : it would pass with an empy ord ioi
e70dd9e - Benjamin Lorentz, Mon Oct 17 15:33:26 2022 -0400 : remove the variable
95c571d - Benjamin Lorentz, Mon Oct 17 15:32:35 2022 -0400 : added ordered item of interest
3c9fff6 - Benjamin Lorentz, Mon Oct 17 14:35:59 2022 -0400 : need ioi
a28744b - Benjamin Lorentz, Mon Oct 17 14:34:49 2022 -0400 : needed to pass report 03 in
c8d0182 - Benjamin Lorentz, Mon Oct 17 14:31:04 2022 -0400 : update report 03 and add new process
9f6846c - Benjamin Lorentz, Mon Oct 17 12:08:13 2022 -0400 : didnt need the tree output
a6882fe - Benjamin Lorentz, Mon Oct 17 12:06:08 2022 -0400 : change read csv to read lines
35d46a5 - Benjamin Lorentz, Mon Oct 17 12:03:51 2022 -0400 : dont try to save files in the document, point to where they are located
ab03b40 - Benjamin Lorentz, Mon Oct 17 11:53:03 2022 -0400 :  use /usr/bin/env bash again
2c0d64b - Benjamin Lorentz, Mon Oct 17 11:49:49 2022 -0400 : Revert "use cp with the dereferecne"
d1b6d39 - Benjamin Lorentz, Mon Oct 17 11:41:27 2022 -0400 : change shebangs to not be usr/bin/env to just bin/bash or python
```


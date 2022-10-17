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

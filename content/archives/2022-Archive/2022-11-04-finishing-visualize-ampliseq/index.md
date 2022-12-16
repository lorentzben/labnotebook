---
title: Finishing Visualize Ampliseq
author: Ben Lorentz
date: '2022-11-04'
slug: finishing-visualize-ampliseq
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- continue reading jones
- Visualize Ampliseq
  - add example params and slurm for ampliseq into ampliseq-vis repos
  - Report chunk 11-14
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Try to run DESeq2’s GLM/LRT on shaile’s design
- Learn a little more about GLM in R

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters


Today's Goal is to finish the Report generator for Visualize Ampliseq. One of the largest issues I see is incorporating Lefse since we may need to generate some other intermediate files but we will only know for certain once we get into it! If we finish that early, then we can either peek into the 3 runs (low, med, high richness)[low priority], read some papers that we have saved in Zotero, or Spend some time on section three tasks (database, genome assembly, etc.)

### Report 11

Implemented sucessfully with no issues

### Report 12

Implemented without issues

### Report 13

Lefse is implemented, working on including images in report file. 

Need to look at lefse logs d6/dea90c only one out of the 3 were actually generated. 

this may be something we have to fix.
```bash

cp: cannot create regular file '/opt/conda/bin/run_': Read-only file system
cp: cannot create regular file '/opt/conda/bin/run_': Read-only file system

```

the whole log:

```bash
cp: cannot create regular file '/opt/conda/bin/run_': Read-only file system
cp: cannot create regular file '/opt/conda/bin/run_': Read-only file system

Number of significantly discriminative features: 8 ( 8 ) before internal wilcoxon
Number of discriminative features with abs LDA score > 2.0 : 2
clade_sep parameter too large, lowered to 0.266967773438
clade_sep parameter too large, lowered to 0.266967773438

Number of significantly discriminative features: 12 ( 12 ) before internal wilcoxon
Number of discriminative features with abs LDA score > 2.0 : 0
No differentially abundant features found in lefse_result.res
No differentially abundant features found in lefse_result.res
clade_sep parameter too large, lowered to 0.266967773438
clade_sep parameter too large, lowered to 0.266967773438

Number of significantly discriminative features: 0 ( 0 ) before internal wilcoxon
No features with significant differences between the two classes
Number of discriminative features with abs LDA score > 2.0 : 0
No differentially abundant features found in lefse_result.res
No differentially abundant features found in lefse_result.res
clade_sep parameter too large, lowered to 0.266967773438
clade_sep parameter too large, lowered to 0.266967773438

Number of significantly discriminative features: 4 ( 7 ) before internal wilcoxon
Number of discriminative features with abs LDA score > 2.0 : 0
No differentially abundant features found in lefse_result.res
No differentially abundant features found in lefse_result.res
clade_sep parameter too large, lowered to 0.266967773438
clade_sep parameter too large, lowered to 0.266967773438
```
Lefse is Running correctly, just not many differential features...


### Report 14 

Done and dusted!

### Check to make sure pipeline runs locally

TODO want to check if 13 works on local docker.

Visualize ampliseq seems to work now! We just need to merge it back to master and tag it for nextflow.

after this: read some papers that we have saved in Zotero, or Spend some time on section three tasks (database, genome assembly, etc.)


### Tilocca 2019

This paper has some really interesting notes on how to do a system's biology approach to a question about a element in a living system. The thesis is focused on phosphorus in chickens and pigs and how does this differ. One element of note is that they give a very very nice overview of the different types of -OMICS approaches. It makes me want to go back and look at notes from 6550 the only issue is that I didn't download the course presentations (won't make that mistake again). Some of the proteomics stuff is a little confusing right now, how do you link your reference genomes to your protein database list? (do you literally get a gene list translate it and then query those proteins from a master database and then query your peaks against that one?) I remember having to query peaks against a database for chemical structures for chemical compounds. I don't remember but I think there might have been a forier transform to compare complex samples, I do forsee complex mixtures being a frustrating point. This is something I will have to continue to examine. I want to emmulate this background section for my work. I finished chapter 1, next is chapter 2.

### Todos for Next week:

- continue reading Tillocca
- continue reading jones
- Visualize Ampliseq
  - add example params and slurm for ampliseq into ampliseq-vis repos
- Run Visualize Ampliseq
  - on low med high richness samples
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Try to run DESeq2’s GLM/LRT on shaile’s design
- Learn a little more about GLM in R

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters

### Git Commits

#### Lab Notebook

```bash
ae70442 - Benjamin Lorentz, Fri Nov 4 12:18:07 2022 -0400 : added notes about generating report file
e8d5cf3 - Benjamin Lorentz, Fri Nov 4 08:37:16 2022 -0400 : inital page for Friday
c794bf2 - Benjamin Lorentz, Thu Nov 3 16:54:53 2022 -0400 : last notes for thursday
```

#### Visualize Ampliseq

```bash
51e400b - Benjamin Lorentz, Fri Nov 4 14:47:43 2022 -0400 : gotta use the local version of 13
c94fbae - Benjamin Lorentz, Fri Nov 4 13:45:37 2022 -0400 : remove process medium so it can be run locally
11413a7 - Benjamin Lorentz, Fri Nov 4 12:14:02 2022 -0400 : add report 14
d663de1 - Benjamin Lorentz, Fri Nov 4 12:04:59 2022 -0400 : remove the images channel
00f661a - Benjamin Lorentz, Fri Nov 4 12:03:03 2022 -0400 : added gitignore and local report 13
1e347bd - Benjamin Lorentz, Fri Nov 4 11:50:43 2022 -0400 : trying to edit 13_report to match 02_report
c92398d - Benjamin Lorentz, Fri Nov 4 11:45:54 2022 -0400 : remove the pdf call
34bf564 - Benjamin Lorentz, Fri Nov 4 11:44:01 2022 -0400 : added 13 local and added the stub back in
aa46935 - Benjamin Lorentz, Fri Nov 4 11:38:44 2022 -0400 : images get copied into work dir so we dont need the prepend
7d8baa9 - Benjamin Lorentz, Fri Nov 4 11:36:36 2022 -0400 : include the images in the output
bd26302 - Benjamin Lorentz, Fri Nov 4 11:33:39 2022 -0400 : must add in the item of interes
fcfabc6 - Benjamin Lorentz, Fri Nov 4 11:30:35 2022 -0400 : added report 13 gen files and changed lefse result dir to av
oid confusion
46dac39 - Benjamin Lorentz, Fri Nov 4 11:10:08 2022 -0400 : add lefse analysis process
c0b5883 - Benjamin Lorentz, Fri Nov 4 10:53:37 2022 -0400 : remove process report 13
189d475 - Benjamin Lorentz, Fri Nov 4 10:52:26 2022 -0400 : added lefse format process
88dfab5 - Benjamin Lorentz, Fri Nov 4 10:29:38 2022 -0400 : rename permanova to anosim
fe24259 - Benjamin Lorentz, Fri Nov 4 10:08:30 2022 -0400 : needed to add an extra path for distances
50b38fc - Benjamin Lorentz, Fri Nov 4 10:07:22 2022 -0400 : need to pass the jaccard distance matrix
6130151 - Benjamin Lorentz, Fri Nov 4 09:52:33 2022 -0400 : the report file was not pushed
432ce92 - Benjamin Lorentz, Fri Nov 4 09:50:03 2022 -0400 : added report 12 chunk
7bfed33 - Benjamin Lorentz, Fri Nov 4 09:41:37 2022 -0400 : fix rooted tree path
b952eb9 - Benjamin Lorentz, Fri Nov 4 09:39:16 2022 -0400 : got the container wrong
e08e81a - Benjamin Lorentz, Fri Nov 4 09:37:19 2022 -0400 : added report 11 to main and updated paths
480367a - Benjamin Lorentz, Thu Nov 3 16:42:37 2022 -0400 : added report 10

```




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

after this: read some papers that we have saved in Zotero, or Spend some time on section three tasks (database, genome assembly, etc.)


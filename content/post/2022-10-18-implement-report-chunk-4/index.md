---
title: Implement Report Chunk 4
author: Ben Lorentz
date: '2022-10-18'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for today:

- Evaluate Report 03
- Start Report 04
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Update repo for Homework for this week
- Check in on classifier still running

- update WSL2 packages locally

```bash
apt list --upgradable
 
```

### Report 04

The former report 04 
obs shannon simpson  chao1 ace faith_pd 

When copying over reports to someplace I can see them 03 and 04 show 0kb...

here is a run to look into

```bash
[b5/a19225] process > ORDERIOI (1)                         [100%] 1 of 1 ✔
[6f/56aa40] process > REPORT01BARPLOT (1)                  [100%] 1 of 1 ✔
[cb/1204f6] process > REFORMATANDQZATAX (1)                [100%] 1 of 1 ✔
[e2/092e0a] process > GENERATEBIOMFORGRAPHLAN (1)          [100%] 1 of 1 ✔
[e1/1557c3] process > RUNGRAPHLAN (1)                      [100%] 1 of 1 ✔
[dd/fb4cf7] process > REPORT02GRAPHLANPHYLOGENETICTREE (1) [  0%] 0 of 1
[2f/1be993] process > REPORT03HEATMAP (1)                  [  0%] 0 of 1
[e5/497905] process > REPORT04ALPHATABLE (1)               [100%] 1 of 1
```

I had a mistype for mode it was mSode, the issue is still heatmaps isn't being copied over. I first want to see if the report copies over. 

Report 01 also did not include images correctly so I'm thinking of trying to knit them in now that we don't have to deal with the mounting issue, and also do this with report 02:

```bash
knitr::include_graphics("temp.png")
```

update WSL2 packages locally

```bash
apt list --upgradable
 
```

### Notes from Class

Projects at the beginning of November, and Meetings with Dr. Bergman to discuss ideas.\
Ideas with improvement with methods and results discussion. RNA-seq might be a good idea for a re-implementation project. 

Homework 4 due next week. 

Variant Calling Format and there is Structural Variants 

30x or more coverage for diploid, 25-50x is good enough.

5x process poisson process mean == varience closer to 1x more missed locations. 

sort map and index bam file to reference file. 

SAMTools and BCFtools are focused on varient calling. 

mpileup command takes mapped read compared to reference using quality score what is the likelihood genotype is like reference alternative, or haplotype. 

VCF and BCF aren't the same binary vs human readable as sam vs bam, can save the compressed human-readable version to save data space but still access the results. 

BCFtools vs Zcat to open the mpileup format

You would want to report the call file format. 

Indel and SNP examples, this is something I've got to wrap my head around, what is QTL. 

Evolutionary genetics, medical, QTL. Next mapping to explore gene expression-> chip-seq and methylation. 

### Meeting with Shailes follow-up with ALDEx2 analysis


---
title: Make Report_02
author: Ben Lorentz
date: '2022-10-14'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Todo for today:

- Start on Report 02
- Check in on classifier still running
- Make up cheat sheet for QIIME2 and Phyloseq

Yesterday we were able to get nextflow verison 0.1 up and running, today the goal is to just get report 02 to run, that's all! If we get past that, it would be awesome.

I was going back and forth on if we should just leave graphan/lefse as a later project, but it is a good exercise in implementing DSL1 code into DSL2. This is also a larger bit to chew off today. 

I also think for either 03 or whichever has the sequence stats, I want to pull in the ampliseq table that they generate that shows what sequences you lose along the way. 

There is an issue with the graphlan biom generations which is signified by:
```bash
There was a problem importing results/dada2/ASV_tax_species.tsv:

  results/dada2/ASV_tax_species.tsv is not a(n) TSVTaxonomyFormat file:

  ['Feature ID', 'Taxon'] must be the first two header values. The first two header values provided are: ['ASV_ID', 'Domain'] (on line 1).
```

So we will need to see which file we can use to import. 

Task: Unzip a taxonomy.qza file and see what kind of format they're working with and then modify my taxonomy file to match it. 

So taxonomy is good and we are generating image files for Graphlan. I also found out that Singulairty is installed on my work laptop so we could in theory use that for development, I just need to push the microbiome_analyst:1.1 image.

My current issue is that report_02 does not see the graplan images and my guess was something related to the symlink but even cping with L which dereferences the files (copies them locally). So I'm not sure what the right solution is now. Temporaraly I will put a note in the report to see the pngs, but I want to see if the issue is docker vs singulairty in the future and what we can do. 

### Todos for next week: 
- Complete on Report 02
  - compare docker vs singularity 
  - push microbiome_analyst:1.1
  - mess with file permissions/symlinks 
- Start Report 03
- Check in on classifier still running
- Make up cheat sheet for QIIME2 and Phyloseq

### Git Commits 

#### Lab notebook

```bash
cb56c4a - Benjamin Lorentz, Fri Oct 14 12:33:59 2022 -0400 : added notes for graphalan biom file formatting
16ab999 - Benjamin Lorentz, Fri Oct 14 10:01:45 2022 -0400 : more notes for friday morning
3ff1601 - Benjamin Lorentz, Fri Oct 14 08:28:27 2022 -0400 : post for friday
```

#### Visualize Ampliseq

```bash
2964823 - Benjamin Lorentz, Fri Oct 14 17:11:22 2022 -0400 : use cp with the dereferecne
21bd4bd - Benjamin Lorentz, Fri Oct 14 17:09:24 2022 -0400 : just call it phy_trees
1f546bd - Benjamin Lorentz, Fri Oct 14 17:08:29 2022 -0400 : gotta get my stars right
ba9c818 - Benjamin Lorentz, Fri Oct 14 17:07:45 2022 -0400 : cp rf
bc3f520 - Benjamin Lorentz, Fri Oct 14 17:05:45 2022 -0400 : gotta make a dir
50ee54f - Benjamin Lorentz, Fri Oct 14 17:05:00 2022 -0400 : try to move files locally before knit
7365837 - Benjamin Lorentz, Fri Oct 14 17:02:01 2022 -0400 : just say error = False
7c85006 - Benjamin Lorentz, Fri Oct 14 16:59:39 2022 -0400 : use normalize path to see if that helps
064226d - Benjamin Lorentz, Fri Oct 14 16:47:37 2022 -0400 : unquote the path
dbe7f15 - Benjamin Lorentz, Fri Oct 14 16:46:19 2022 -0400 : use markdown formatting as opposed to sorted
98e9eb7 - Benjamin Lorentz, Fri Oct 14 16:29:49 2022 -0400 : use the proper name for the report
62bc75c - Benjamin Lorentz, Fri Oct 14 16:26:06 2022 -0400 : added report channel
cddfafc - Benjamin Lorentz, Fri Oct 14 16:15:01 2022 -0400 : fix the lorentzb/lorentzb
95058bd - Benjamin Lorentz, Fri Oct 14 16:11:11 2022 -0400 : I think all the channels are connected correctly
95c19a4 - Benjamin Lorentz, Fri Oct 14 16:08:40 2022 -0400 : added block to format taxonomy file
17209e9 - Benjamin Lorentz, Fri Oct 14 12:23:25 2022 -0400 : need to quote out the qza generation files
eb477d1 - Benjamin Lorentz, Fri Oct 14 12:21:15 2022 -0400 : have each step check for docker or singularity image
a8193da - Benjamin Lorentz, Fri Oct 14 12:01:39 2022 -0400 : need to have enough inputs for generate biom graphlan
477a708 - Benjamin Lorentz, Fri Oct 14 11:59:25 2022 -0400 : put paren around outputs
89490ec - Benjamin Lorentz, Fri Oct 14 11:58:31 2022 -0400 : remove comma in generate biom for graphlan that was not nessecary
9b84d86 - Benjamin Lorentz, Fri Oct 14 11:54:05 2022 -0400 : separate workflow and bracket
3d93f35 - Benjamin Lorentz, Fri Oct 14 11:51:52 2022 -0400 : moved workflow to bottom
d01ca16 - Benjamin Lorentz, Fri Oct 14 11:02:09 2022 -0400 : update readme
528093e - Benjamin Lorentz, Fri Oct 14 11:01:08 2022 -0400 : add report 02 files, and two chunks to generate graphlan phylogenetic trees
```

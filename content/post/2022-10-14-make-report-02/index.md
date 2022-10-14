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
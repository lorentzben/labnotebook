---
title: Shailes Deseq2 analysis
author: Ben Lorentz
date: '2022-11-14'
slug: shailes-deseq2-analysis
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Check what Casey said in slack (if the uncorrected p-vals and FC had the same number of hits)
- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- Re-Run the low med high analyses
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

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

I was able to build a docker image that includes DESeq2, I need to update the docker image to run R-studio (comment out the cmd at the end). Then try to implement the GLM code with contrasts.

Next try to implement Dr. Bergman's Suggestions to see if the methods match the paper (closely). 

Next Review the ampliseq run to see if there is still issues with the diversity analysis. I think the next best solution would be to use core metric out for chunk 10.

### Shaile's Docker Image

I was able to generate some results for the question Shailes was asking which was: "Does the treatment additive cause a significant difference between the challenge and challenge with additive", I sent over the results to him with this email:

```md
Hi Shailes, 

I was able to implement the package DESeq2 to test for differential expression of the different treatment types (control, challenge, challenge+BMD). 
The results are stored in a directory here: https://github.com/lorentzben/picrust2_shailes/tree/main/results that you can download and examine. 

The directory all_together contains the pathways and KEGG id’s that were found to be significant at q < 0.05 for each timepoint (0,24,72,168) and uses contrasts to slice the whole dataset to compare each timepoint.
The directory by_time has the same structure as all_together, however each timepoint was separated into it’s separate analysis and then the comparisons were done.

When comparing the results, all_together was less conservative than by_time so I chose to proceed with by_time, of note the by_time pathways were also found to be significant in the all_together dataset, however there may appear to be some spurious hits. 

The final directory contains the plots in the lefse style format you showed me previously, these are rendered from the by_time results and there are a couple with no significant pathways.

The code used to generate all of these results is here: https://github.com/lorentzben/picrust2_shailes/blob/main/code/Shailes_DESeq2_analysis.Rmd

Please give this all a look over and let me know what kind of questions you have. 

Thanks, 

Ben Lorentz
```

I also found out how to make contrasts make sense in DESeq2. You just need to make sure they are formed in a way DESeq likes (I used [this block](https://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html#contrasts) in the tutorial). For example I set up a contrast to compare challenge and challenge+BMD like this:

```r
resultsNames(dds)

res0_ctrl <- results(dds, contrast=c('group', 'Control0','Challenge_BMD0'))
sighits0_crtl_path <- subset(res0_ctrl, padj < 0.05)
```

I in the end went with the data that was subset to only examine one day at a time since I didn't want to have background noise from day 0 affecting day 168, since this was more conservative and the same pathways were still found to be significant, however I can very much see the argument for the other side. I think this chapter of differential expression is pretty well close to understood, but who knows what's still in store.

### Term paper analysis to match the reference paper

I want to implement Dr. Bergman's suggestion:

```md

```

And compare FC and uncorrected p-values.

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
Hi Ben. 

I think you are interpreting this situation correctly, and if the authors did not correct for multiple testing, then I think their GO analysis is suspect, so there may not be a strong motivation to replicate this part of their analysis.

In your sleuth Wald test analysis, do you also see a large number of genes with beta estimates > 1.5 and uncorrected p-values < 0.05 as are seen for DESeq2 in the paper? If so, perhaps you can run the GO analysis on this DEG list.

Alternatively, to confirm your suspicion that the authors used unccorected p-values, you could try to replicate their DESeq2 analysis. 

Do you feel comfortable trying to do this?In either case, I think you will potentially learn that the DEG list that the authors used for GO analysis may be pretty low stringency, and therefore their GO analysis may not be terribly meaningful /shrug
```

And compare FC and uncorrected p-values.

I decided to run the wald test on the 5 tissues and to look into the gene lists, to make my time worthwhile since there are going to be a ton of hits, I want to sort by p/q value and then sort by fold change to see the smallest p and the largest fold change. Then tomorrow I should see about implementing the DESeq2 analysis to see if the results are similar or different. Slurm job:  32544

### Visualize Ampliseq

I don't think the pipeline actually generates the matrix, so I can pipe in the COREMETRIC.out.distance to bypass that...

### Todos for Today:

- talk to Casey in person about analysis and how to write the words part about a flub
- Run the data through DESeq after samtools(?) or alignment..
- Update Visualize ampliseq to use the correct channel
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

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

### Git Commits

#### Lab Notebook

```bash
6e6919c - Benjamin Lorentz, Mon Nov 14 15:42:15 2022 -0500 : include dr. bergmans note
b6f94dd - Benjamin Lorentz, Mon Nov 14 15:20:38 2022 -0500 : added notes from shailes work and begining of bergman
adabc2a - Benjamin Lorentz, Mon Nov 14 09:22:07 2022 -0500 : added heading for shailes
45fdbfb - Benjamin Lorentz, Mon Nov 14 09:09:50 2022 -0500 : page for monday
```

#### Term Paper

```bash
f3c8b33 - Benjamin Lorentz, Mon Nov 14 16:25:27 2022 -0500 : added wald test scripts and updated sleuth driver script
16e4534 - Benjamin Lorentz, Mon Nov 14 16:21:32 2022 -0500 : generate DGE list using less stringent ps
```

#### Shailes Picrust 2

```bash
015cc4b - Benjamin Lorentz, Mon Nov 14 15:12:04 2022 -0500 : added contrasts doc which has the same results as the inita
l way I did contrasts
5fcd08a - Benjamin Lorentz, Mon Nov 14 14:45:06 2022 -0500 : added result files and code to generate them
d3f4aac - Benjamin Lorentz, Mon Nov 14 12:13:34 2022 -0500 : all together analysis complete
c1df2fd - Benjamin Lorentz, Mon Nov 14 11:26:34 2022 -0500 : added shailes analysis
1f1659b - Benjamin Lorentz, Mon Nov 14 09:21:03 2022 -0500 : added deseq2 docker img
```
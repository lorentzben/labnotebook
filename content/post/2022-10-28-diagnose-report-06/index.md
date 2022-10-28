---
title: Diagnose report 06
author: Ben Lorentz
date: '2022-10-28'
slug: diagnose-report-06
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Todos for Tomorrow:
- Open Enrollment for Work *Done*
- continue reading jones
- Homework 5
- Visualize Ampliseq
  - Refine chunk 06
  - add example params and slurm for ampliseq into ampliseq-vis repos
- Fix chunk 01
  - cd into /home/bjl34716/my_utils/work/7f/657f4474ffedad9c33d2df75047bf0
  - run report 01 line by line in singularity docker://lorentzb/microbiome_analyst:1.1
- nf-core/Ampliseq
  - Plugin error from diversity: All numbers are identical in kruskal [forum link](https://forum.qiime2.org/t/error-plugin-error-from-diversity-all-numbers-are-identical-in-kruskal/15033)
  - examine raw results
  - examine pc results
  - examine raw q2 results
- Term Paper
  - Collect reference genome and annotations
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

- Shaile’s compare flip/flop

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters

### nf-core/ampliseq Diagnose

The error I got for cheeky_becquerel, and soggy_bartik was: "Plugin error from diversity: All numbers are identical in kruskal" 

There was too much data filtered out
cd into /scratch/bjl34716/applegate/villegas_raw_nf/work/d1/7e067af4991b526d54172e6a898785
WARNING The sampling depth of 2 seems too small for rarefaction.txt

check the multiqc /scratch/bjl34716/applegate/villegas_raw_nf/work/09/73e4815ae4c0b4b1a0e2e5a35d13c6/multiqc_report.html

Todo: 
- use qual of 20
  - stoic_brenner 15118977
- Make a subsetted metadata
  - for each level of richness
  - submit to cluster

- run data through with primers for cutadapt?
- use 0,0 for cutoffs
- choose cutoffs based on multiqc
- try pseudopooling for ASV detection [tutorial](https://benjjneb.github.io/dada2/pseudo.html)
  - this will find more rare variants. 
  
My issue is that the data is being filtered too heavily, the minimum count for the sum of each sample was 500 which triggers an error for ampliseq. If minimum count is between 5000-1000 then it will be very small or 10,000-5,000 quite small, if the count is greater than 10,000 then the sampling depth is good. 

I want to compare runs from qual 25 and qual 20. This could be compared by the overall_summary.tsv files.
we are retaining all 90 samples, we may want to cull the data... to retain 80% of the samples. 

We can re-run this analysis with the following samples in the 'B' metadata:

```bash
# filter for balanced richness
D28P52b1cec
D7P52b1cec
D28P58b1cec
D28P28b1cec
D14P17b1cec
D7P55b1cec
D28P60b1cec
D14P35b1cec
D7P57b1cec
D28P34b1cec
D28P40b1cec
D14P23b1cec
D14P11b1cec
D14P19b1cec
D28P38b1cec
D14P3b1cec
D28P44b1cec
```

A following analysis could remove these samples in the 'C' group as they have less than 1000 ASVs by the end of analysis "while much lower number of sequences (~1000) is usually an adequate number to characterize beta-diversity (i.e. differences between samples; (Lundin et al. 2012))."- [Golebiewski et. al 2019](https://sfamjournals.onlinelibrary.wiley.com/doi/10.1111/jam.14380):

```bash
# Filter for least rich
D28P38b1cec
D14P3b1cec
D28P44b1cec
```

Potential workflow:

Run through all samples try to retain as much as possible -> if rarefaction depth is too low remove some samples to examine a more rich analysis. 

A final Even more rich analysis would be removing the following samples and give a potential rarefaction depth of 11,000 features:

```bash
# Filter for most Rich
D14P57b1cec
D14P34b1cec
D28P52b1cec
D7P52b1cec
D28P58b1cec
D28P28b1cec
D14P17b1cec
D7P55b1cec
D28P60b1cec
D14P35b1cec
D7P57b1cec
D28P34b1cec
D28P40b1cec
D14P23b1cec
D14P11b1cec
D14P19b1cec
D28P38b1cec
D14P3b1cec
D28P44b1cec
```

### Visualize Ampliseq

Todo 
  - Refine chunk 06
  - add example params and slurm for ampliseq into ampliseq-vis repos


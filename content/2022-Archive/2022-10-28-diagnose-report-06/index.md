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

Todos for Today:
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

---

- Shaile’s compare flip/flop

---

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

A following analysis could remove these samples in the 'C' group as they have less than 1000 ASVs by the end of analysis "while much lower number of sequences (~1000) is usually an adequate number to characterize beta-diversity (i.e. differences between samples; (Lundin et al. 2012))."- [Golebiewski et. al 2019](https://sfamjournals.onlinelibrary.wiley.com/doi/10.1111/jam.14380) or "There is no single cut-off that works best for all datasets, but researchers often use minimum cut-offs within the range of 1000 to 4000 reads." - [Amplicon SOP qiime2](https://github.com/LangilleLab/microbiome_helper/wiki/Amplicon-SOP-v2-(qiime2-2020.8)#43-exclude-low-depth-samples):

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

This is getting ridiculous so I setup [ampliseq-benchmarking](https://github.com/lorentzben/ampliseq-benchmarking)
on the server: /home/bjl34716/nf_dev/ampliseq-benchmarking
on my local: /mnt/f/my_utils/ampliseq-benchmarking

#### Low Rich analysis

- revision d9450931b808c1b4c6516d4be5eedeb7ee81a35c
- nf name compassionate_hilbert
- slurm slurm-15126906.out

#### Medium Rich analysis

- revision d9450931b808c1b4c6516d4be5eedeb7ee81a35c
- nf-name mighty_poitras
- slurm 15127379

#### High Rich analysis

- revision d9450931b808c1b4c6516d4be5eedeb7ee81a35c
- nf-name angry_wilson
- slurm 15127830

TODO
- include output stats at the end of each run in the repo

### Visualize Ampliseq

Todo 
  - Refine chunk 06
  - add example params and slurm for ampliseq into ampliseq-vis repos
  - Fix chunk 01
    - cd into /home/bjl34716/my_utils/work/7f/657f4474ffedad9c33d2df75047bf0
    - run report 01 line by line in singularity docker://lorentzb/microbiome_analyst:1.1
    
#### Report 01

working dir /home/bjl34716/my_utils/work/7f/657f4474ffedad9c33d2df75047bf0/

we will go line by line to figure out what the issue is: 

```bash
Quitting from lines 118-157 (01_report_MbA.Rmd)
Error in mbSetObj$dataSet : $ operator is invalid for atomic vectors
Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> PlotTaxaAundanceBar
```

Singularity was having trouble accessing local files so I am migrating to the server.
the working directory is /scratch/bjl34716/ampliseq-vis/work/fe/16636a

I think the issue was the skip section of report 01 mba since it removed the header for the metadata file. I have since fixed it in two steps as opposed to one and pushed revision: f0fec40030f3581d86e2c586ae2dddf9fc63f6bd 

We still must fix report 06.

--- 

Todos for Next Week:

- Homework 5
- continue reading jones
- Visualize Ampliseq
  - Refine chunk 06
  - add example params and slurm for ampliseq into ampliseq-vis repos
- nf-core/Ampliseq
  - compare low, medium, high richness results
- Term Paper
  - Collect reference genome and annotations
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Shaile’s compare flip/flop and reply to his email

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters


### Git Log

#### Lab Notebook

```bash
7c887e6 - Benjamin Lorentz, Fri Oct 28 13:03:48 2022 -0400 : notes about my repo for benchmarking ampliseq
b4467e1 - Benjamin Lorentz, Fri Oct 28 11:56:13 2022 -0400 : more notes for friday
9e3adf5 - Benjamin Lorentz, Fri Oct 28 11:49:56 2022 -0400 : notes on subsetting samples
05810f5 - Benjamin Lorentz, Fri Oct 28 08:57:55 2022 -0400 : page for friday
30a1947 - Benjamin Lorentz, Thu Oct 27 17:26:23 2022 -0400 : update path notes for report 01 issues
866ad2c - Benjamin Lorentz, Thu Oct 27 17:24:22 2022 -0400 : notes for the end of thursday
```


#### Ampliseq-benchmark

```bash
d945093 - Benjamin Lorentz, Fri Oct 28 13:00:01 2022 -0400 : had to actually add the manifests
bac1bfb - Benjamin Lorentz, Fri Oct 28 12:56:49 2022 -0400 : needs an underscore as opposed to a hyphen
99cee8e - Benjamin Lorentz, Fri Oct 28 12:54:42 2022 -0400 : update paths so they are correct
483b140 - Benjamin Lorentz, Fri Oct 28 12:50:10 2022 -0400 :  had to separate the string from the bracket
fae2efb - Benjamin Lorentz, Fri Oct 28 12:46:19 2022 -0400 : added manifests in
537216e - Benjamin Lorentz, Fri Oct 28 12:41:11 2022 -0400 : eveything but individual mapping files
228aa98 - Ben Lorentz, Fri Oct 28 12:28:09 2022 -0400 : Initial commit
```

#### Visualize Ampliseq

```bash
f0fec40 - Benjamin Lorentz, Fri Oct 28 16:49:13 2022 -0400 : I think fix the metadata issue
8cf01df - Benjamin Lorentz, Thu Oct 27 17:15:40 2022 -0400 : metadata won't' have a prepend if it is copied in
28f677e - Benjamin Lorentz, Thu Oct 27 17:13:27 2022 -0400 : report 06 is written in R
dbdd3db - Benjamin Lorentz, Thu Oct 27 17:08:08 2022 -0400 : Edits to 01 and 06
```

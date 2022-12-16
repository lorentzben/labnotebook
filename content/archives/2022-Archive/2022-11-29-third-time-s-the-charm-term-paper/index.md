---
title: Third time's the charm (term paper)
author: Ben Lorentz
date: '2022-11-29'
slug: third-time-s-the-charm-term-paper
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Examine htseq-count results slurm 33056
  - do we have to use --stranded reverse; yes.
- rebuild the supplemental tables 1-5 with my results
- Run DESeq2 analysis on htseq-count table
- Visualize Ampliseq
  - examine slurm run 15474870
  
### Term Paper

#### HTSeq results

Slurm Job 33056 suceeded completely. Comparing the results the reverse stranded results look remarkably similar to the unstranded analysis. I will continue with the reverse following the results from the check-strand.py script.

#### Deseq2 

I installed deseq2 and added it to the renv.lock file and pushed this up to github so it is saved. I have set up a skeleton for the script since we have to do some column header modifications before joining and analyzing each tissue individually. ( We could also look at a multi-leveled analysis so we don't have to split the table into separate minitables )

Ceca Significant p-adjusted
130

Duodenum Significant p-adjusted
6

Ileum Significant p-adjusted
201

Jejunum Significant p-adjusted
18

Liver Significant p-adjusted
239

I think that the samples might not be linked to the correct columns so I want to go through and link the Log.final.out files to the supplemental tables.

#### STAR supplemental tables

I started constructing the supplemental tables in the file star result comparion.xslx, this will not tell me exactly what I want, it is a good step but what I need is to run each hisat comparison indvidually and then join them at the end like:

```bash
htseq-count -m intersection-nonempty --stranded reverse -i gene_id hisat_results/C1_R1.sam ../reference/genes.formatted.gtf > C1_count1.gff
htseq-count -m intersection-nonempty --stranded reverse -i gene_id hisat_results/C1_R2.sam ../reference/genes.formatted.gtf > C1_count2.gff
htseq-count -m intersection-nonempty --stranded reverse -i gene_id hisat_results/C1_R3.sam ../reference/genes.formatted.gtf > C1_count3.gff
htseq-count -m intersection-nonempty --stranded reverse -i gene_id hisat_results/C2_R1.sam ../reference/genes.formatted.gtf > C2_count4.gff
htseq-count -m intersection-nonempty --stranded reverse -i gene_id hisat_results/C2_R2.sam ../reference/genes.formatted.gtf > C2_count5.gff
htseq-count -m intersection-nonempty --stranded reverse -i gene_id hisat_results/C2_R3.sam ../reference/genes.formatted.gtf > C2_count6.gff

join C1_count1.gff C1_count2.gff| join - C1_count3.gff | join - C2_count4.gff |join - C2_count5.gff|join - C2_count6.gff > gene_counts_HTseq.gff
```

Then we can add these counts to individual counts. 

### Todos for Tomorrow:

- set up a hiseq-count loop like above and submit
- finish the supplemental tables 1-5 with my results
- Run DESeq2 analysis on htseq-count table
- Visualize Ampliseq
  - examine slurm run 15474870
  
### Git Commits

#### Lab Notebook

```bash
d321621 - Benjamin Lorentz, Tue Nov 29 17:30:18 2022 -0500 : everything for tues except git logs
090514f - Benjamin Lorentz, Tue Nov 29 12:01:07 2022 -0500 : updated progress notes for tuesday
75ae4bd - Benjamin Lorentz, Tue Nov 29 10:37:48 2022 -0500 : added stub for tuesday page
```

#### Term Paper

```bash
84809fc - Benjamin Lorentz, Tue Nov 29 17:29:55 2022 -0500 : added r code to run DESeq2 and some refrence files
ece26e8 - Benjamin Lorentz, Tue Nov 29 11:53:37 2022 -0500 : added skeleton for DGE analysis
9b1855b - Benjamin Lorentz, Tue Nov 29 11:50:54 2022 -0500 : modified renv.lock to include deseq2
```

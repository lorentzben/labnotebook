---
title: Star and Diagnosing Ampliseq
author: Ben Lorentz
date: '2022-11-16'
slug: star-and-diagnosing-ampliseq
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Run the kallisto wt on updated kallisto results
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


### Term Paper

Today I want to run Sleuth WT on the Kallisto with the correct index. I also want to examine the results from Star and see if we can pass it into HTSeq and then make a count table for DESeq2 or another data structure. 

Slurm job for sleuth wt: 32585


Based on one sample (SRR8265630) I think I selected the alignment step went over pretty well:

Uniquely mapped reads number |       3604790
     Uniquely mapped reads % |       94.64%
     
We still must determine strandedness, there is an issue with singularity on the teach cluster so I think I will pull down a set of forward and reverse reads, run the guessmylt in singularity on sapelo2 and then use that to inform HTSeq.

Using the docker image: docker pull quay.io/biocontainers/guessmylt:0.2.5--py_0 
and the file: SRR8265619

```bash
Results of paired library inferred from reads:

   Library type    Relative orientation         Reads     Percent    Vizualization
             ff                matching          1934        9.7%    <=====----<=====


             fr                  inward         14455       72.3%    ----------<=====
                                                                     =====>----------

             rf                 outward          3588       17.9%    <=====----------
                                                                     ----------=====>

      undecided                      NA            23        0.1%    -------??-------
                                                                     -------??-------

Sorry but without annotated gene we cannot stand which strand is the referential (*_firststrand / *_secondstrand).
You cannot guess neither if the library is stranded or unstranded, we can only observe the relative orientation of reads between pairs.
``` 

However I forgot the annotation file so I am running again with the GTF included. I am planning to leave this running overnight.

Once this second analysis runs we can make a decision, and if it is still unclear maybe ask Dr. Bergman about it. 

### Visualize Ampliseq

nf-core/ampliseq keeps hanging on one last job. I want to clean up the work dir and the assets dir and then re-start the analysis of just the low samples to see if is a code or a resource issue. 

The script ran for 12 hours without finishing... so I decided to cancel that run and re-submit, this time without caching to see if that solves the analysis issue.

Slurm job: 15387126
revision: 0c486cd12b74ed0bebe043d73fd7352cea865b1b 
nextflow name: astonishing_cuvier

If it gets hung up again (currently 13:28:48-15:51) then we can add the flag --skip_ancom. There is currently 2 days on the execution, so we might want to wait for this to error out. 


### Host Microbiome 

My task today is to import the Adhikari 2020 paper that I annotated last night. I was able to add it to obsidian though I did not use most of the annotations since they are pretty specific to the housing/strain, but I did add a new page about taxa of interest. 

### Todos for Tomorrow:

- Run the data through DESeq after samtools(?) or alignment..
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
bd9ce76 - Benjamin Lorentz, Wed Nov 16 08:54:20 2022 -0500 : added post for wednesday
751a295 - Ben Lorentz, Tue Nov 15 21:24:24 2022 -0500 : after work note
ef3fda9 - Benjamin Lorentz, Tue Nov 15 17:02:47 2022 -0500 : final notes for tuesday
```

#### Ampliseq Benchmark

```bash
0c486cd - Benjamin Lorentz, Wed Nov 16 10:56:44 2022 -0500 : remove the resume from both nextflow scripts
```

#### Term Paper

```bash
dd33536 - Benjamin Lorentz, Wed Nov 16 11:01:00 2022 -0500 : updated result files and moved old index results
```

#### Host Microbiome 

```bash

```
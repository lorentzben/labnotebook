---
title: 'Exam Review 2'
date: 2023-07-13T13:15:20Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat6315"
  - "microbiome-review"
description: "Description for the page"
---

### Todos for Today

- Figure out what course we should take for Fall
- Read papers about microbiome analysis
- STAT 6315
  - Review For exam 2 (incl notes)
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Implications of the networks generated
  - How does KEGG work?
  - Show Aggrey the charts and ask him what he thinks
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  - Some kind of machine learning classifier to determine major players in a phenotypic outcome.

### Reply about email and figure out what course

If you need something for the fall, you might see if there are seats left in EHSC8460.  We may also have a couple of 1 credit courses focused on specific tools that we offer in the fall &/or spring.

I decided to add STAT 8200 for the Fall, we can add some of the faculty classes later on in the course.

### Microbiome paper

Note from Microbiome 101: Studying, Analyzing, and Interpreting Gut Microbiome Data for Clinicians Allaband et al. :

Consequently, the best option is to use the same PCR primers as other studies with which you would like to compare your results, or if there is no specific study in mind then using widely used primers such as the V1 to V3 or V3 to V5 primers from the Human Microbiome Project or the V4 primers from the Earth Microbiome Project (which have the advantage that they pick up archaea such as Methanobrevibacter and Methanosphaera, which are both important in the gut) is the best plan. 

In general, genus-level resolution is possible for most bacterial taxa, but species resolution is difficult.59 Amplicon analyses in general are challenging to apply to viruses, which is mostly because there is no gene common to all viruses like there is in bacteria
 
The current preferred methods for stool are a combination of shotgun metagenomics and metabolomics. It is likely that metabolomics will not only be able to report on microbially modified or microbially biosynthesized molecules, but also provide a direct read of the medications as well as diet that affect the gut microbiome.

This makes me feel so much better:

Finally, for all next-generation sequencing–based methods of microbiome analysis, it is paramount to include positive and negative controls to help distinguish between signal and noise.

There are several features of microbiome data from a statistical standpoint such as sparsity, compositionality, and zero inflation that make standard statistical tools inappropriate for most microbiome analyses. It is therefore critical to use tools designed for these analyses, such as QIIME/Qiita,81 the BioBakery,92 or PhyloSeq93 that take these considerations into account. 

Best practices for analysing microbiomes Knight et al 2018

 For any study design, appropriate methods to assess statistical power should be employed in order to discern technical variability and real biological results8. However, statistical power and effect size analysis remain a challenge in microbiome research9. Some methods that are currently used for power and effect size analysis are based on PERMANOVA8, Dirichlet Multinomial10 or random forest analysis11. As these methods are further developed to integrate metagenomics, metatranscriptomics, metaproteomics and metabolomics data sets, study design and selection of appropriate sample size will also improve. 
 
The use of blanks during sampling, DNA extraction, PCR and sequencing is essential for detecting contamination. Reads that are derived from microorganisms introduced as contaminants or that grow during shipping can sometimes be reduced during analysis28, though samples should be at −80 °C when possible29.

Mock communities (reference samples with a known composition) are useful for standardizing analyses31, as is including the same standard specimens in each DNA sequencing run32. In general, reconciling microbiome data that were generated using different methods remains an unsolved challenge.

because DNA sequences vary in these primer-amplified regions, primers do not have equal affinity for all possible DNA sequences and consequently induce bias during PCR amplification. Other sources of inherent bias in marker gene sequencing include variable region selection, amplicon size33 and the number of PCR cycles34. Low-biomass samples are particularly susceptible to bias introduced by overamplification — as the PCR cycle number increases, contaminating microorganisms are increasingly over-represented

Come back to this

### Stat 6315

Rewatch all the test 2 review videos
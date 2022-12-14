---
title: Analysis of ampliseq pipeline
author: Ben Lorentz
date: '2022-12-14'
slug: analysis-of-ampliseq-pipeline
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Tomorrow:

- Visualize Ampliseq 
  - examine the 3 results to see what richness should be selected for this set
    - AND record why!!
    - add these notes to the github as an example
    - How do we measure diversity?
      - https://www.nomnomnow.com/learn/article/microbiome-diversity
      - https://pubmed.ncbi.nlm.nih.gov/33510727/
      - https://microbiomeconservancy.org/news/the-global-microbiome-conservancy-the-race-to-preserve-the-species-in-our-feces/
- Host microbiome interaction
  - finish Borda-Molina
  
### Visualize Ampliseq

#### Differences in Reports

- 01_report: Stacked bar plots seems the same
- 02_report: Plots seem the same
- 03_report: lowest filetered_tax_fillter: ~900, lowest middle: ~1,100 lowest high: ~11,000
- 04_report: lowest obs low: 20, mid: ~450, high: ~450 
- 05_report: the lowest richness stretched out the distribution on the lower end, the p-values decreased as the richness increased which could be due to those rare samples which could be true values or could be spurious
- 06_report: there are three samples in the med and high datasets that skew the unweighted unifrac, and the low looks more evenly distributed 
- 07_report: all the same but it looks like the full depth was not considered
- 08_report: ^^
- 09_report: deeper richness highlights some greater differences
- 10_report: the dynamic range was compressed as richness increased
- 11_report: the trend seems the same across richnesses
- 12_report: it seems that p-values become more stringent as richness increases
- 13_report: lefse differential expression results are more abundant. 

#### How do we describe diversity?



### Host Microbiome Interaction


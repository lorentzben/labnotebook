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

### Todos for Today:

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

richness = how many species are present
evenness = how well represented each species is to another
[source](https://www.nomnomnow.com/learn/article/microbiome-diversity)

There are issues when you go not rich enough and when you have too rich, generally you want to balance richness and evenness. 

I found this tool [M&M]() which could be a good use to generate mock communities to see if the tool I have built is performing well and if the visualizations look good. 

### Todos for Tomorrow:

- Visualize Ampliseq 
  - determine the proper richness
    - microbiome helper sop
    - mock community analysis
- Host microbiome interaction
  - finish Borda-Molina

### Git Commits

#### Lab Notebook

```bash
2e3a374 - Ben Lorentz, Wed Dec 14 15:07:44 2022 -0500 : updated cheatsheet with ubuntu command
5f52992 - Ben Lorentz, Wed Dec 14 15:01:23 2022 -0500 : had to leave office since no wifi
2acd0c9 - Benjamin Lorentz, Wed Dec 14 14:18:49 2022 -0500 : added some links to research
2a82e4c - Benjamin Lorentz, Wed Dec 14 14:17:24 2022 -0500 : wednesday update with differences in report
15156eb - Benjamin Lorentz, Wed Dec 14 09:19:35 2022 -0500 : notes for wednesday
d4dd3b4 - Benjamin Lorentz, Tue Dec 13 16:50:38 2022 -0500 : final notes for tuesday
```



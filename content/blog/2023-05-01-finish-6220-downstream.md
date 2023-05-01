---
title: 'Finish 6220 Downstream'
date: 2023-05-01T12:54:26Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
description: "Description for the page"
---

### Todos for Today

- Class
  - Paper finalize
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - Yes NC Yes SRS
     - Yes NC no SRS
     - No NC Yes SRS
     - No NC No SRS
  - Taguchi optmization for richness?
  - Make these subworkflows as opposed to one long workflow?
  - Unit tests based on the example data
  - Positive Control Analysis
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Check out https://youtu.be/oBfu3prR5FA

### STAT 6220

#### Paper Edits

I edited some of the wording and moved some information around so that we have some info in the methods for question 1. I send the edits to 


### Ade

#### SRS Downstream

No SRS Yes NC

This one should "just work" since it was the last implementation, but I still want to go through 1 by 1 to ensure

Rarefaction plot

Pass in the QZA table from the FILTERNEGATIVECONTROL/TSVtoQZA

No SRS No NC

I removed the empty table calls from this section

#### Testing the analyses:

Yes SRS Yes NC:


### Todos for Tomorrow

- Class
  - if there are any paper edits
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - test 4 options
  - Taguchi optmization for richness?
  - Make these subworkflows as opposed to one long workflow?
  - Unit tests based on the example data
  - Positive Control Analysis
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Git Commits

#### Lab Notebook

```bash
62fb19a - Benjamin Lorentz, Mon May 1 08:56:17 2023 -0400 : added page for monday
```

#### Visualize Ampliseq

```bash
9f99cb5 - Benjamin Lorentz, Mon May 1 16:43:45 2023 -0400 : update main.nf
```
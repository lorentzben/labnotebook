---
title: 'Testing All Use Cases'
date: 2023-05-16T12:43:39Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
  - "Module"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish Modularization
    - Test all cases
    - Whats going on with MBA and rarefaction
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
  
### Ade

#### Testing Each Usecase

No SRS No NC Yes Mock Yes Rarefaction

cycle 4 rev: 1b7865dce164c91d240bad6ce38cb94673d621d4
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22785612

```bash
Completed at: 15-May-2023 17:19:19
Duration    : 28m 5s
CPU hours   : 1.9 (33.6% cached)
Succeeded   : 9
Cached      : 28
```

No SRS No NC Yes Mock No Rarefaction

cycle 4 rev: fda6db21bfdeeed4fa736c33ff55642c0dde50d4
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22845220

```bash
```

No SRS No NC Yes Mock Yes Rarefaction

cycle 4 rev: bcaf865240d96432b97acf034153612806da6826
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 

```bash
```


#### Function to fix:

Can we pass in the raw tabel? what does qiime use?

No SRS No Nc No Mock Yes rare:

01_barplot is broken.

No SRS Yes NC No Mock Yes Rarefaction:

01_barplot is broken again

We need to examine this:

https://github.com/search?q=repo%3Axia-lab%2FMicrobiomeAnalystR+%22Too+many+facets+to+be+displayed+-+please+select+a+more+meaningful+facet+option+with+at+least+3+samples+per+group.%22&type=code

#### Remove TODOs

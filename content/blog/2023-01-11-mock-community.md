---
title: 'Mock Community'
date: 2023-01-11T15:36:39Z
draft: false
meta_img: "images/image.png"
tags:
  - "visualize-ampliseq"
  - "rarefaction"
  - "mock microbial community"
description: "Description for the page"
---

### Todos for Today:

- Visualize Ampliseq
  - implement the alpha-rarefaction curve
  - update path in 07 report
- Generate a Mock community M&M or other and validate pipelines
- Examine some papers collected

### Question for This Week:

Can we use a mock community to describe the common taxa in the different chicken gut segments AND can we use that community to benchmark the pipeline we have developed?

### Visualize Ampliseq

#### Report 07

We need to add a process in [for this](https://docs.qiime2.org/2022.11/plugins/available/diversity/alpha-rarefaction/) to be fed into 07_report, and this can be implemented using Python

TODO check that mindepth is the correct cutoff, or if we want maxdepth 
TODO update these save commands

```python3
from qiime2.plugins.diversity.visualizers import alpha_rarefaction
```

We are going to keep the same structure of COREMETRICPYTHON but just sub in the alpha_rarefaction command as oppsed to the diversity pipeline command 


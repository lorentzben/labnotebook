---
title: 'Look Into Srs'
date: 2023-04-12T14:38:32Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
  - "normalize"
  - "figaro"
  - "SRS"
description: "Description for the page"
---

### Todos for Today

- Class
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - examine figaro results
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
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

#### Figaro Results

cycle 4 rev: a0d5d49488705468a68a817b31e9352b831e95bf 
visualize ampliseq rev: 9eb6cb85ee329c5e40eb399c36c71046f78f08b2
slurm job: 20933907

```bash
[cd/4c9fd0] process > NFCORE_AMPLISEQ:AMPLISEQ:QI... [100%] 4 of 4, failed: 1 ✘

Command exit status:
  1

Command output:
  (empty)

Command error:
  QIIME is caching your current deployment for improved performance. This may take a few moments and should only happen once per deployment.
  Plugin error from diversity:

    float division by zero

  Debug info has been saved to /tmp/qiime2-q2cli-err-urcamfx0.log

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/42/abab9eecd5af01671fe6cd7590203e

Completed at: 11-Apr-2023 18:59:58
Duration    : 52m 5s
CPU hours   : 1.3 (0.7% cached)
Succeeded   : 28
Cached      : 1
```

160773d9-8a5f-416f-8869-06ecf8392bd8/data/alpha-diversity.tsv

```bash
        pielou_evenness
LT100   0.946394630357186
LT101   0.946394630357186
LT102   1.0
LT103   0.946394630357186
LT104   1.0
LT105   0.946394630357186
LT106   1.0
LT107   1.0
LT108   1.0
LT109   1.0
LT110   1.0
LT111   1.0
LT112   1.0
LT113   1.0
LT114   1.0
LT115   1.0
LT116   1.0
LT117   0.946394630357186
LT118   0.946394630357186
LT119   1.0
LT120   1.0
LT73
LT74    0.946394630357186
LT75    1.0
LT76    1.0
LT77    1.0
LT78    1.0
LT79    0.946394630357186
```
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
Completed at: 16-May-2023 09:50:19
Duration    : 12m 9s
CPU hours   : 1.9 (28.4% cached)
Succeeded   : 22
Cached      : 10
```

No SRS No NC Yes Mock Yes Rarefaction

cycle 4 rev: bcaf865240d96432b97acf034153612806da6826
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22846399

```bash
  The following objects are masked from 'package:base':

      intersect, setdiff, setequal, union

  ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
  ✔ ggplot2 3.3.6     ✔ purrr   0.3.5
  ✔ tibble  3.1.8     ✔ stringr 1.4.1
  ✔ readr   2.1.3     ✔ forcats 0.5.2
  ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
  ✖ dplyr::filter() masks stats::filter()
  ✖ dplyr::lag()    masks stats::lag()
  Loading required package: memoise
  Quitting from lines 145-184 (01_report_MbA.Rmd)
  Error in AddErr("Too many facets to be displayed - please select a more meaningful facet option with at least 3 samples per group.") :
    could not find function "AddErr"
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> PlotTaxaAundanceBar
  In addition: There were 36 warnings (use warnings() to see them)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/73/0fca0d383323472bdc4605543669d7
```

Yes SRS No NC No Mock No Rarefaction

cycle 4 rev: 777f680c885cdc54f821ebd5ebff3ce227674b5e
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22847548

```bash
Completed at: 16-May-2023 10:33:02
Duration    : 24m 8s
CPU hours   : 1.9 (9% cached)
Succeeded   : 24
Cached      : 6
```

Yes SRS No NC No Mock Yes Rarefaction

cycle 4 rev: ebe79f9c744d4ad77c45e1c9729179899e387d6e
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22849909

```bash
  The following objects are masked from 'package:stats':

      filter, lag

  The following objects are masked from 'package:base':

      intersect, setdiff, setequal, union

  ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
  ✔ ggplot2 3.3.6     ✔ purrr   0.3.5
  ✔ tibble  3.1.8     ✔ stringr 1.4.1
  ✔ readr   2.1.3     ✔ forcats 0.5.2
  ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
  ✖ dplyr::filter() masks stats::filter()
  ✖ dplyr::lag()    masks stats::lag()
  Loading required package: memoise
  Quitting from lines 145-184 (01_report_MbA.Rmd)
  Error in AddErr("Too many facets to be displayed - please select a more meaningful facet option with at least 3 samples per group.") :
    could not find function "AddErr"
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> PlotTaxaAundanceBar
  In addition: There were 36 warnings (use warnings() to see them)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/8d/398e6d68d760c9747be1aa260cb8d0
```

Yes SRS Yes NC No Mock No Rarefaction

cycle 4 rev: 01d667ee3ed650bf216091dacd8c3c17bc499ea0
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22851429

```bash
Completed at: 16-May-2023 11:15:14
Duration    : 23m 7s
CPU hours   : 1.8 (10.1% cached)
Succeeded   : 24
Cached      : 11
```

Yes SRS Yes NC No Mock Yes Rarefaction

cycle 4 rev: 77311e8385808c22f1f9a3b6a8bd6a4d9cd0f4c6
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22854479

```bash
  The following objects are masked from 'package:base':

      intersect, setdiff, setequal, union

  ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
  ✔ ggplot2 3.3.6     ✔ purrr   0.3.5
  ✔ tibble  3.1.8     ✔ stringr 1.4.1
  ✔ readr   2.1.3     ✔ forcats 0.5.2
  ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
  ✖ dplyr::filter() masks stats::filter()
  ✖ dplyr::lag()    masks stats::lag()
  Loading required package: memoise
  Quitting from lines 145-184 (01_report_MbA.Rmd)
  Error in AddErr("Too many facets to be displayed - please select a more meaningful facet option with at least 3 samples per group.") :
    could not find function "AddErr"
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> PlotTaxaAundanceBar
  In addition: There were 36 warnings (use warnings() to see them)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/b7/3e66498c7a3cd67dbbf6597e36b177
```

Yes SRS No NC Yes Mock No Rarefaction

cycle 4 rev: c3d833725b46a6cb2b5cd302b1cd6c4931c91d4c
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22855903

```bash
Completed at: 16-May-2023 11:56:38
Duration    : 15m 8s
CPU hours   : 1.6 (11.2% cached)
Succeeded   : 24
Cached      : 9
```

Yes SRS No NC Yes Mock Yes Rarefaction

cycle 4 rev: 4c72b1d5a1fbf9c8adb81ef580ceddb9da414aac
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22857413

```bash
```


#### Function to fix:

Can we pass in the raw tabel? what does qiime use?

No SRS No Nc No Mock Yes rare:

01_barplot is broken.

No SRS Yes NC No Mock Yes Rarefaction:

01_barplot is broken again

No SRS No Nc Yes Mock Yes Rarefacton:
 
01_barplot is broken again

Yes SRS No NC No Mock Yes Rarefaction

01_barplot is broken again

Yes SRS Yes NC No Mock Yes Rarefaction

01_barplot is broken again

We need to examine this:

https://github.com/search?q=repo%3Axia-lab%2FMicrobiomeAnalystR+%22Too+many+facets+to+be+displayed+-+please+select+a+more+meaningful+facet+option+with+at+least+3+samples+per+group.%22&type=code

#### Remove TODOs

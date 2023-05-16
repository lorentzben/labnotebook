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
  /scratch/bjl34716/ade/cycle-4/work/97/0dba5920797a5b6d4300bcd05d8b5e
```

Yes SRS Yes NC Yes Mock No Rarefaction

cycle 4 rev: adbec537ff3d3ac89c8877506e493527a9469e53
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22865150

```bash
Completed at: 16-May-2023 13:52:04
Duration    : 14m 9s
CPU hours   : 1.5 (37.5% cached)
Succeeded   : 20
Cached      : 18
```

Yes SRS Yes NC Yes Mock Yes Rarefaction

cycle 4 rev: 98c213954d9d342400ef38bcd24672eab2a603d6
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22866958

```bash
Completed at: 16-May-2023 13:56:01
Duration    : 1m 7s
CPU hours   : 2.1 (100% cached)
Succeeded   : 0
Cached      : 38
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

Yes SRS No NC Yes Mock Yes Rarefaction

01_barplot is broken again

No SRS No Nc No Mock Yes rare
No SRS Yes NC No Mock Yes Rarefaction
No SRS No Nc Yes Mock Yes Rarefacton
Yes SRS No NC No Mock Yes Rarefaction
Yes SRS Yes NC No Mock Yes Rarefaction
Yes SRS No NC Yes Mock Yes Rarefaction

We need to examine this:

https://github.com/search?q=repo%3Axia-lab%2FMicrobiomeAnalystR+%22Too+many+facets+to+be+displayed+-+please+select+a+more+meaningful+facet+option+with+at+least+3+samples+per+group.%22&type=code

#### My guess at facet issue:

Based on the error message I think when we rarefy/filter we end up with an uneven number of samples per treatment ex:

```bash

/scratch/bjl34716/ade/cycle-4/work/b7/3e66498c7a3cd67dbbf6597e36b177 

"#NAME" "LT100" "LT101" "LT102" "LT103" "LT104" "LT106" "LT107" "LT108" "LT109" "LT110" "LT111" "LT112" "LT113" "LT114" "LT115"LT116"  "LT117" "LT118" "LT119" "LT120" "LT74"  "LT75"  "LT76"  "LT77"  "LT78"  "LT79"  "LT80"  "LT81"  "LT82"  "LT84"  "LT85""LT86"   "LT87"  "LT88"  "LT89"  "LT90"  "LT91"  "LT92"  "LT93"  "LT95"  "LT98"  "LT99"  "MOCK323""
```
There is only 1 mock sample so I think MBA gets upset, I want to see if we remove that sample if its okay.

One check:
/scratch/bjl34716/ade/cycle-4/work/07/19e5ecfec4d62383659fbcd9a7bb6b

```bash
"#NAME" "LT100" "LT101" "LT102" "LT103" "LT104" "LT106" "LT107" "LT108" "LT109" "LT110" "LT111" "LT112" "LT113" "LT114" "LT115"LT116"  "LT117" "LT118" "LT119" "LT120" "LT74"  "LT75"  "LT76"  "LT77"  "LT78"  "LT79"  "LT80"  "LT81"  "LT82"  "LT84"  "LT85""LT86"   "LT87"  "LT88"  "LT89"  "LT90"  "LT91"  "LT92"  "LT93"  "LT95"  "LT98"  "LT99""
```

No SRS No Nc Yes Mock Yes Rarefaction

cycle 4 rev: 1a398142d61fcfb2c5566a2cf04a90859c702fcb
visualize ampliseq rev: 558b4af7e4dca29d90550a07998d9da730f73130
slurm job: 22869306

```bash
Completed at: 16-May-2023 15:13:54
Duration    : 21m 10s
CPU hours   : 2.1 (67.1% cached)
Succeeded   : 3
Cached      : 29
```

No SRS No Nc No Mock Yes rare

cycle 4 rev: 14a34829331d82aa0ac28d60002e134fe6eceda7
visualize ampliseq rev: 558b4af7e4dca29d90550a07998d9da730f73130
slurm job: 22870433

```bash
Completed at: 16-May-2023 15:35:47
Duration    : 3m 14s
CPU hours   : 2.2 (73.4% cached)
Succeeded   : 3
Cached      : 26
```

No SRS Yes NC No Mock Yes Rarefaction

cycle 4 rev: abac531521b113c33d00b3a780ace054d1c01259
visualize ampliseq rev: 558b4af7e4dca29d90550a07998d9da730f73130
slurm job: 22872297

```bash
Completed at: 16-May-2023 15:57:11
Duration    : 18m 8s
CPU hours   : 2.0 (70.7% cached)
Succeeded   : 3
Cached      : 31
```
Yes SRS No NC No Mock Yes Rarefaction

cycle 4 rev: 838fd3e58606b7431c2a64835a255ad0f5a2d821 
visualize ampliseq rev: 558b4af7e4dca29d90550a07998d9da730f73130
slurm job: 22872683

```bash
Completed at: 16-May-2023 16:24:06
Duration    : 24m 9s
CPU hours   : 2.4 (67.8% cached)
Succeeded   : 4
Cached      : 26
```

Yes SRS Yes NC No Mock Yes Rarefaction

cycle 4 rev: baa7d883d296972d89963efa3fe2d83db084a19c 
visualize ampliseq rev: 558b4af7e4dca29d90550a07998d9da730f73130
slurm job: 22873337

```bash
```

Yes SRS No NC Yes Mock Yes Rarefaction


#### Remove TODOs

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish Modularization
    - Yes SRS No NC Yes Mock Yes Rarefaction
    - Remove TODOs
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
a65264f - Benjamin Lorentz, Tue May 16 12:02:11 2023 -0400 : notes before lunch
b669591 - Benjamin Lorentz, Tue May 16 09:39:47 2023 -0400 : added notes for tuesday
666a614 - Benjamin Lorentz, Mon May 15 16:54:51 2023 -0400 : final notes for monday
```

#### Cycle 4

```bash
baa7d88 - Benjamin Lorentz, Tue May 16 16:28:16 2023 -0400 : update params to /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_SRS_NC.yaml
838fd3e - Benjamin Lorentz, Tue May 16 16:00:56 2023 -0400 : use param /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_SRS.yaml
abac531 - Benjamin Lorentz, Tue May 16 15:39:56 2023 -0400 : updated params to /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_NC.yaml
14a3482 - Benjamin Lorentz, Tue May 16 15:31:27 2023 -0400 : updated params /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter.yaml
1b085c7 - Benjamin Lorentz, Tue May 16 15:28:18 2023 -0400 : update params to /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_SRS_MOCK.yaml
1a39814 - Benjamin Lorentz, Tue May 16 14:53:40 2023 -0400 : use paramfile /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_MOCK.yaml
98c2139 - Benjamin Lorentz, Tue May 16 13:39:31 2023 -0400 : include rarefaction
adbec53 - Benjamin Lorentz, Tue May 16 13:38:50 2023 -0400 : pivot to SRS NC Mock no rare
4c72b1d - Benjamin Lorentz, Tue May 16 11:43:12 2023 -0400 : add rarefaction back in
c3d8337 - Benjamin Lorentz, Tue May 16 11:30:06 2023 -0400 : use srs mock params
77311e8 - Benjamin Lorentz, Tue May 16 10:53:53 2023 -0400 : add rarefaction back in
01d667e - Benjamin Lorentz, Tue May 16 10:52:54 2023 -0400 : update param to srs nc
:...skipping...
baa7d88 - Benjamin Lorentz, Tue May 16 16:28:16 2023 -0400 : update params to /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_SRS_NC.yaml
838fd3e - Benjamin Lorentz, Tue May 16 16:00:56 2023 -0400 : use param /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_SRS.yaml
abac531 - Benjamin Lorentz, Tue May 16 15:39:56 2023 -0400 : updated params to /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_NC.yaml
14a3482 - Benjamin Lorentz, Tue May 16 15:31:27 2023 -0400 : updated params /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter.yaml
1b085c7 - Benjamin Lorentz, Tue May 16 15:28:18 2023 -0400 : update params to /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_SRS_MOCK.yaml
1a39814 - Benjamin Lorentz, Tue May 16 14:53:40 2023 -0400 : use paramfile /home/bjl34716/ade/cycle-4/litter/srs-test/ade_viz_params_litter_MOCK.yaml
98c2139 - Benjamin Lorentz, Tue May 16 13:39:31 2023 -0400 : include rarefaction
adbec53 - Benjamin Lorentz, Tue May 16 13:38:50 2023 -0400 : pivot to SRS NC Mock no rare
4c72b1d - Benjamin Lorentz, Tue May 16 11:43:12 2023 -0400 : add rarefaction back in
c3d8337 - Benjamin Lorentz, Tue May 16 11:30:06 2023 -0400 : use srs mock params
77311e8 - Benjamin Lorentz, Tue May 16 10:53:53 2023 -0400 : add rarefaction back in
01d667e - Benjamin Lorentz, Tue May 16 10:52:54 2023 -0400 : update param to srs nc
ebe79f9 - Benjamin Lorentz, Tue May 16 10:36:56 2023 -0400 : add rarefaction back in
6b7721a - Benjamin Lorentz, Tue May 16 10:10:52 2023 -0400 : update driverscript
777f680 - Benjamin Lorentz, Tue May 16 10:09:17 2023 -0400 : update driver script - no rare litter SRS
bcaf865 - Benjamin Lorentz, Tue May 16 09:38:28 2023 -0400 : update litter mock
fda6db2 - Benjamin Lorentz, Tue May 16 09:37:44 2023 -0400 : update driver script and mock param
```

#### Visualize Amplieseq

```bash
558b4af - Benjamin Lorentz, Tue May 16 14:50:47 2023 -0400 : update visualize ampliseq and 01 report MBA
```
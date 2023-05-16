---
title: 'Continue Report Migration'
date: 2023-05-15T13:11:38Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
  - "Module"
option for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish Modularization
    - Report 09
    - Report 10
    - Report 11
    - Report 12
    - Report 13
    - Test all cases 
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

#### Report 09

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: b7cfcc61cc03d9d33913f3085a5e1bfd1dc444e2
slurm job: 22755895

```bash
No such variable: ord_ioi

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 315 or see '.nextflow.log' file for more details
```

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: 6c3913ce00365f8aee095f3df13213f9d9b633aa
slurm job: 22756023

```bash
[7a/0be893] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Completed at: 15-May-2023 10:40:15
Duration    : 2m 9s
CPU hours   : 0.9 (96.9% cached)
Succeeded   : 1
Cached      : 29
```

#### Report 10

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: 61ab0afe2b48e7a151fe4612ab2c4e85d31eeea5 
slurm job: 22757073

```bash
[92/b38625] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 15-May-2023 11:01:32
Duration    : 7m 47s
CPU hours   : 1.2 (73% cached)
Succeeded   : 2
Cached      : 30
```

#### Report 11

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: a0861fd6e8cbb4112ad1480d96a78b887b7d3178
slurm job: 22758140

```bash
[ba/04cc32] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Waiting files transfer to complete (3 files)
Completed at: 15-May-2023 11:18:31
Duration    : 3m 33s
CPU hours   : 1.2 (95.2% cached)
Succeeded   : 1
Cached      : 32
```

#### Report 12

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: 1f019076928cfc102aceb04b2c8433ce9b801b05
slurm job: 22762209

```bash
Error executing process > 'VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:REPORT12PERMANOVA (null)'

Caused by:
  Not a valid path value: 'Treatment'


Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line
```

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: a9766d84f2bc5a8210c7ee5146a51835934311fa 
slurm job: 22762797

```bash
[39/7b66e4] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Completed at: 15-May-2023 12:05:34
Duration    : 7m 8s
CPU hours   : 1.4 (86.4% cached)
Succeeded   : 1
Cached      : 33
```

#### Report 13

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: bdc347ef70e70aa68917803798d5724979aeaa17
slurm job: 22775214

```bash
Missing process or function with name 'LEFSEFORMAT'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 86 or see '.nextflow.log' file for more details
```

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: 1233d45fc41618e56ef6094ec4dc88e9c75a5755
slurm job: 22775368

```bash
[d9/88240b] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Completed at: 15-May-2023 14:38:17
Duration    : 22m 7s
CPU hours   : 2.1 (67.9% cached)
Succeeded   : 3
Cached      : 34
```

#### Report 14

cycle 4 rev: 7371bf4bedf814cbec7db4050f7e7cca27e71fd9
visualize ampliseq rev: 178bc8400941068abf9c80dc321a4a442470c2d1
slurm job: 22776283

```bash
[78/f83784] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Completed at: 15-May-2023 14:45:18
Duration    : 1m 7s
CPU hours   : 2.1 (99.9% cached)
Succeeded   : 1
Cached      : 37
```

#### Testing Each Usecase

No SRS No NC No Mock No Rarefaction

cycle 4 rev: d3b9fc08644f169f51cf0c52bbb1cdb2024bb70a
visualize ampliseq rev: 178bc8400941068abf9c80dc321a4a442470c2d1
slurm job: 22777195

```bash
Completed at: 15-May-2023 15:27:48
Duration    : 21m 5s
CPU hours   : 2.3 (25.1% cached)
Succeeded   : 22
Cached      : 7
```

No SRS No NC No Mock Yes Rarefaction

cycle 4 rev: d3b9fc08644f169f51cf0c52bbb1cdb2024bb70a
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22778970

```bash
Loading required package: phyloseq

Attaching package: 'dplyr'

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
Execution halted`, size: 1038 (max: 255)

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/25/9c7551ec140f6cd9e5c2d5e1c4353f
```

Need to come back to this:

No SRS Yes NC No Mock No Rarefaction

cycle 4 rev: d6e160cb8a5ed06d206bf8f85e5c34e749156672
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22781360

```bash
Completed at: 15-May-2023 16:17:07
Duration    : 18m 8s
CPU hours   : 2.0 (27.7% cached)
Succeeded   : 22
Cached      : 12
```

No SRS Yes NC No Mock Yes Rarefaction

cycle 4 rev: 43d96d2f103bfca018c78612872c743df65afb5a
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22783244

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
  /scratch/bjl34716/ade/cycle-4/work/f1/d55fccf1e9db9cfdde758797a7082c
```

No SRS Yes NC Yes Mock No Rarefaction

cycle 4 rev: 0421a1e4a140e293354ae14c5bcb1872061bd2fc 
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22784190

```bash
Completed at: 15-May-2023 16:48:26
Duration    : 16m 8s
CPU hours   : 1.9 (49.2% cached)
Succeeded   : 19
Cached      : 18
```

No SRS Yes NC No Mock Yes Rarefaction

cycle 4 rev: 1b7865dce164c91d240bad6ce38cb94673d621d4
visualize ampliseq rev: c2f73491a5c6e9c7ff7c12ca3f953c9cea01b532
slurm job: 22785612

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

### Todos for Tomorrow

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
  
### Git Commits

#### Lab Notebook

```bash
7d45797 - Benjamin Lorentz, Mon May 15 09:14:15 2023 -0400 : add page for monday
```

#### Visualize Ampliseq

```bash
178bc84 - Benjamin Lorentz, Mon May 15 14:44:49 2023 -0400 : update visualize ampliseq
1233d45 - Benjamin Lorentz, Mon May 15 14:16:37 2023 -0400 : update visualize ampliseq
bdc347e - Benjamin Lorentz, Mon May 15 14:12:07 2023 -0400 : update visualize ampliseq
a9766d8 - Benjamin Lorentz, Mon May 15 11:58:49 2023 -0400 : fix the renderrepot12
1f01907 - Benjamin Lorentz, Mon May 15 11:53:07 2023 -0400 : update visualize ampliseq
a0861fd - Benjamin Lorentz, Mon May 15 11:12:01 2023 -0400 : update visualize ampliseq
61ab0af - Benjamin Lorentz, Mon May 15 10:52:46 2023 -0400 : update visualize-ampliseq
6c3913c - Benjamin Lorentz, Mon May 15 10:38:45 2023 -0400 : update visualize ampliseq
b7cfcc6 - Benjamin Lorentz, Mon May 15 10:36:29 2023 -0400 : update visualize ampliseq
```

#### Cycle 4

```bash
1b7865d - Benjamin Lorentz, Mon May 15 16:33:23 2023 -0400 : include rarefaction
0421a1e - Benjamin Lorentz, Mon May 15 16:32:51 2023 -0400 : litter nc mock no rarefact
43d96d2 - Benjamin Lorentz, Mon May 15 16:00:43 2023 -0400 : litter nc with rarenum
d6e160c - Benjamin Lorentz, Mon May 15 15:31:42 2023 -0400 : update param to litter nc
c2f7349 - Benjamin Lorentz, Mon May 15 15:21:10 2023 -0400 : include rarefaction
34cd84c - Benjamin Lorentz, Mon May 15 15:08:32 2023 -0400 : include rarefaction
d3b9fc0 - Benjamin Lorentz, Mon May 15 15:05:57 2023 -0400 : update litter and driverscript
```

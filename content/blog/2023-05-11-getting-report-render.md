---
title: 'Getting Report Render'
date: 2023-05-11T13:35:00Z
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
    - Report 01 ...
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

#### Report Generation Module


cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: 71d931cdd7
slurm sub: 22303640

```bash
Command error:
  
  
  processing file: 01_report_MbA.Rmd
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
  
  ── Column specification ────────────────────────────────────────────────────────
  cols(
    .default = col_double(),
    `"#NAME"` = col_character()
  )
  ℹ Use `spec()` for the full column specifications.
  
  Quitting from lines 38-140 (01_report_MbA.Rmd) 
  Error in mbSetObj$dataSet : $ operator is invalid for atomic vectors
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> Read16SAbundData
  In addition: There were 33 warnings (use warnings() to see them)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/f0/c84373cd7a6d012ae2aaf11bf0d5ff
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 3bf4e94489729954d841e8adff3c74637d02cfd8
slurm sub: 22341883

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Unknown method invocation `container` on _parse_closure5 type
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: c0a61d6dce0ebe12537a7f08efa13fb209fdac24
slurm sub: 22341899

```bash
N E X T F L O W  ~  version 22.04.5
Project config file is malformed -- Cause: No signature of method: nextflow.config.ConfigParser$_parse_closure5.container() is applicable for argument types: (org.codehaus.groovy.runtime.GStringImpl) values: [lorentzb/microbiome_analyst:1.1]
cp: cannot stat ‘/home/bjl34716/ade/cycle-4/litter/srs-test/figaro_result’: No such file or directory
```

Because of the module container this is not a valid approach, shifting approach

#### Report 01

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 9cd7a68f6c2efacf766828672b95e3010ff85b27
slurm sub: 22342414

```bash
N E X T F L O W  ~  version 22.04.5
Project config file is malformed -- Cause: No signature of method: nextflow.config.ConfigParser$_parse_closure5.container() is applicable for argument types: (org.codehaus.groovy.runtime.GStringImpl) values: [lorentzb/microbiome_analyst:1.1]
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: f4867f4e51ead2c18a5440923c244ca4098d98e6
slurm sub: 22342486

```bash
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

── Column specification ────────────────────────────────────────────────────────
cols(
  .default = col_double(),
  `"#NAME"` = col_character()
)
ℹ Use `spec()` for the full column specifications.

Quitting from lines 38-140 (01_report_MbA.Rmd)
Error in mbSetObj$dataSet : $ operator is invalid for atomic vectors
Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> Read16SAbundData
In addition: There were 33 warnings (use warnings() to see them)
Execution halted`, size: 1097 (max: 255)

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/9e/e4e784f37e24f02838f5d0c12a3760
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: d31a4262963c46c48e48561c5e91b9262670aed0 
slurm sub: 22342792

```bash
Error executing process > 'VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:REPORT01BARPLOT (Report_01)'

Caused by:
  Missing output file(s) `figures/*` expected by process `VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:REPORT01BARPLOT (Report_01)`

Command executed:

  #!/usr/bin/env bash

  ls -lRh

  dt=$(date '+%d-%m-%Y_%H.%M.%S');
  Rscript -e "rmarkdown::render('01_report_MbA.Rmd', output_file='$PWD/01_report_MbA.Rmd_$dt.html', output_format='html_document', clean=TRUE, knit_root_dir='$PWD')"

  #Rscript -e "rmarkdown::render('"01_report_MbA.Rmd"', output_file='$PWD/"01_report_MbA.Rmd"_$dt.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='$PWD')"

Command exit status:
  0
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 3a5df0da8dec1ef77723713eda75f92a9198c91e
slurm sub: 22342821

```bash
[07/19e5ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
Completed at: 11-May-2023 11:36:58
Duration    : 1m 4s
CPU hours   : 0.6 (100% cached)
Succeeded   : 0
Cached      : 20
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 40b401601e7e93ec658e6426aa60acefd83a037a
slurm sub: 22342932

updated modules.conf

```bash
[07/19e5ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
Completed at: 11-May-2023 11:47:21
Duration    : 1m 5s
CPU hours   : 0.6 (100% cached)
Succeeded   : 0
Cached      : 20
```

LGTM

#### Report 02




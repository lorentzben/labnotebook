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


cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 4a424733e10fa67bf63445e3184282660de7fe69
slurm sub: 22346718

```bash
No such variable: emit

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/renderreport02.nf' at line: 20 or see '.nextflow.log' file for more details
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 9ee1e0e40f8272411f13f8f5b1abb19751a2a553
slurm sub: 22346788

```bash
Completed at: 11-May-2023 13:59:46
Duration    : 1m 6s
CPU hours   : 0.6 (100% cached)
Succeeded   : 0
Cached      : 20
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 77d52827300fc3d9fe997d978fd06255ead7cdda
slurm sub: 22346888

```bash
Execution cancelled -- Finishing pending tasks before exit
Error executing process > 'VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:REPORT02GRAPHLANPHYLOGENETICTREE (null)'

Caused by:
  Not a valid path value: 'Treatment'


Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line



cp: cannot stat ‘/home/bjl34716/ade/cycle-4/litter/srs-test/figaro_result’: No such file or directory
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: a669c0235967ccd9fd71b13cc05b30aa99273bf9
slurm sub: 22346927

```bash
[8d/3e5fa5] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Completed at: 11-May-2023 14:13:05
Duration    : 1m 5s
CPU hours   : 0.7 (99.6% cached)
Succeeded   : 1
Cached      : 21
```

#### Report 03

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 4ad3554bd94c26c7377224d51defc9cc7e27b2a6
slurm sub: 22355857

```bash
[8d/3e5fa5] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Completed at: 11-May-2023 14:13:05
Duration    : 1m 5s
CPU hours   : 0.7 (99.6% cached)
Succeeded   : 1
Cached      : 21
```

#### Report 04

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 398ecda167e9e6d1b1b4916e349919c5dba35240
slurm sub: 22359561

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Unknown method invocation `publishDir` on _parse_closure5 type


cp: cannot stat ‘/home/bjl34716/ade/cycle-4/litter/srs-test/figaro_result’: No such file or directory
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 7296c9ed2f6659cd5b20493a7e3d953d9d416664
slurm sub: 22359795

```bash
Process `VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:REPORT04ALPHATABLE` declares 4 input channels but 3 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 282 or see '.nextflow.log' file for more details

[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
:
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 82a620503278faab611cfd214e44645c1220f2e2
slurm sub: 22360270

```bash
Completed at: 11-May-2023 15:50:25
Duration    : 2m 7s
CPU hours   : 0.7 (98.4% cached)
Succeeded   : 2
Cached      : 23
```

#### Report 05

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: 91eedffb891fef0dd0037a2bfff57918ec0c9c2f
slurm sub: 22371405

```bash
No such variable: ord_ioi

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 285 or see '.nextflow.log' file for more details
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c
visualize ampliseq rev: fd8b86a75bdddb5736d9ff280b48cbca65090ba8
slurm sub: 22371725

```bash
processing file: 05_report.Rmd
Saving 7 x 5 in image
Saving 7 x 5 in image
── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
✔ tibble  3.1.6     ✔ dplyr   1.0.8
✔ tidyr   1.2.0     ✔ stringr 1.4.0
✔ readr   2.1.2     ✔ forcats 0.5.1
✔ purrr   0.3.4
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter()     masks stats::filter()
✖ dplyr::group_rows() masks kableExtra::group_rows()
✖ dplyr::lag()        masks stats::lag()

Attaching package: 'rstatix'

The following object is masked from 'package:stats':

    filter

Saving 7 x 5 in image
Saving 7 x 5 in image
Saving 7 x 5 in image
Quitting from lines 191-269 (05_report.Rmd)
Error in eval(predvars, data, env) : object 'shannon_entropy' not found
Calls: <Anonymous> ... eval -> <Anonymous> -> model.frame.default -> eval -> eval
In addition: There were 38 warnings (use warnings() to see them)
Execution halted`, size: 949 (max: 255)
Work dir:
  /scratch/bjl34716/ade/cycle-4/work/83/ce09b0226d5aa75827fb597f5ca025
```

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish Modularization
    - Report 05 issue:
      - 22371725
    - Report 06
    - Report 07
    - Report 08
    - Report 09
    - Report 10
    - Report 11
    - Report 12
    - Report 13
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
5c108cb - Benjamin Lorentz, Thu May 11 11:59:27 2023 -0400 : added notes to lunch
8c773e6 - Benjamin Lorentz, Thu May 11 10:20:56 2023 -0400 : add a page for Thursday
6b69281 - Benjamin Lorentz, Wed May 10 17:05:00 2023 -0400 : final notes for wednesday
```

#### Visualize Ampliseq

```bash
fd8b86a - Benjamin Lorentz, Thu May 11 16:51:55 2023 -0400 : update visualize-ampliseq
91eedff - Benjamin Lorentz, Thu May 11 16:47:40 2023 -0400 : add report 05
82a6205 - Benjamin Lorentz, Thu May 11 15:48:23 2023 -0400 : update visualize-ampliseq
7296c9e - Benjamin Lorentz, Thu May 11 15:45:50 2023 -0400 : update modules conf
398ecda - Benjamin Lorentz, Thu May 11 15:44:03 2023 -0400 : add module for 4 and coreqzatotsv export
e1377c5 - Benjamin Lorentz, Thu May 11 15:25:58 2023 -0400 : update modules.conf
4ad3554 - Benjamin Lorentz, Thu May 11 15:22:01 2023 -0400 : add report 03
a669c02 - Benjamin Lorentz, Thu May 11 14:11:46 2023 -0400 : update renderreport02 channel
77d5282 - Benjamin Lorentz, Thu May 11 14:07:46 2023 -0400 : update visualize-ampliseq
143d996 - Benjamin Lorentz, Thu May 11 14:06:04 2023 -0400 : fix report 02 name
9ee1e0e - Benjamin Lorentz, Thu May 11 13:57:05 2023 -0400 : update renderreport02
4a42473 - Benjamin Lorentz, Thu May 11 13:55:08 2023 -0400 : add reportname
92b7218 - Benjamin Lorentz, Thu May 11 13:54:09 2023 -0400 : update visualize-ampliseq.nf
:...skipping...
fd8b86a - Benjamin Lorentz, Thu May 11 16:51:55 2023 -0400 : update visualize-ampliseq
91eedff - Benjamin Lorentz, Thu May 11 16:47:40 2023 -0400 : add report 05
82a6205 - Benjamin Lorentz, Thu May 11 15:48:23 2023 -0400 : update visualize-ampliseq
7296c9e - Benjamin Lorentz, Thu May 11 15:45:50 2023 -0400 : update modules conf
398ecda - Benjamin Lorentz, Thu May 11 15:44:03 2023 -0400 : add module for 4 and coreqzatotsv export
e1377c5 - Benjamin Lorentz, Thu May 11 15:25:58 2023 -0400 : update modules.conf
4ad3554 - Benjamin Lorentz, Thu May 11 15:22:01 2023 -0400 : add report 03
a669c02 - Benjamin Lorentz, Thu May 11 14:11:46 2023 -0400 : update renderreport02 channel
77d5282 - Benjamin Lorentz, Thu May 11 14:07:46 2023 -0400 : update visualize-ampliseq
143d996 - Benjamin Lorentz, Thu May 11 14:06:04 2023 -0400 : fix report 02 name
9ee1e0e - Benjamin Lorentz, Thu May 11 13:57:05 2023 -0400 : update renderreport02
4a42473 - Benjamin Lorentz, Thu May 11 13:55:08 2023 -0400 : add reportname
92b7218 - Benjamin Lorentz, Thu May 11 13:54:09 2023 -0400 : update visualize-ampliseq.nf
40b4016 - Benjamin Lorentz, Thu May 11 11:45:31 2023 -0400 : update modules.conf
3a5df0d - Benjamin Lorentz, Thu May 11 11:35:36 2023 -0400 : update rendereport 01
d31a426 - Benjamin Lorentz, Thu May 11 11:31:54 2023 -0400 : update 01_report_MbA
f4867f4 - Benjamin Lorentz, Thu May 11 11:06:15 2023 -0400 : remove equals sign
9cd7a68 - Benjamin Lorentz, Thu May 11 11:03:14 2023 -0400 : add module renderreport01
c0a61d6 - Benjamin Lorentz, Thu May 11 10:29:23 2023 -0400 : update nextflow.config
3bf4e94 - Benjamin Lorentz, Thu May 11 10:26:57 2023 -0400 : update nextflow.config and renderreport
71d931c - Benjamin Lorentz, Wed May 10 17:01:46 2023 -0400 : remove sep
```



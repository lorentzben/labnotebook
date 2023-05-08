---
title: 'Rebuild Main.nf'
date: 2023-05-05T13:40:19Z
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

- Class
  - if there are any paper edits
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - Filter NC and Mock Samples
     - Update downstream processes for SRS NC MOCK
     - Implement the other ones
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

#### Downstream processes:

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 4e0038876815fb717361918409a3ddec2fd627e
slurm sub: 21994911

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
  • `0` -> `0...52`
  • `0` -> `0...53`
  • `0` -> `0...54`
  • `0` -> `0...55`
  • `0` -> `0...56`
  Rows: 1741 Columns: 56
  ── Column specification ────────────────────────────────────────────────────────
  Delimiter: "\t"
  chr  (1): 7b9c8d4a1896d84d92ab4820edd025a6
  dbl (55): 36, 60, 395, 372, 277, 0...7, 536, 43, 38, 749, 519, 558, 1070, 22...
  
  ℹ Use `spec()` to retrieve the full column specification for this data.
  ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
  Error in `select()`:
  ! Can't subset columns that don't exist.
  ✖ Column `X.OTU.ID` doesn't exist.
  Backtrace:
       ▆
    1. ├─table %>% select(-c("X.OTU.ID"))
    2. ├─dplyr::select(., -c("X.OTU.ID"))
    3. └─dplyr:::select.data.frame(., -c("X.OTU.ID"))
    4.   ├─dplyr:::tidyselect_fix_call(...)
    5.   │ └─base::withCallingHandlers(...)
    6.   └─tidyselect::eval_select(expr(c(...)), .data)
    7.     └─tidyselect:::eval_select_impl(...)
    8.       ├─tidyselect:::with_subscript_errors(...)
    9.       │ ├─base::tryCatch(...)
   10.       │ │ └─base tryCatchList(expr, classes, parentenv, handlers)
   11.       │ │   └─base tryCatchOne(expr, names, parentenv, handlers[[1L]])
   12.       │ │     └─base doTryCatch(return(expr), name, parentenv, handler)
   13.       │ └─tidyselect:::with_entraced_errors(expr)
   14.       │   └─rlang::try_fetch(...)
   15.       │     └─base::withCallingHandlers(...)
   16.       └─tidyselect:::vars_select_eval(...)
   17.         └─tidyselect:::walk_data_tree(expr, data_mask, context_mask, error_call)
   18.           └─tidyselect:::eval_c(expr, data_mask, context_mask)
   19.             └─tidyselect:::reduce_sels(node, data_mask, context_mask, init = init)
   20.               └─tidyselect:::walk_data_tree(new, data_mask, context_mask)
   21.                 └─tidyselect:::eval_c(expr, data_mask, context_mask)
   22.                   └─tidyselect:::reduce_sels(node, data_mask, context_mask, init = init)
   23.                     └─tidyselect:::walk_data_tree(new, data_mask, context_mask)
   24.                       └─tidyselect:::as_indices_sel_impl(...)
   25.                         └─tidyselect:::as_indices_impl(x, vars, call = call, strict = strict)
   26.                           └─tidyselect:::chr_as_locations(x, vars, call = call)
   27.                             └─vctrs::vec_as_location(x, n = length(vars), names = vars)
   28.                               └─vctrs `<fn>`()
   29.                                 └─vctrs:::stop_subscript_oob(...)
   30.                                   └─vctrs:::stop_subscript(...)
   31.                                     └─rlang::abort(...)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/62/e7d00602edff9cab379936cb6b09c1
```
```

/scratch/bjl34716/ade/cycle-4/work/62/e7d00602edff9cab379936cb6b09c1



cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: e1e9c5842a4398c968d0038f6ddfb6c300a1f754
slurm sub: 22028941

```bash
Execution cancelled -- Finishing pending tasks before exit
Error executing process > 'FILTERNEGATIVECONTROL (1)'

Caused by:
  Not a valid path value: 'NC'


Tip: view the complete command output by changing to the process work dir and entering the command `cat .command.out`
```


cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: a4c536b05398fcab7797cd1da8f44d656dde1e97
slurm sub: 22028974

```bash
  ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
  ✔ ggplot2 3.3.6     ✔ purrr   0.3.4
  ✔ tibble  3.1.7     ✔ dplyr   1.0.9
  ✔ tidyr   1.2.0     ✔ stringr 1.4.0
  ✔ readr   2.1.2     ✔ forcats 0.5.1
  ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
  ✖ dplyr::filter() masks stats::filter()
  ✖ dplyr::lag()    masks stats::lag()
  Error in read.table("nc_name.txt") : no lines available in input
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/76/564b177ca06a15453f3a2a9e44334f

Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
✔ ggplot2 3.3.6     ✔ purrr   0.3.4
✔ tibble  3.1.7     ✔ dplyr   1.0.9
✔ tidyr   1.2.0     ✔ stringr 1.4.0
✔ readr   2.1.2     ✔ forcats 0.5.1
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
Error in read.table("nc_name.txt") : no lines available in input
Execution halted`, size: 464 (max: 255)
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: c941156c9c4c8704d50d1730e5b21ce074f46ad2
slurm sub: 22029029

```bash
Caused by:
  Process `SRSNORMALIZE (1)` terminated with an error exit status (1)

Command executed:
Command exit status:
  1

Command output:
  (empty)

Command error:
  Loading required package: vegan
  Loading required package: permute
  Loading required package: lattice
  This is vegan 2.6-2
  Loading required package: shiny
  Loading required package: DT

  Attaching package: ‘DT’

  The following objects are masked from ‘package:shiny’:

      dataTableOutput, renderDataTable

  Loading required package: shinycssloaders
  Loading required package: shinybusy
  Warning message:
  In readLines("/scratch/bjl34716/ade/cycle-4/work/5a/365310254ec7672b2bc7d1a2420a56/srs_min_curve_val.txt") :
    incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/5a/365310254ec7672b2bc7d1a2420a56/srs_min_curve_val.txt'
  Error in colSums(data) : 'x' must be numeric
  Calls: SRS -> colSums
  Execution halted
Work dir:
  /scratch/bjl34716/ade/cycle-4/work/79/05f938043a560be32f0909667acd39

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `Loading required package: vegan
Loading required package: permute
Loading required package: lattice
This is vegan 2.6-2
Loading required package: shiny
Loading required package: DT

Attaching package: ‘DT’

The following objects are masked from ‘package:shiny’:

    dataTableOutput, renderDataTable

Loading required package: shinycssloaders
Loading required package: shinybusy
Warning message:
In readLines("/scratch/bjl34716/ade/cycle-4/work/5a/365310254ec7672b2bc7d1a2420a56/srs_min_curve_val.txt") :
  incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/5a/365310254ec7672b2bc7d1a2420a56/srs_min_curve_val.txt'
Error in colSums(data) : 'x' must be numeric
Calls: SRS -> colSums
Execution halted`, size: 714 (max: 255)
```

This is using the most rare version of the feature table, lets trace it backwards:

```groovy
SRSNORMALIZE(filtered_tsv_table, SRSCURVE.out.min_val, params.rare)
SRSCURVE(filtered_qza_table, filtered_tsv_table, srs_curve_ch, srs_min_max_ch)
filtered_tsv_table = QIIME2_EXPORT_ABSOLUTE_MOCK.out.tsv

```

#### Making a Subworkflow

Starting with Yes NC, Yes Mock, Yes SRS

just trying ord ioi

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 0b5a9d6be3f4d8bb6e979dcddc061386a0b1777e
slurm sub: 22038028

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [elated_jones] DSL2 - revision: 0b5a9d6be3 [srs]
No such variable: WorkflowMain

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 82 or see '.nextflow.log' file for more details
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 4351c3846eeb1b2f090fa9e87d2924dd5efae6b2
slurm sub: 22038113

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [hopeful_williams] DSL2 - revision: 4351c3846e [srs]
No such variable: WorkflowMain

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 82 or see '.nextflow.log' file for more details
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: edea0d5296c761c96929b824f95b83d1cede9505
slurm sub: 22038168

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [wise_borg] DSL2 - revision: edea0d5296 [srs]
No such variable: WorkflowMain

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 82 or see '.nextflow.log' file for more details
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: cc9dc59743f4d7867b8a798cf69fa42a62a0c979
slurm sub: 22038172

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [lethal_meitner] DSL2 - revision: cc9dc59743 [srs]
No such variable: WorkflowVisualizeAmpliseq

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 3 or see '.nextflow.log' file for more details
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: ff2eac75ce7b961706867abd67e049fd0d095621
slurm sub: 22038180

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [exotic_colden] DSL2 - revision: ff2eac75ce [srs]
WARN: Access to undefined parameter `control` -- Initialise it to a default value eg. `params.control = some_value`
No such variable: NfcoreSchema

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 65 or see '.nextflow.log' file for more details
```


cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 67fc993a23612a45b93d200819519256d5364a67
slurm sub: 22038200

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [drunk_lovelace] DSL2 - revision: 67fc993a23 [srs]
Unknown process directive: `_out_file`

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/orderioi.nf' at line: 17 or see '.nextflow.log' file for more details
```



cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: d81fa2f81db6ba300b6cf02d014a23d08eadcc38
slurm sub: 22038223

```bash
Completed at: 05-May-2023 15:04:45
Duration    : 1m 3s
CPU hours   : (a few seconds)
Succeeded   : 1
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 827ae441a989cb6f5ba46c22bd51c87ed1595860
slurm sub: 22038354

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
No such file: Config file does not exist: /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/conf/modules.config
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 23a61bb03407fcfde6e6d9c6bb7288a56f4d50b0
slurm sub: 22038385

```bash
Completed at: 05-May-2023 15:37:39
Duration    : 1m 3s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 1
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: c81e7bb731431c0d67f13341b41638855b139fd1
slurm sub: 22038510

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [extravagant_pesquet] DSL2 - revision: c81e7bb731 [srs]
No such variable: Exception evaluating property 'out' for nextflow.script.ChannelOut, Reason: groovy.lang.MissingPropertyException: No such property: out for class: groovyx.gpars.dataflow.DataflowBroadcast

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 75 or see '.nextflow.log' file for more details
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: a839b58b93e67d706a0f72cd5afa3e086a9f64c4
slurm sub: 22038529

```bash
No such file: /scratch/bjl34716/ade/cycle-4/litter-srsresults/qiime2/phylogenetic_tree/rooted-tree.qza
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 905b8246f743b651f110f73e1a7bafa5c94dcd0f
slurm sub: 22038536

```bash
Completed at: 05-May-2023 16:08:29
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 2
Cached      : 1
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: abe8c1a7467e400655593a1af0812610dc6cf50c
slurm sub: 22038845

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [crazy_boyd] DSL2 - revision: abe8c1a746 [srs]
Missing process or function with name 'FILTERNEGATIVECONTROL'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 86 or see '.nextflow.log' file for more details
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 11f9a60a1c83643e6506a7eb646d6f619880c08e
slurm sub: 22038863

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [clever_perlman] DSL2 - revision: 11f9a60a1c [srs]
Missing process or function with name 'FILTERNEGATIVECONTROL'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 86 or see '.nextflow.log' file for more details
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -

```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 955ef0f8810ab19e35286cf83d5653ae801fd9a6 
slurm sub: 22038887

```bash

N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [kickass_bell] DSL2 - revision: 955ef0f881 [srs]
Missing process or function with name 'ifEmpty'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 86 or see '.nextflow.log' file for more details
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 7a7305bd845cd95847944363cbea9f7381b94591
slurm sub: 22038954

```bash
Completed at: 05-May-2023 16:56:19
Duration    : 5m 4s
CPU hours   : (a few seconds)
Succeeded   : 6
Cached      : 3
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: a763266943f2386299d4201e478b5ccb402bca2a
slurm sub: 22039096

```bash
/scratch/bjl34716/ade/cycle-4/work/81/6235904316606a9a487689523d9856/NC.qza
/scratch/bjl34716/ade/cycle-4/work/01/d90a4d6681d0d44427136bcd0c4e92/feature-table.tsv
/scratch/bjl34716/ade/cycle-4/work/79/5a9cb23f75f755bc1b69140b661853/MOCK.qza
/scratch/bjl34716/ade/cycle-4/work/72/b9efca874b51ad0dd892ac460c3e49/feature-table.tsv

Completed at: 05-May-2023 16:59:54
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 9

[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e6/c60301] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[dc/94eb24] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7d/6e7a31] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[81/623590] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[01/d90a4d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[79/5a9cb2] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[72/b9efca] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
```

Sick! So when you set the channel it will overwrite

### Todos for Next Week


- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
    - continue down the script into modules
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

#### Lab notebook

```bash
7ae25e8 - Benjamin Lorentz, Fri May 5 09:42:12 2023 -0400 : added page for friday
a839eff - Benjamin Lorentz, Thu May 4 17:14:32 2023 -0400 : final notes for thursday
```

#### Visualize Ampliseq

```bash
a763266 - Benjamin Lorentz, Fri May 5 16:59:00 2023 -0400 : update visualize ampliseq
7a7305b - Benjamin Lorentz, Fri May 5 16:51:14 2023 -0400 : update visualize-ampliseq.nf
955ef0f - Benjamin Lorentz, Fri May 5 16:46:44 2023 -0400 : add back in the filter negative control script
11f9a60 - Benjamin Lorentz, Fri May 5 16:43:58 2023 -0400 : update modules.conf
abe8c1a - Benjamin Lorentz, Fri May 5 16:41:53 2023 -0400 : update visualize-ampliseq
905b824 - Benjamin Lorentz, Fri May 5 16:07:20 2023 -0400 : update visualize ampliseq
a839b58 - Benjamin Lorentz, Fri May 5 16:04:36 2023 -0400 : update visulize-ampliseq
c81e7bb - Benjamin Lorentz, Fri May 5 16:00:46 2023 -0400 : add clean up raw table processes
ccc7ae1 - Benjamin Lorentz, Fri May 5 15:43:38 2023 -0400 : update tower.yml
23a61bb - Benjamin Lorentz, Fri May 5 15:36:49 2023 -0400 : update nextflow.conf
827ae44 - Benjamin Lorentz, Fri May 5 15:31:32 2023 -0400 : update conf files
0cb1cff - Benjamin Lorentz, Fri May 5 15:25:30 2023 -0400 : update tower.yaml
1d061dd - Benjamin Lorentz, Fri May 5 15:21:40 2023 -0400 : update tower.yaml
:...skipping...
a763266 - Benjamin Lorentz, Fri May 5 16:59:00 2023 -0400 : update visualize ampliseq
7a7305b - Benjamin Lorentz, Fri May 5 16:51:14 2023 -0400 : update visualize-ampliseq.nf
955ef0f - Benjamin Lorentz, Fri May 5 16:46:44 2023 -0400 : add back in the filter negative control script
11f9a60 - Benjamin Lorentz, Fri May 5 16:43:58 2023 -0400 : update modules.conf
abe8c1a - Benjamin Lorentz, Fri May 5 16:41:53 2023 -0400 : update visualize-ampliseq
905b824 - Benjamin Lorentz, Fri May 5 16:07:20 2023 -0400 : update visualize ampliseq
a839b58 - Benjamin Lorentz, Fri May 5 16:04:36 2023 -0400 : update visulize-ampliseq
c81e7bb - Benjamin Lorentz, Fri May 5 16:00:46 2023 -0400 : add clean up raw table processes
ccc7ae1 - Benjamin Lorentz, Fri May 5 15:43:38 2023 -0400 : update tower.yml
23a61bb - Benjamin Lorentz, Fri May 5 15:36:49 2023 -0400 : update nextflow.conf
827ae44 - Benjamin Lorentz, Fri May 5 15:31:32 2023 -0400 : update conf files
0cb1cff - Benjamin Lorentz, Fri May 5 15:25:30 2023 -0400 : update tower.yaml
1d061dd - Benjamin Lorentz, Fri May 5 15:21:40 2023 -0400 : update tower.yaml
ca491e1 - Benjamin Lorentz, Fri May 5 15:19:55 2023 -0400 : add modules.conf
d81fa2f - Benjamin Lorentz, Fri May 5 15:03:34 2023 -0400 : update orderioi
67fc993 - Benjamin Lorentz, Fri May 5 15:00:36 2023 -0400 : update visualize-ampliseq.nf
ff2eac7 - Benjamin Lorentz, Fri May 5 14:57:35 2023 -0400 : update visualize-ampliseq.nf
cc9dc59 - Benjamin Lorentz, Fri May 5 14:56:12 2023 -0400 : update main.nf
edea0d5 - Benjamin Lorentz, Fri May 5 14:53:35 2023 -0400 : update visualize-ampliseq.nf
dd99994 - Benjamin Lorentz, Fri May 5 14:50:56 2023 -0400 : update orderioi module
4351c38 - Benjamin Lorentz, Fri May 5 14:43:47 2023 -0400 : update main.nf and nextflow config
0b5a9d6 - Benjamin Lorentz, Fri May 5 14:37:55 2023 -0400 : first step refactoring into a workflow
dcad684 - Benjamin Lorentz, Fri May 5 12:03:47 2023 -0400 : add workflows and subworkflows
c941156 - Benjamin Lorentz, Fri May 5 10:49:25 2023 -0400 : update main.nf
a4c536b - Benjamin Lorentz, Fri May 5 10:41:30 2023 -0400 : update main.nf
e1e9c58 - Benjamin Lorentz, Fri May 5 10:37:39 2023 -0400 : update main.nf and contam_script.r
4e00388 - Benjamin Lorentz, Thu May 4 17:07:37 2023 -0400 : update main and contam_script.r
```


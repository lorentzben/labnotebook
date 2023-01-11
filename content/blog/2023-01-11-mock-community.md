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

We are going to keep the same structure of COREMETRICPYTHON but just sub in the alpha_rarefaction command as oppsed to the diversity pipeline command.

does core metric python generate the curve and we just didn't save it?

- it does not, we must generate it.

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: eede4489f254c5cb22ac8088cd9147dde3a8127d
slurm sub: 16923200

```bash
No such variable: emit

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 766
```

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: 678b7b8054b1523fe3a1c8617af1baa9b18994f3
slurm sub: 16923247

```bash
Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Traceback (most recent call last):
    File ".command.sh", line 57, in <module>
      rarefact = alpha_rarefaction(table, rooted_tree, 9000, metadata)
    File "<decorator-gen-455>", line 2, in alpha_rarefaction
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 208, in bound_callable
      self.signature.check_types(**user_input)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/type/signature.py", line 342, in check_types
      name, spec.qiime_type, parameter.type))
  TypeError: Parameter 'max_depth' requires an argument of type Int % Range(1, None). An argument of type Phylogeny[Rooted] was passed.

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/9c/e5e94f76c20c4160a729d422ba09ee
```

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: 6d87ed86ceecb9c24094959ce81b1d580667eef4
slurm sub: 16936472

```bash
Command error:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: Ignoring unknown aesthetics: show.legend 
  3: Removed 4 rows containing missing values (geom_point). 
  4: Removed 4 row(s) containing missing values (geom_path). 
  5: Removed 4 rows containing missing values (geom_point). 
  6: Removed 4 row(s) containing missing values (geom_path). 
  Execution halted
  
  
  processing file: 07_report.Rmd
  -- Attaching packages --------------------------------------- tidyverse 1.3.1 --
  v ggplot2 3.3.5     v purrr   0.3.4
  v tibble  3.1.6     v dplyr   1.0.8
  v tidyr   1.2.0     v stringr 1.4.0
  v readr   2.1.2     v forcats 0.5.1
  -- Conflicts ------------------------------------------ tidyverse_conflicts() --
  x dplyr::filter() masks stats::filter()
  x dplyr::lag()    masks stats::lag()
  
  Attaching package: 'reshape2'
  
  The following object is masked from 'package:tidyr':
  
      smiths
  
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Saving 16 x 10 in image
  Quitting from lines 37-391 (07_report.Rmd) 
  Error in data.frame(..., check.names = FALSE) : 
    arguments imply differing number of rows: 89, 0
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> cbind -> cbind -> data.frame
  In addition: Warning messages:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: Ignoring unknown aesthetics: show.legend 
  3: Removed 4 rows containing missing values (geom_point). 
  4: Removed 4 row(s) containing missing values (geom_path). 
  5: Removed 4 rows containing missing values (geom_point). 
  6: Removed 4 row(s) containing missing values (geom_path). 
  Execution halted

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/56/f9f8332b38728a21b629667cf77197
```

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: a659d62f75c250463cb664549c96a10ee2d4fd88
slurm sub: 16937772

```bash
Attaching package: 'reshape2'
  
  The following object is masked from 'package:tidyr':
  
      smiths
  
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Using sample as id variables
  Saving 16 x 10 in image
  Quitting from lines 40-397 (07_report.Rmd) 
  Error in data.frame(..., check.names = FALSE) : 
    arguments imply differing number of rows: 89, 0
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> cbind -> cbind -> data.frame
  In addition: Warning messages:
  1: In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  2: Ignoring unknown aesthetics: show.legend 
  3: Removed 4 rows containing missing values (geom_point). 
  4: Removed 4 row(s) containing missing values (geom_path). 
  5: Removed 4 rows containing missing values (geom_point). 
  6: Removed 4 row(s) containing missing values (geom_path). 
  Execution halted

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/16/8997be86df45a0fc4ad1dd49211ad9
```

this run was less about getting a result that works and more about getting metadata into a work dir that is accessible. 

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: 5f8155698c89f8bd96a0a47c8d188394a61e111e
slurm sub: 16938521

```bash
success
```

This version of the pipeline is successful.


### Mock Microbial Community

M&Ms might not provide us with exactly what we want (it doesn't learn from environmental samples)
but they might cite a tool that does do it https://www.biorxiv.org/content/10.1101/2021.04.21.440404v1.supplementary-material
This is an ongoing issue for tomorrow.

### Todos for Tomorrow:

- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Examine some papers collected

### Git Commits

#### Lab Notebook

```bash
b0197af - Benjamin Lorentz, Wed Jan 11 13:50:12 2023 -0500 : updates around lunchtime
7286d9d - Ben Lorentz, Wed Jan 11 08:26:08 2023 -0500 :  added notes from first hour
8c10bc8 - Ben Lorentz, Wed Jan 11 07:43:42 2023 -0500 : add page for wednesday
1e4f6ea - Ben Lorentz, Tue Jan 10 17:20:59 2023 -0500 : update git commits
db93696 - Ben Lorentz, Tue Jan 10 17:15:52 2023 -0500 : updates for tuesday
```

#### Visualize Ampliseq

```bash
71810dc - Benjamin Lorentz, Wed Jan 11 15:29:30 2023 -0500 : update main.nf 01_report 01_report_MbA 10_report
5f81556 - Benjamin Lorentz, Wed Jan 11 15:12:16 2023 -0500 : update 07_report.md
a659d62 - Benjamin Lorentz, Wed Jan 11 14:43:03 2023 -0500 : update main.nf 07_report.Rmd
6d87ed8 - Benjamin Lorentz, Wed Jan 11 13:47:30 2023 -0500 : update main.nf 07_report.Rmd
678b7b8 - Benjamin Lorentz, Wed Jan 11 11:51:50 2023 -0500 : update main.nf
eede448 - Benjamin Lorentz, Wed Jan 11 11:42:48 2023 -0500 : update main.nf
d62b704 - Ben Lorentz, Wed Jan 11 08:26:23 2023 -0500 : in progress main.nf
```
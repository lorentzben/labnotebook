---
title: 'Re-Generate Ade Tables'
date: 2023-02-28T13:15:20Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---

### Todos for Today

- Ade 
  - find out what version was last used 
  - send code 
- Stat 6220 
  - Homework 2 (ask prof about last question)
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
  
### Ade

#### Submitting data through new pipeline

cycle 4 rev: 2d3b0a20e2cd74e4a856349977557a915c29673e
slurm subL: 19517282

```bash
N E X T F L O W  ~  version 22.04.5
Specified params file does not exists: /home/bjl34716/ade/cycle-4/ade_params_21.yaml
cp: cannot stat ‘/work/sealab/bjl34716/ade/cycle-4/day-21’: No such file or directory
cp: cannot stat ‘/home/bjl34716/ade/cycle-4/day-21/metadata.tsv’: No such file or directory
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Specified params file does not exists: /home/bjl34716/ade/cycle-4/ade_viz_params_21.yaml
N E X T F L O W  ~  version 22.04.5
Specified params file does not exists: /home/bjl34716/ade/cycle-4/ade_params_28.yaml
cp: cannot stat ‘/work/sealab/bjl34716/ade/cycle-4/day-28’: No such file or directory
cp: cannot stat ‘/home/bjl34716/ade/cycle-4/day-28/metadata.tsv’: No such file or directory
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Already-up-to-date
Specified params file does not exists: /home/bjl34716/ade/cycle-4/ade_viz_params_28.yaml
```

cycle 4 rev: f0c591aff420689cbf7991de616652c25339e891 
slurm sub: 19517389

```bash
ERROR: Please check input samplesheet -> Column 'sampleID' and 'forwardReads' are required but not detected.
```

cycle 4 rev: ab85a4c2b96e180c26baeaa3b7987a308871275b
slurm sub: 19518121

```bash
Please review data input, sampleIDs may not start with a number, but "165FD" does. The pipeline unintentionally modifies such strings and the metadata will not match any more.
```

cycle 4 rev: 053b8b3dec99a62cfb3711f62f039f7370745bd1
slurm sub: 19518410

```bash
 The exit status of the task that caused the workflow execution to fail was: 141

Error executing process > 'NFCORE_AMPLISEQ:AMPLISEQ:DADA2_PREPROCESSING:DADA2_FILTNTRIM (FD166)'

Caused by:
  Process `NFCORE_AMPLISEQ:AMPLISEQ:DADA2_PREPROCESSING:DADA2_FILTNTRIM (FD166)` terminated with an error exit status (141)

Command executed:

  #!/usr/bin/env Rscript
  suppressPackageStartupMessages(library(dada2))
  
  out <- filterAndTrim("FD166_1.fastq.gz", "FD166_1.filt.fastq.gz", "FD166_2.fastq.gz", "FD166_2.filt.fastq.gz",
      truncLen = c(251, 250),
      maxN = 0, truncQ = 2, trimRight = 0, minQ = 0, rm.lowcomplex = 0, orient.fwd = NULL, matchIDs = FALSE, id.sep = "\\s", id.field = NULL, n = 1e+05, OMP = TRUE, qualityType = "Auto",maxEE = c(2, 2),trimLeft = 0, minLen = 50, maxLen = Inf, rm.phix = TRUE,
      compress = TRUE,
      multithread = 6,
      verbose = TRUE)
  out <- cbind(out, ID = row.names(out))
  
  write.table( out, file = "FD166.filter_stats.tsv", sep = "\t", row.names = FALSE, quote = FALSE, na = '')
  write.table(paste('filterAndTrim	truncLen = c(251, 250)','maxN = 0, truncQ = 2, trimRight = 0, minQ = 0, rm.lowcomplex = 0, orient.fwd = NULL, matchIDs = FALSE, id.sep = "\\s", id.field = NULL, n = 1e+05, OMP = TRUE, qualityType = "Auto",maxEE = c(2, 2),trimLeft = 0, minLen = 50, maxLen = Inf, rm.phix = TRUE',sep=","), file = "filterAndTrim.args.txt", row.names = FALSE, col.names = FALSE, quote = FALSE, na = '')
  writeLines(c("\"NFCORE_AMPLISEQ:AMPLISEQ:DADA2_PREPROCESSING:DADA2_FILTNTRIM\":", paste0("    R: ", paste0(R.Version()[c("major","minor")], collapse = ".")),paste0("    dada2: ", packageVersion("dada2")) ), "versions.yml")

Command exit status:
  141

Command output:
  (empty)

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/f5/b365312b61486a8be6112547517152

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line
```


cycle 4 rev: 2ba77405d2882b3ca9730d92a70e1ff71df4dea0
slurm sub: 19519548

```bash
Error executing process > 'NFCORE_AMPLISEQ:AMPLISEQ:QIIME2_BARPLOT (1)'

Caused by:
  Process `NFCORE_AMPLISEQ:AMPLISEQ:QIIME2_BARPLOT (1)` terminated with an error exit status (1)

Command executed:

  export XDG_CONFIG_HOME="${PWD}/HOME"

  qiime taxa barplot          --i-table filtered-table.qza          --i-taxonomy taxonomy.qza          --m-metadata-file day_21_cycle_4_metadata.tsv          --o-visualization taxa-bar-plots.qzv          --verbose
  qiime tools export --input-path taxa-bar-plots.qzv          --output-path barplot

  cat <<-END_VERSIONS > versions.yml
  "NFCORE_AMPLISEQ:AMPLISEQ:QIIME2_BARPLOT":
      qiime2: $( qiime --version | sed -e "s/q2cli version //g" | tr -d '`' | sed -e "s/Run qiime info for more version details.//g" )
  END_VERSIONS

Command exit status:
  1

Command output:
  (empty)
Command error:
  QIIME is caching your current deployment for improved performance. This may take a few moments and should only happen once per deployment.
  Traceback (most recent call last):
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/q2cli/commands.py", line 329, in __call__
      results = action(**arguments)
    File "<decorator-gen-140>", line 2, in barplot
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      outputs = self._callable_executor_(scope, callable_args,
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/qiime2/sdk/action.py", line 453, in _callable_executor_
      ret_val = self._callable(output_dir=temp_dir, **view_args)
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/q2_taxa/_visualizer.py", line 35, in barplot
      raise ValueError('Sample IDs found in the table are missing in the '
  ValueError: Sample IDs found in the table are missing in the metadata: {'P-1000149'}.

  Plugin error from taxa:

    Sample IDs found in the table are missing in the metadata: {'P-1000149'}.

  See above for debug info.

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/6c/c9999a02d25b79263c1da369c08b62

Tip: view the complete command output by changing to the process work dir and entering the command `cat .command.out` 
```
```

There is an issue with the feature table 

cycle 4 rev: dae05a5b614cb05f094d21c4e069e53b142bddb3
slurm sub: 19520711

```bash
No such file: /scratch/bjl34716/ade/cycle-4/day-21/metadata.tsv
```

cycle 4 rev: 7bcc1534e241b6e38903ac820f54f1dd30a8de75
slurm sub: 19521830

```bash
Command error:
  
  
  processing file: 01_report_MbA.Rmd
  Loading required package: phyloseq
  
  Attaching package: 'dplyr'
  
  The following objects are masked from 'package:stats':
  
      filter, lag
  
  The following objects are masked from 'package:base':
  
      intersect, setdiff, setequal, union
  
  Quitting from lines 38-112 (01_report_MbA.Rmd) 
  Error in mbSetObj$dataSet : $ operator is invalid for atomic vectors
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> SanityCheckData -> apply
  In addition: There were 33 warnings (use warnings() to see them)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/5d/ea3d500e27a0f4172d5e0fcb6c1f73
```


```r
> new_metadata
   sample.id     Age      Litter   Infection  Extraction   Treatment  X X.1 X.2
1  #q2:types numeric categorical categorical categorical categorical NA  NA  NA
2      165FD      21       FRESH          NO        FAST   FRESHCTRL NA  NA  NA
3      166FD      21       FRESH          NO        FAST   FRESHCTRL NA  NA  NA
4      172FD      21       FRESH          NO        FAST   FRESHCTRL NA  NA  NA
5      173FD      21       FRESH          NO        FAST   FRESHCTRL NA  NA  NA
6      174FD      21       FRESH          NO        FAST   FRESHCTRL NA  NA  NA
7       150P      21       FRESH         YES        POWR    FRESHINF NA  NA  NA
8       151P      21       FRESH         YES        POWR    FRESHINF NA  NA  NA
9      157FD      21       FRESH         YES        FAST    FRESHINF NA  NA  NA
10     158FD      21       FRESH         YES        FAST    FRESHINF NA  NA  NA
11     159FD      21       FRESH         YES        FAST    FRESHINF NA  NA  NA
12     167FD      21        CYC1          NO        FAST   CYCL1CTRL NA  NA  NA
13     168FD      21        CYC1          NO        FAST   CYCL1CTRL NA  NA  NA
14     169FD      21        CYC1          NO        FAST   CYCL1CTRL NA  NA  NA
15     170FD      21        CYC1          NO        FAST   CYCL1CTRL NA  NA  NA
16      171P      21        CYC1          NO        POWR   CYCL1CTRL NA  NA  NA
17      152P      21        CYC1         YES        POWR    CYCL1INF NA  NA  NA
18      153P      21        CYC1         YES        POWR    CYCL1INF NA  NA  NA
19      154P      21        CYC1         YES        POWR    CYCL1INF NA  NA  NA
20      155P      21        CYC1         YES        POWR    CYCL1INF NA  NA  NA
21     156FD      21        CYC1         YES        FAST    CYCL1INF NA  NA  NA
22      160P      21        CYC3          NO        POWR   CYCL3CTRL NA  NA  NA
23     161FD      21        CYC3          NO        FAST   CYCL3CTRL NA  NA  NA
24      162P      21        CYC3          NO        POWR   CYCL3CTRL NA  NA  NA
25     163FD      21        CYC3          NO        FAST   CYCL3CTRL NA  NA  NA
26     164FD      21        CYC3          NO        FAST   CYCL3CTRL NA  NA  NA
27     145FD      21        CYC3         YES        FAST    CYCL3INF NA  NA  NA
28     146FD      21        CYC3         YES        FAST    CYCL3INF NA  NA  NA
29      147P      21        CYC3         YES        POWR    CYCL3INF NA  NA  NA
30     148FD      21        CYC3         YES        FAST    CYCL3INF NA  NA  NA
31      149P      21        CYC3         YES        POWR    CYCL3INF NA  NA  NA
   X.3 X.4 X.5 X.6 X.7 X.8
1   NA  NA  NA  NA  NA  NA
2   NA  NA  NA  NA  NA  NA
3   NA  NA  NA  NA  NA  NA
4   NA  NA  NA  NA  NA  NA
5   NA  NA  NA  NA  NA  NA
6   NA  NA  NA  NA  NA  NA
7   NA  NA  NA  NA  NA  NA
8   NA  NA  NA  NA  NA  NA
9   NA  NA  NA  NA  NA  NA
10  NA  NA  NA  NA  NA  NA
11  NA  NA  NA  NA  NA  NA
12  NA  NA  NA  NA  NA  NA
13  NA  NA  NA  NA  NA  NA
14  NA  NA  NA  NA  NA  NA
15  NA  NA  NA  NA  NA  NA
16  NA  NA  NA  NA  NA  NA
17  NA  NA  NA  NA  NA  NA
18  NA  NA  NA  NA  NA  NA
19  NA  NA  NA  NA  NA  NA
20  NA  NA  NA  NA  NA  NA
21  NA  NA  NA  NA  NA  NA
22  NA  NA  NA  NA  NA  NA
23  NA  NA  NA  NA  NA  NA
24  NA  NA  NA  NA  NA  NA
25  NA  NA  NA  NA  NA  NA
26  NA  NA  NA  NA  NA  NA
27  NA  NA  NA  NA  NA  NA
28  NA  NA  NA  NA  NA  NA
29  NA  NA  NA  NA  NA  NA
30  NA  NA  NA  NA  NA  NA
31  NA  NA  NA  NA  NA  NA
```

There is some weird padding around the metadata, I went into visualize ampliseq and updated them.

visualize ampliseq rev: EXPECTED but not used 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
cycle 4 rev: 7bcc1534e241b6e38903ac820f54f1dd30a8de75
slurm sub: 19522402

```bash
Command error:
  
  
  processing file: 01_report_MbA.Rmd
  Loading required package: phyloseq
  
  Attaching package: 'dplyr'
  
  The following objects are masked from 'package:stats':
  
      filter, lag
  
  The following objects are masked from 'package:base':
  
      intersect, setdiff, setequal, union
  
  Quitting from lines 38-112 (01_report_MbA.Rmd) 
  Error in mbSetObj$dataSet : $ operator is invalid for atomic vectors
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> SanityCheckData -> apply
  In addition: There were 33 warnings (use warnings() to see them)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/3a/e286a5c63062c3d719c9a89f738782

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line
```

visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
cycle 4 rev: 44734efb931e4965db37ffc7f780990d97051048
slurm sub: 19522585

```bash
Command error:
  
  
  processing file: 01_report_MbA.Rmd
  Loading required package: phyloseq
  
  Attaching package: 'dplyr'
  
  The following objects are masked from 'package:stats':
  
      filter, lag
  
  The following objects are masked from 'package:base':
  
      intersect, setdiff, setequal, union
  
  Quitting from lines 38-113 (01_report_MbA.Rmd) 
  Error in `*tmp*`$dataSet : $ operator is invalid for atomic vectors
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> ApplyAbundanceFilter
  In addition: There were 37 warnings (use warnings() to see them)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/e8/58b4159ca4dd45fd103d1ff3fbc05a
```


#### Submitting data through old revision of pipeline

### Todos for Tomorrow

- Ade 
  - why is visualize ampliseq failing out?
  - set up the old pipeline analysis to send the feature table over
  - find out what version was last used 
  - send code 
- Stat 6220 
  - Review for Midterm
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Git Commits

#### Lab Notebook

```bash
f702ecf - Benjamin Lorentz, Tue Feb 28 08:17:35 2023 -0500 : added page for tuesday
8e67f82 - Benjamin Lorentz, Tue Feb 28 08:14:01 2023 -0500 : added note from monday evening
```

#### Visualize Ampliseq

```bash
6282c8e - Benjamin Lorentz, Tue Feb 28 16:23:19 2023 -0500 : update 01_report_MbA.Rmd
```

#### cycle 4 

```bash
7bcc153 - Benjamin Lorentz, Tue Feb 28 15:31:51 2023 -0500 : update ade-cycle-4-nextflow.sh
dae05a5 - Benjamin Lorentz, Tue Feb 28 13:59:03 2023 -0500 : update day 21 mapping file
2ba7740 - Benjamin Lorentz, Tue Feb 28 12:41:05 2023 -0500 : update params 21 and 28
053b8b3 - Benjamin Lorentz, Tue Feb 28 11:37:41 2023 -0500 : update mapping and metadata sheets
ab85a4c - Benjamin Lorentz, Tue Feb 28 11:23:53 2023 -0500 : add nextflow metadata and update param files
f0c591a - Benjamin Lorentz, Tue Feb 28 10:58:30 2023 -0500 : update ade-cycle-4-nextflow
2d3b0a2 - lorentzben, Tue Feb 28 10:53:30 2023 -0500 : dos2unix
aeeabf3 - Benjamin Lorentz, Tue Feb 28 10:54:24 2023 -0500 : add ade params 28
edb5bb2 - Benjamin Lorentz, Tue Feb 28 10:53:04 2023 -0500 : add ade vis param sheets
9de5ce6 - Benjamin Lorentz, Tue Feb 28 10:50:42 2023 -0500 : added ade_viz_parameters
4b0e64b - Benjamin Lorentz, Tue Feb 28 10:21:18 2023 -0500 : add day 21 and 28 metadata and mapping files
```
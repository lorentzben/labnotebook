---
title: 'Filtering Mock Nc'
date: 2023-05-04T13:32:09Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
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

SRS Normalize:

Yes SRS Yes NC Mock:
  - MOCK.tsv

Yes SRS Yes NC: 
  - NC.tsv

Yes SRS:
  - SRSNORMALIZE.out.biom_normalized
  
Yes NC: 
  - NC.tsv

Yes Mock:
  - Mock.tsv

No SRS No Mock No NC:
 - results/qiime2/abundance_tables/feature-table.biom

We need to figure out what channel should be passed in:

raw_qza_table = []
raw_tsv_table = []

filtered_qza_table = []
filtered_tsv_table = []

testing raw_tsv_table_ch:

cycle 4 rev:
visualize ampliseq rev: ba229b6e6ccffa8b72faa7af813c7edfc2002a77
slurm sub: 21972857

```bash
No such variable: qza_table

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 119 or see '.nextflow.log' file for more details
[-        ] process > ORDERIOI              -
[-        ] process > FILTERNEGATIVECONTROL -

```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: fc9d3a7d8ab02f6a40d168f7132d5467ed30b31a
slurm sub: 21972959

```bash
[-        ] process > REPORT12PERMANOVA              -
No such variable: qza_table

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 156 or see '.nextflow.log' file for more details

```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: f618fe7320d7b2864d3d921d2edaca323738b8f7
slurm sub: 21973029

```bash
Work dir:
  /scratch/bjl34716/ade/cycle-4/work/35/18f2f933a890f679ea8039dfeebe0d

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`


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
In readLines("/scratch/bjl34716/ade/cycle-4/work/f1/1743756e06386b6a6330812641bf22/srs_min_curve_val.txt") :
  incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/f1/1743756e06386b6a6330812641bf22/srs_min_curve_val.txt'
Error in colSums(data) : 'x' must be numeric
Calls: SRS -> colSums
Execution halted`, size: 714 (max: 255)
```
```

We'll come back to this issue...

We want to check that the correct table is being read in first. 

```bash
bjl34716@ss-sub1 srs-test$ head /scratch/bjl34716/ade/cycle-4/litter-srs/qiime2/abundance_tables/feature-table.tsv
# Constructed from biom file
#OTU ID LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109   LT110   LT111   LT112   LT113   LT114 LT115    LT116   LT117   LT118   LT119   LT120   LT73    LT74    LT75    LT76    LT77    LT78    LT79 ,   LT80    LT81    LT82  LT83     LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95    LT96    LT97    LT98    LT99  MOCK167  MOCK288 MOCK323 MOCK71  NC168   NC287   NC324   NC72
7b9c8d4a1896d84d92ab4820edd025a6        36.0    60.0    395.0   372.0   277.0   0.0     536.0   43.0    38.0    749.0   519.0 558.0    1070.0  22.0    14.0    808.0   177.0   434.0   418.0   68.0    54.0    0.0     469.0   467.0   549.0   12.0    0.0   242.0    305.0   245.0   302.0   0.0     10.0    601.0   663.0   873.0   694.0   68.0    0.0     360.0   298.0   505.0   41.0  0.0      0.0     838.0   820.0   0.0     0.0     0.0     0.0     0.0     0.0     0.0     0.0
```

test the tsv and qza processes:

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: f114b8f10db8cf147bbcea288f8da39abe3124c7
slurm sub: 21975238

```bash
/scratch/bjl34716/ade/cycle-4/work/f8/660a3ceda607e3ad81a093d5f234bc/raw_table_MbA.tsv
/scratch/bjl34716/ade/cycle-4/work/f8/660a3ceda607e3ad81a093d5f234bc/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/6f/bef95f42cf75a451c8fe98cd62adee/raw-feature-table.qza
```
SRSNORMALIZE

docker://lorentzb/srs:1.0

/scratch/bjl34716/ade/cycle-4/work/e7/d5fdc2c067d77110203d5b82f2b6c9

```r
> library(qiime2R)
library(SRS)
    library(phyloseq)
    library(biomformat)
> filt <- read.table('filtered-table.tsv')
> biom <- read_q2biom("results/qiime2/abundance_tables/feature-table.biom")
Error in read_q2biom("results/qiime2/abundance_tables/feature-table.biom") :
  could not find function "read_q2biom"
> sum(sort(rownames(biom)) == sort(rownames(filt)))
[1] 1742
> dim(biom)
[1] 1742   55

```

GENERATEBIOMFORGRAPHLAN

COREMETRICPYTHON

This is run no matter what, but we need to pull in the norm table from srs if that is used.

TODO test this function:

```python
if(os.path.exists($table):
        print("$table exists")
    else: 
        unrarefied_table = Artifact.load('table.qza')
```

Quick integration test

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: c5a8cfd572db8a227ba25489513a4f63edcc3506
slurm sub: 21993266

```bash
[-        ] process > ORDERIOI -
Process 'QIIME2_EXPORT_ABSOLUTE' has been already used -- If you need to reuse the same component include it with a different name or include in a different workflow context

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 114 or see '.nextflow.log' file for more details
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: b84d63fc8b764fd6dffd97bf62894761d4733512
slurm sub: 21993413

```bash
Command error:
    import pandas.util.testing as pdt
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Plugin error from taxa:
  
    Please provide a DataFrame with a string-based Index
  
  Debug info has been saved to /tmp/qiime2-q2cli-err-qbhxz9ov.log
  Usage: qiime tools export [OPTIONS]
  
    Exporting extracts (and optionally transforms) data stored inside an
    Artifact or Visualization. Note that Visualizations cannot be transformed
    with --output-format
  
  Options:
    --input-path ARTIFACT/VISUALIZATION
                          Path to file that should be exported        [required]
    --output-path PATH    Path to file or directory where data should be
                          exported to                                 [required]
    --output-format TEXT  Format which the data should be exported as. This
                          option cannot be used with Visualizations
    --help                Show this message and exit.
  
                      There was a problem with the command:                     
   (1/1) Invalid value for '--input-path': File 'collapse-NC-table.qza' does not
    exist.
  Usage: biom convert [OPTIONS]
  Try 'biom convert -h' for help.
  
  Error: Invalid value for '-i' / '--input-fp': File 'collapse-NC-frequency/feature-table.biom' does not exist.
  Traceback (most recent call last):
    File ".command.sh", line 43, in <module>
      table = pd.read_table("otu-"+str(item)+"-table.tsv", sep='	', header=1)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 767, in read_table
      return read_csv(**locals())
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 688, in read_csv
      return _read(filepath_or_buffer, kwds)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 454, in _read
      parser = TextFileReader(fp_or_buf, **kwds)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 948, in __init__
      self._make_engine(self.engine)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 1180, in _make_engine
      self._engine = CParserWrapper(self.f, **self.options)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 2010, in __init__
      self._reader = parsers.TextReader(src, **kwds)
    File "pandas/_libs/parsers.pyx", line 382, in pandas._libs.parsers.TextReader.__cinit__
    File "pandas/_libs/parsers.pyx", line 674, in pandas._libs.parsers.TextReader._setup_parser_source
  FileNotFoundError: [Errno 2] No such file or directory: 'otu-NC-table.tsv'

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/64/4fabdb92c96a6db886519312d46b7f
```

It's trying to check the metadata for NC and MOCK but they don't exist how did we remove metadata 
cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: e642a754c776bead0e55109060b9c1db81eb261b 
slurm sub: 21994338

```bash
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
  In readLines("/scratch/bjl34716/ade/cycle-4/work/e0/a3219b4b1f572d6e580a5e61a617de/srs_min_curve_val.txt") :
    incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/e0/a3219b4b1f572d6e580a5e61a617de/srs_min_curve_val.txt'
  Error in colSums(data) : 'x' must be numeric
  Calls: SRS -> colSums
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/96/b4e45be326838d480c8848050c635e
```

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

We have to go in and fix the filer script :/

#### Unit testing:

Here is the nf-core test data location

https://github.com/nf-core/test-datasets/tree/ampliseq

### Todos for Tomorrow

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
  
### Git Commit

#### Lab Notebook

```bash
2638860 - Benjamin Lorentz, Thu May 4 11:55:29 2023 -0400 : added notes before lunch
```

#### Visualize Ampliseq

```bash
4e00388 - Benjamin Lorentz, Thu May 4 17:07:37 2023 -0400 : update main and contam_script.r
e642a75 - Benjamin Lorentz, Thu May 4 16:53:20 2023 -0400 : update main.nf
b84d63f - Benjamin Lorentz, Thu May 4 16:34:07 2023 -0400 : update main.nf
c5a8cfd - Benjamin Lorentz, Thu May 4 16:28:14 2023 -0400 : update main.nf and my_count_table_min_max.py
f114b8f - Benjamin Lorentz, Thu May 4 11:30:42 2023 -0400 : update main.nf
f618fe7 - Benjamin Lorentz, Thu May 4 10:44:17 2023 -0400 : update main.nf
fc9d3a7 - Benjamin Lorentz, Thu May 4 10:42:02 2023 -0400 : update main.nf
ba229b6 - Benjamin Lorentz, Thu May 4 10:12:15 2023 -0400 : some updates for main.nf and 01_report_Mba
```

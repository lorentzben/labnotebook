---
title: 'Longitudinal Study'
date: 2023-06-01T13:16:10Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "Mock"
  - "Module"
  - "primer-detect"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Longitudinal Analysis By hand
    - Check out slurm 23139002
  - Email Dr. Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Ade

#### Longitudinal Analysis By hand

Check out slurm 23139002

cycle 4 rev: 681d1bd138828175a89c9c9b8a904f56c0f9d906
visualize ampliseq rev: d8cfbe9871bfd3ae8add451c7547e0475a91e167
slurm job: 23139002

```bash
Command exit status:
  1

Command output:
  Saved FeatureTable[Frequency] to: FRESHINF28-filtered-table.qza
  Saved FeatureTable[Frequency] to: collapse-FRESHINF28-table.qza
  Exported collapse-FRESHINF28-table.qza as BIOMV210DirFmt to directory collapse-FRESHINF28-frequency/
  Saved FeatureTable[Frequency] to: FRESHINF0-filtered-table.qza

Command error:
    import pandas.util.testing as pdt
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Plugin error from taxa:
  
    Please provide a DataFrame with a string-based Index
  
  Debug info has been saved to /tmp/qiime2-q2cli-err-of5g9aim.log
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
   (1/1) Invalid value for '--input-path': File 'collapse-FRESHINF0-table.qza'
    does not exist.
  Usage: biom convert [OPTIONS]
  Try 'biom convert -h' for help.
  
  Error: Invalid value for '-i' / '--input-fp': File 'collapse-FRESHINF0-frequency/feature-table.biom' does not exist.
  Traceback (most recent call last):
    File ".command.sh", line 46, in <module>
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
  FileNotFoundError: [Errno 2] No such file or directory: 'otu-FRESHINF0-table.tsv'

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/23/45136fe66ebeff567e93bc024c47e4
```

Don't forget to rm -rf /scratch/bjl34716/ade/cycle-4/litter-figaro-nc-mock-srs-viz-all-sample

Check my rarefaction depth level:

I chose new 10,000

```md
LT114	102001
LT113	95729
LT101	67105
LT112	65792
LT108	64948
LT99	64816
LT89	64241
LT106	61219
LT87	60412
LT115	60158
LT111	57570
LT109	55301
LT98	55032
LT120	53947
LT42	53718
LT95	53386
LT93	53373
LT118	52632
LT85	52062
LT50	49377
LT100	49347
LT103	49230
LT102	49182
MOCK323	49150
LT86	48479
LT88	46482
LT117	45902
LT110	45400
LT52	43953
LT107	43829
LT104	42135
LT119	41908
LT54	41885
LT91	41304
LT38	40229
NC168	40119
NC287	39372
LT90	36425
LT92	36028
LT39	34973
LT51	34955
LT76	34074
LT74	32447
LT53	31683
LT78	31167
LT2	30540
LT44	30239
LT77	30188
LT80	29413
LT33	29374
LT40	29334
LT30	28870
LT13	28155
LT15	28082
LT47	27786
LT10	27697
LT84	27089
LT41	26454
LT7	25273
LT82	25140
LT14	25085
LT36	24962
LT48	24824
LT60	24809
LT66	24704
LT49	24616
LT22	24292
LT25	23936
LT79	23414
LT65	23339
LT43	23324
LT68	23321
LT64	22826
LT3	22361
LT55	22294
LT19	22282
LT75	22270
LT1	21469
LT16	20685
LT21	20655
LT28	20489
LT45	20259
LT81	19875
LT4	19848
LT67	19610
LT62	19582
LT27	19514
LT56	19385
LT9	19333
LT59	19191
LT58	19117
LT57	18785
LT72	18147
LT32	17786
LT29	17357
LT31	16980
LT116	16814
LT20	16275
LT63	15895
LT46	14998
LT69	14959
LT70	14958
LT34	14921
LT8	13125
LT35	12678
***MOCK71	10918***
LT5	5434
LT17	5215
LT96	2933
LT24	2596
MOCK288	2338
LT71	2271
LT6	2069
LT12	1991
LT23	1505
LT18	1308
LT11	1070
NC72	337
NC324	208
LT105	111
MOCK167	59
LT37	31
LT26	25
LT97	25
LT61	8
LT73	6
LT83	4
```

cycle 4 rev: 2068d8b3d18e3c2271bd0586a8aef4cebaa5bbb0
visualize ampliseq rev: 89f6beb3c8284c41fe3c5851b4a97b139b463c4c
slurm job: 23151598

```bash
 (1/1) Invalid value for '--input-path': File 'collapse-FRESHCTRL0-table.qza'
  does not exist.
Usage: biom convert [OPTIONS]
Try 'biom convert -h' for help.

Error: Invalid value for '-i' / '--input-fp': File 'collapse-FRESHCTRL0-frequency/feature-table.biom' does not exist.
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/53/b57879df6de47d425767d44f267ea4/.command.sh", line 50, in <module>
    table = pd.read_table("otu-"+str(item)+"-table.tsv", sep='  ', header=1)
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
FileNotFoundError: [Errno 2] No such file or directory: 'otu-FRESHCTRL0-table.tsv'`, size: 3067 (max: 255)

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/53/b57879df6de47d425767d44f267ea4
```


cycle 4 rev: 2068d8b3d18e3c2271bd0586a8aef4cebaa5bbb0
visualize ampliseq rev: 3f5b05ffd4b81741d401a1c9055706ca459709e0
slurm job: 23152718

```bash

Command exit status:
  1

Command output:
  (empty)

Command error:
  Traceback (most recent call last):
    File ".command.sh", line 14, in <module>
      ioi_set.discard("NC")
  NameError: name 'ioi_set' is not defined

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/65/46439094e1b5ede9b23fd7382473f5
```


cycle 4 rev: 2068d8b3d18e3c2271bd0586a8aef4cebaa5bbb0
visualize ampliseq rev: de88954bb71d619fcb5cccf23db14c5f912dcf25
slurm job: 23153671

```bash
 label: ANOSIM analysis (with options)
  List of 5
   $ echo      : logi FALSE
   $ fig.height: num 8
   $ fig.width : num 10
   $ message   : logi FALSE
   $ warning   : logi FALSE


Command error:
  ✖ dplyr::filter()     masks stats::filter()
  ✖ dplyr::lag()        masks stats::lag()
  ✖ tidyr::pack()       masks Matrix::pack()
  ✖ dplyr::select()     masks MASS::select()
  ✖ tidyr::unpack()     masks Matrix::unpack()

  Attaching package: 'rstatix'

  The following object is masked from 'package:MASS':

      select

  The following object is masked from 'package:stats':

      filter
      Attaching package: 'kableExtra'

  The following object is masked from 'package:dplyr':

      group_rows


  Attaching package: 'ggpubr'

  The following object is masked from 'package:qiime2R':

      mean_sd

  Loading required package: permute

  Attaching package: 'permute'

  The following object is masked from 'package:gtools':

      permute

  The following object is masked from 'package:deldir':

      getCol

  Loading required package: lattice
  This is vegan 2.6-2
  Quitting from lines 356-455 (12_report.Rmd)
   Error in cl.vec[within] <- levels(grouping)[grouping[take]] :
    NAs are not allowed in subscripted assignments
  Calls: <Anonymous> ... withVisible -> eval_with_user_handlers -> eval -> eval -> anosim
  In addition: There were 50 or more warnings (use warnings() to see the first 50)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c3/bbe97f162031075d50196a299a282f
```

Something is wrong here...

#### Email Dr. Ade

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - fix report 12 from 356-455 (12_report.Rmd)
  - Longitudinal Analysis By hand
    - Check out slurm 23139002
  - Email Dr. Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Git Commit

#### Lab Notebook

```bash
db06bd2 - Benjamin Lorentz, Thu Jun 1 09:20:42 2023 -0400 : inital page for Thursday
```

#### Cycle 4

```bash
2068d8b - Benjamin Lorentz, Thu Jun 1 10:11:19 2023 -0400 : update viz params all samples
```

#### Visualize Ampliseq

```bash
de88954 - Benjamin Lorentz, Thu Jun 1 15:58:50 2023 -0400 : update generate biom for graphlan \n - move vars to correct place
3f5b05f - Benjamin Lorentz, Thu Jun 1 15:13:37 2023 -0400 : update generatebiomforgraphlan
89f6beb - Benjamin Lorentz, Thu Jun 1 14:08:18 2023 -0400 : update generatebiomgraphlan and visualize-ampliseq
```
  
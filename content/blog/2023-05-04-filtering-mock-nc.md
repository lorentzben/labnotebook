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


GENERATEBIOMFORGRAPHLAN

Report 01


#### Unit testing:

Here is the nf-core test data location

https://github.com/nf-core/test-datasets/tree/ampliseq
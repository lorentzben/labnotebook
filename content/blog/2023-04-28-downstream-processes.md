---
title: 'Downstream Processes'
date: 2023-04-28T14:24:57Z
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
  - Paper finalize
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - Yes NC Yes SRS
     - Yes NC no SRS
     - No NC Yes SRS
     - No NC No SRS
  - Tamura optmization for richness?
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
- Check out https://youtu.be/oBfu3prR5FA


### Ade

###### Downstream Analysis

Make sure each report pulls in the proper table.

Yes Nc and Yes SRS 

if you need a tsv normalized version: SRSNORMALIZE.out.tsv_normalized
if you need a qza normalized version: norm_qza_table (with 0s), or COREMETRICPYTHON.out.rare_table (no 0s)

Report 01

tsv filtered nc but not normalized: FILTERNEGATIVECONTROL.out.filtered_table_tsv
qza filtered nc but not normalized: qza_table


What is in the Report01 folder for no SRS no NC?:

```bash
ls /scratch/bjl34716/ade/cycle-4/work/04/39a8161b7715c92ea64f5fe8687304

filtered-table.tsv is not present
```

We need to make the NC/NC check and then just make sure the right one is passed through

I think all set for 01: uses the NC filtered table :)

Report 02

Uses the correctly filtered table to generate the bioms

Report 03

Pulls in the coremetric python rare table, which should be okay.

Report 04

Comes out of QZATOTSV -> COREMETRICPYTHON.out.vector 

This takes in the normalized table so we're good

Report 05

Comes out of QZATOTSV -> COREMETRICPYTHON.out.vector 

This takes in the normalized table so we're good

Report 06

This pulls in COREMETRICPYTHON.out.rare_table and the coremetricpython qzas

Report 07

Not relevant since we are using SRS curve

Report 08

Also pulls in the coremetric python raretable 

Report 09

Pulls in the coremetric distance so it looks good

Report 10

coremetric python -> Report 10

Looks good

Report 11

Takes in the python rarefaction table 

Looks good

Report 12

Pulls in the rarefied table so its correct

Report 13

We are pulling in the non-normalized filterd file so we are good. 

#### SRS but no control

Check that results/qiime2/abundance_tables/feature-table.biom counts is the same as the dada2 table

```r
library(biomformat)
library(qiime2R)
library(tidyverse)

> list.files()
 [1] "abs-abund-table-2.tsv"        "abs-abund-table-3.tsv"
 [3] "abs-abund-table-4.tsv"        "abs-abund-table-5.tsv"
 [5] "abs-abund-table-6.tsv"        "abs-abund-table-7.tsv"
 [7] "count_table_filter_stats.tsv" "feature-table.biom"
 [9] "feature-table.tsv"            "filtered-table.qza"
 
tsv_table <- read_tsv('qiime2/abundance_tables/feature-table.tsv',skip=1)
cols <- dim(tsv_table)[2]

#TSV table 

> colSums(tsv_table[,2:cols])
 LT100  LT101  LT102  LT103  LT104  LT106  LT107  LT108  LT109  LT110  LT111
 48747  66434  48411  48550  41524  60339  43101  64002  54540  44800  56880
 LT112  LT113  LT114  LT115  LT116  LT117  LT118  LT119  LT120   LT74   LT75
 64693  94508 100712  59075  16500  45227  51696  40982  52901  31768  21874
  LT76   LT77   LT78   LT79   LT80   LT81   LT82   LT84   LT85   LT86   LT87
 33526  29821  30551  23060  28657  19474  24690  26625  51320  47709  59664
  LT88   LT89   LT90   LT91   LT92   LT93   LT95   LT98   LT99
 45949  63460  35688  40683  35298  52512  52153  54424  64062
 
 
> biom_table <- read_biom('qiime2/abundance_tables/feature-table.biom')

> colSums(as(biom_data(biom_table),"matrix"))
 LT100  LT101  LT102  LT103  LT104  LT106  LT107  LT108  LT109  LT110  LT111
 48747  66434  48411  48550  41524  60339  43101  64002  54540  44800  56880
 LT112  LT113  LT114  LT115  LT116  LT117  LT118  LT119  LT120   LT74   LT75
 64693  94508 100712  59075  16500  45227  51696  40982  52901  31768  21874
  LT76   LT77   LT78   LT79   LT80   LT81   LT82   LT84   LT85   LT86   LT87
 33526  29821  30551  23060  28657  19474  24690  26625  51320  47709  59664
  LT88   LT89   LT90   LT91   LT92   LT93   LT95   LT98   LT99
 45949  63460  35688  40683  35298  52512  52153  54424  64062
 
> biom_colsum <- colSums(as(biom_data(biom_table),"matrix"))
> tsv_colsum <- colSums(tsv_table[,2:cols])

> tsv_colsum == biom_colsum
LT100 LT101 LT102 LT103 LT104 LT106 LT107 LT108 LT109 LT110 LT111 LT112 LT113
 TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
LT114 LT115 LT116 LT117 LT118 LT119 LT120  LT74  LT75  LT76  LT77  LT78  LT79
 TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
 LT80  LT81  LT82  LT84  LT85  LT86  LT87  LT88  LT89  LT90  LT91  LT92  LT93
 TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
 LT95  LT98  LT99
 TRUE  TRUE  TRUE
 
> biom_rowsum <- rowSums(as(biom_data(biom_table),"matrix"))
> tsv_rowsum <- rowSums(tsv_table[,2:cols])

> tsv_rowsum == biom_rowsum
list
> sum(tsv_rowsum == biom_rowsum)
[1] 988
> dim(tsv_table)
[1] 988  43

dada2_table <- read_tsv('dada2/ASV_table.tsv')
dada2_cols <- dim(dada2_table)[2]
dada2_colsum <- colSums(dada2_table[,2:dada2_cols])
dada2_rowsum <- rowSums(dada2_table[,2:dada2_cols])

> dim(tsv_table)
[1] 988  43

> dim(dada2_table)
[1] 1390   43

sum(tsv_rowsum == dada2_rowsum)
sum(tsv_colsum == dada2_colsum)

> sum(sort(tsv_rowsum, decreasing=T) == dada2_rowsum)
[1] 1280
Warning message:
In sort(tsv_rowsum, decreasing = T) == dada2_rowsum :
  longer object length is not a multiple of shorter object length
  
```

Filtering does happen in ampliseq between dada2 and qiime tables which is why we see higher frequency. So the ones we want come from the qiime folder.

non-normalized TSV will come from: results/qiime2/abundance_tables/feature-table.tsv
non-normalized QZA will come from: GENERATEBIOMFORGRAPHLAN.out."feature-table.qza" (results/qiime2/abundance_tables/feature-table.biom)

normalized-tsv comes from: SRSNORMALIZE.out.tsv_normalized
normalized-qza comes from: norm_qza_table = TSVTOQZA2.out.qza.map{it.last()}

Report 01

We double checked that the path is correct: 
"qiime2/abundance_tables/feature-table.tsv"

Report 02

Also reads in the correct table passing in empty lists to make readability a little better:
results/qiime2/abundance_tables/feature-table.biom

Report 03

Pulls in the table from coremetric python rarefaction

Report 04

Pulls in coremetric vectors

Report 05

Pulls in coremetric vectors

Report 06

Pulls in 'rarefied table' from coremetric python

Report 07

SRS curve 

Report 08

Takes in coremetric pythons raretable

Report 09

Takes coremetrics distance matricies

Report 10

Pulls in distance matricies from coremetric

Report 11

Uses coremetrics rare table

Report 12

takes in coremetrics rare table

Report 13

Uses the unnormalized table


#### No SRS control

#### No SRS no control

#### If we don't provide a raredepth:

Does the coremetric and SRS use the same depth? (so same table)
### Unit testing:

Here is the nf-core test data location

https://github.com/nf-core/test-datasets/tree/ampliseq
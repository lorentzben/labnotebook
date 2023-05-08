---
title: 'Continue Module Migration'
date: 2023-05-08T13:46:58Z
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
  
### Ade 

#### Making a Subworkflow

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 35dc5414abb52c4404c16971fd082705c23de4b3
slurm sub: 22203082

```bash
Completed at: 08-May-2023 11:47:23
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 9

There is a filtered tsv table
```

cycle 4 rev: cec637d6283e3ca0680616301127510660acf4aa
visualize ampliseq rev: 35dc5414abb52c4404c16971fd082705c23de4b3
slurm sub: 22203628

```bash
Completed at: 08-May-2023 11:51:09
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 3

There is a filtered tsv table
```

cycle 4 rev: cec637d6283e3ca0680616301127510660acf4aa
visualize ampliseq rev: 657ccffa31e8191ff008364197ab7a59c3b2a520
slurm sub: 

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [peaceful_laplace] DSL2 - revision: 657ccffa31 [srs]
Module compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/srscurve.nf
- cause: Unexpected input: '{' @ line 1, column 17.
   process SRSCURVE{
                   ^

1 error
```

cycle 4 rev: cec637d6283e3ca0680616301127510660acf4aa
visualize ampliseq rev: 3ef8979142edb14783cec719d0c16bf3c4d71db2
slurm sub: 22220737

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [intergalactic_jepsen] DSL2 - revision: 3ef8979142 [srs]
Module compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/srscurve.nf
- cause: Unexpected input: '{' @ line 1, column 17.
   process SRSCURVE{
                   ^

1 error
```


cycle 4 rev: cec637d6283e3ca0680616301127510660acf4aa
visualize ampliseq rev: c497ec20fc245491dcb6e037fbb335621ab33ea8 
slurm sub: 22221200

```bash
Completed at: 08-May-2023 13:52:58
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 3
no normalization with SRS
```


cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: c497ec20fc245491dcb6e037fbb335621ab33ea8 
slurm sub: 22221339

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Already-up-to-date
Launching `https://github.com/lorentzben/visualize-ampliseq` [suspicious_wilson] DSL2 - revision: c497ec20fc [srs]
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
Unknown process directive: `_out_file`

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/srscurve.nf' at line: 19 or see '.nextflow.log' file for more details
```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: fdfab57883baa164c6e377afc55a49176d060dc3 
slurm sub: 22221722

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
  In readLines("/scratch/bjl34716/ade/cycle-4/work/f2/393f6123db4b1e3966950bb4fb784e/srs_min_curve_val.txt") :
    incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/f2/393f6123db4b1e3966950bb4fb784e/srs_min_curve_val.txt'
  Error in colSums(data) : 'x' must be numeric
  Calls: SRS -> colSums
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/ef/02dd8f6cc9a7ec5079709fbe3e5d34
```

The table in SRS Curve:

```bash
# Constructed from biom file
#OTU ID LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109   LT110   LT111   LT112   LT113   LT114 LT115    LT116   LT117   LT118   LT119   LT120   LT73    LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82  LT83     LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95    LT96    LT97    LT98    LT99
8c9012e5e1fa2e6ec131de357794b220 
```


cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: d959e171172e677adbf4acd3be27ee1ce767b2dd
slurm sub: 22223485

```bash
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
In readLines("/scratch/bjl34716/ade/cycle-4/work/f2/393f6123db4b1e3966950bb4fb784e/srs_min_curve_val.txt") :
  incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/f2/393f6123db4b1e3966950bb4fb784e/srs_min_curve_val.txt'
Error in colSums(data) : 'x' must be numeric
Calls: SRS -> colSums
Execution halted`, size: 714 (max: 255)


srs_in_tsv.view() = /scratch/bjl34716/ade/cycle-4/work/e6/c60301a271a8135a2692c3465b78c2/raw_table.tsv
ch_filtered_tsv_table.view() = /scratch/bjl34716/ade/cycle-4/work/72/b9efca874b51ad0dd892ac460c3e49/feature-table.tsv
ch_raw_tsv_table.view() = /scratch/bjl34716/ade/cycle-4/work/72/b9efca874b51ad0dd892ac460c3e49/feature-table.tsv
```

table passed into SRS:

```bash
# Constructed from biom file
#OTU ID LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109   LT110   LT111   LT112   LT113   LT114 LT115    LT116   LT117   LT118   LT119   LT120   LT73    LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82  LT83     LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95    LT96    LT97    LT98    LT99
8c9012e5e1fa2e6ec131de357794b220 
```

table from filtered table:

```bash
/scratch/bjl34716/ade/cycle-4/work/72/b9efca874b51ad0dd892ac460c3e49/feature-table.tsv
# Constructed from biom file
#OTU ID LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109   LT110   LT111   LT112   LT113   LT114 LT115    LT116   LT117   LT118   LT119   LT120   LT73    LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82  LT83     LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95    LT96    LT97    LT98    LT99
8c9012e5e1fa2e6ec131de357794b220
```

raw table: 

```bash
/scratch/bjl34716/ade/cycle-4/work/e6/c60301a271a8135a2692c3465b78c2/raw_table.tsv

"LT100" "LT101" "LT102" "LT103" "LT104" "LT105" "LT106" "LT107" "LT108" "LT109" "LT110" "LT111" "LT112" "LT113" "LT114" "LT115"LT116"  "LT117" "LT118" "LT119" "LT120" "LT73"  "LT74"  "LT75"  "LT76"  "LT77"  "LT78"  "LT79"  "LT80"  "LT81"  "LT82"  "LT83""LT84"   "LT85"  "LT86"  "LT87"  "LT88"  "LT89"  "LT90"  "LT91"  "LT92"  "LT93"  "LT95"  "LT96"  "LT97"  "LT98"  "LT99"  "MOCK167"      "MOCK288"       "MOCK323"       "MOCK71"        "NC168" "NC287" "NC324" "NC72"
"7b9c8d4a1896d84d92ab4820edd025a6"
```
```

When we export to TSV using QIIME2_EXPORT_ABSOLUTE_* we will need to re-run:

```groovy

CLEANUPRAWTSV(raw_tsv_table_ch
    ).raw_table_tsv.set { ch_raw_tsv_table }
```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: 3d43a8bd7889e6be71cb9c6eb0b62d97fe464bae
slurm sub: 22225351

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
  In readLines("/scratch/bjl34716/ade/cycle-4/work/f2/393f6123db4b1e3966950bb4fb784e/srs_min_curve_val.txt") :
    incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/f2/393f6123db4b1e3966950bb4fb784e/srs_min_curve_val.txt'
  Error in colSums(data) : 'x' must be numeric
  Calls: SRS -> colSums
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/ea/8bac5bad60234f06a0735a10f5b055
  
/scratch/bjl34716/ade/cycle-4/work/e6/c60301a271a8135a2692c3465b78c2/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/72/b9efca874b51ad0dd892ac460c3e49/feature-table.tsv
/scratch/bjl34716/ade/cycle-4/work/72/b9efca874b51ad0dd892ac460c3e49/feature-table.tsv
```


cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: c8e477e425352dcb03c9e8d62c0e113a7d34a0b0
slurm sub: 22226796

```bash
Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c4/c17a3ee0ed12e95d628d8a4e6124f3

Tip: view the complete command output by changing to the process work dir and entering the command `cat .command.out`


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
In readLines("/scratch/bjl34716/ade/cycle-4/work/16/09e63ecd587e2ab2cdf2d9edfaebcc/srs_min_curve_val.txt") :
  incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/16/09e63ecd587e2ab2cdf2d9edfaebcc/srs_min_curve_val.txt'
Error in colSums(data) : 'x' must be numeric
Calls: SRS -> colSums
Execution halted`, size: 714 (max: 255)

/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv
/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv
```


cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: f1c82ef39a5004d6b9abdcaa837430fe13914893
slurm sub: 22228398

```bash
[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b5/09397e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[bf/1061a8] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b7/32b316] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[cd/b3106d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[de/eef3d6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[01/62e5e6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[da/824e15] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[f3/d29f91] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[16/09e63e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[2e/476579] process > VISUALIZE_AMPLISEQ:VISUALIZ... [  0%] 0 of 1
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
ch_raw_tsv_table.view() = /scratch/bjl34716/ade/cycle-4/work/b5/09397efbec8d996055a1848ff63c9b/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/b5/09397efbec8d996055a1848ff63c9b/raw_table.tsv
raw_mba_table.view() = /scratch/bjl34716/ade/cycle-4/work/b5/09397efbec8d996055a1848ff63c9b/raw_table_MbA.tsv
srs_in_tsv.view()/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv
/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv

```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: 15c7bb3789de5101eabeffdc7c7a5071acfc95b6
slurm sub: 22228768

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [condescending_wright] DSL2 - revision: 15c7bb3789 [srs]
Missing process or function with name 'view'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 86 or see '.nextflow.log' file for more details
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: 18e4b0b1a97d10883caf0e86b88124e33777cd08
slurm sub: 22228901

```bash
/scratch/bjl34716/ade/cycle-4/work/b5/09397efbec8d996055a1848ff63c9b/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv
```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: 2e6066abee006d29a58b18b7f2a246b744a91455
slurm sub: 22229130

```bash
raw tsv table:
NC cleaned table :
into srs normalize:
filtered table:
raw_tsv_table:
/scratch/bjl34716/ade/cycle-4/work/b5/09397efbec8d996055a1848ff63c9b/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv
/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv
/scratch/bjl34716/ade/cycle-4/work/01/62e5e64112debbf9c81f30d7f2b583/raw_table.tsv
```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: 5ad1f1a1a26abe4e4dcd9fbfdeedc2ac3c4941fe
slurm sub: 22229608

```bash
/scratch/bjl34716/ade/cycle-4/work/b5/09397efbec8d996055a1848ff63c9b/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/b5/09397efbec8d996055a1848ff63c9b/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/01/62e5e64112debbf9c81f30d7f2b583/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv
/scratch/bjl34716/ade/cycle-4/work/f3/d29f91f4cc17bf6264650981dbbd80/feature-table.tsv
```

```bash
'raw tsv table: ',CLEANUPRAWTSV.out.raw_table_tsv.view() /scratch/bjl34716/ade/cycle-4/work/b5/09397efbec8d996055a1848ff63c9b

'NC cleaned table : ',CLEANUPFILTTSV.out.raw_table_tsv.view() /scratch/bjl34716/ade/cycle-4/work/01/62e5e64112debbf9c81f30d7f2b583

'clean filt mock tsv: ' CLEANUPFILTTSV.out.raw_table_tsv.view() (not present?)

 print('into srs normalize: ',srs_in_tsv.view()) /scratch/bjl34716/ade/cycle-4/work/66/0563484857a79455d811e2d205bece
 
print("filtered table: ",ch_filtered_tsv_table.view())
        
print('raw_tsv_table: ',ch_raw_tsv_table.view())
```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: 5ef88b3998b1bfa2d2e2b7c5f1fedd70ffdd02e0
slurm sub: 22231658

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [thirsty_linnaeus] DSL2 - revision: 5ef88b3998 [srs]
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
raw tsv table:
Process 'CLEANUPFILTTSV' has been already used -- If you need to reuse the same component include it with a different name or include in a different workflow context

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 151 or see '.nextflow.log' file for more details
```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: 258f0baa675efec8fbf1d9c08ad2588fc0cd4734
slurm sub: 22232455

```bash
executor >  slurm (4)
[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b5/09397e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[bf/1061a8] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b7/32b316] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[cd/b3106d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[de/eef3d6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[01/62e5e6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[da/824e15] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[f3/d29f91] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[51/aff40f] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[8a/7762a5] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[b2/42cbc1] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[93/4eddaf] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Completed at: 08-May-2023 15:50:30
Duration    : 8m 4s
CPU hours   : 0.2 (19.7% cached)
Succeeded   : 4
Cached      : 10

Sucess
```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: f6c2739b8dc794a13f14a6d3800234b90302361f
slurm sub: 22233708

```bash
/scratch/bjl34716/ade/cycle-4/work/01/62e5e64112debbf9c81f30d7f2b583/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/51/aff40fa37f9f55f571d7ada15dc33e/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/51/aff40fa37f9f55f571d7ada15dc33e/raw_table.tsv
/scratch/bjl34716/ade/cycle-4/work/51/aff40fa37f9f55f571d7ada15dc33e/raw_table.tsv
```


```bash
/scratch/bjl34716/ade/cycle-4/work/01/62e5e64112debbf9c81f30d7f2b583 ; VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:CLEANUPFILTTSV (feature-table.tsv)

> library(tidyverse)
> table <- read.table('raw_table.tsv')
> colSums(table)
  LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109
  49310   66941   49141   49177   42147     111   61204   43832   64887   55267
  LT110   LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119
  45422   57547   65777   95753  101883   60087   16777   45906   52614   41924
  LT120    LT73    LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81
  53815       6   32467   22261   34065   30143   31022   23455   29338   19877
   LT82    LT83    LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91
  25110       4   27082   52045   48475   60500   46449   64058   36320   41303
   LT92    LT93    LT95    LT96    LT97    LT98    LT99 MOCK167 MOCK288 MOCK323
  35994   53447   53211    2915      25   55016   64752      59    2357   49481
 MOCK71
  10908

/scratch/bjl34716/ade/cycle-4/work/51/aff40fa37f9f55f571d7ada15dc33e ; VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:CLEANUPFILTMOCKTSV (feature-table.tsv)

> library(tidyverse)
> table <- read.table('raw_table.tsv')
> colSums(table)
> colSums(table)
 LT100  LT101  LT102  LT103  LT104  LT105  LT106  LT107  LT108  LT109  LT110
 49310  66941  49141  49177  42147    111  61204  43832  64887  55267  45422
 LT111  LT112  LT113  LT114  LT115  LT116  LT117  LT118  LT119  LT120   LT73
 57547  65777  95753 101883  60087  16777  45906  52614  41924  53815      6
  LT74   LT75   LT76   LT77   LT78   LT79   LT80   LT81   LT82   LT83   LT84
 32467  22261  34065  30143  31022  23455  29338  19877  25110      4  27082
  LT85   LT86   LT87   LT88   LT89   LT90   LT91   LT92   LT93   LT95   LT96
 52045  48475  60500  46449  64058  36320  41303  35994  53447  53211   2915
  LT97   LT98   LT99
    25  55016  64752

/scratch/bjl34716/ade/cycle-4/work/b2/42cbc1760db022f5b7cb9437ec918b ; ch_normalized_tsv

>library(tidyverse)
> table <- read.table('raw_table.tsv')
> colSums(table)
LT100 LT101 LT102 LT103 LT104 LT106 LT107 LT108 LT109 LT110 LT111 LT112 LT113
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
LT114 LT115 LT116 LT117 LT118 LT119 LT120  LT74  LT75  LT76  LT77  LT78  LT79
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT80  LT81  LT82  LT84  LT85  LT86  LT87  LT88  LT89  LT90  LT91  LT92  LT93
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT95  LT98  LT99
16500 16500 16500

```

cycle 4 rev: 2d9381c72353c6a22c34c12ada6b1f242d366b55
visualize ampliseq rev: 55ffde4bf3867d125ff335eb3196f1a851199b31
slurm sub: 22235715

```bash
/scratch/bjl34716/ade/cycle-4/work/b2/42cbc1760db022f5b7cb9437ec918b/normalized-table.tsv
/scratch/bjl34716/ade/cycle-4/work/93/4eddaf5637f52d65926d80b35d2143/feature-table.qza
```

cycle 4 rev: 63aef6caa9cfd8a10166a4e3cf5d76fb1af3c129
visualize ampliseq rev: 55ffde4bf3867d125ff335eb3196f1a851199b31
slurm sub: 22236124

```bash
Completed at: 08-May-2023 16:23:00
Duration    : 1m 3s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 3
DataflowStream[DataflowStream[?], groovyx.gpars.dataflow.operator.PoisonPill@7b38f23f, ?]
DataflowStream[DataflowStream[?], groovyx.gpars.dataflow.operator.PoisonPill@7b38f23f, ?]
```

cycle 4 rev: be09a0bc7c443c3659a206711bc2b81847d59135
visualize ampliseq rev: 55ffde4bf3867d125ff335eb3196f1a851199b31
slurm sub: 22236534

```bash
no normalization with SRS
DataflowStream[?]
DataflowStream[?]
```

cycle 4 rev:  039f77726527c2718c7a2c3dd9bb1e7c6f26b40c
visualize ampliseq rev: 55ffde4bf3867d125ff335eb3196f1a851199b31
slurm sub: 22236770

```bash
no normalization with SRS
DataflowStream[?]
DataflowStream[?]
```

### Todos for Tomorrow

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
df17184 - Benjamin Lorentz, Mon May 8 09:49:42 2023 -0400 : added Mondays page
```

#### Visualize Ampliseq

```bash
55ffde4 - Benjamin Lorentz, Mon May 8 16:17:39 2023 -0400 : update visualize-ampliseq
a92765b - Benjamin Lorentz, Mon May 8 15:59:17 2023 -0400 : update visualize ampliseq
f6c2739 - Benjamin Lorentz, Mon May 8 15:56:01 2023 -0400 : update visualize-ampliseq
258f0ba - Benjamin Lorentz, Mon May 8 15:42:25 2023 -0400 : update visualize ampliseq
5ef88b3 - Benjamin Lorentz, Mon May 8 15:34:06 2023 -0400 : fix my parens
561a770 - Benjamin Lorentz, Mon May 8 15:32:17 2023 -0400 : update visualize ampliseq
5ad1f1a - Benjamin Lorentz, Mon May 8 15:16:26 2023 -0400 : update visualize-ampliseq
2e6066a - Benjamin Lorentz, Mon May 8 15:10:03 2023 -0400 : update visualize-ampliseq
18e4b0b - Benjamin Lorentz, Mon May 8 15:06:07 2023 -0400 : update visualize-ampliseq
15c7bb3 - Benjamin Lorentz, Mon May 8 15:03:23 2023 -0400 : update visualize-ampliseq.nf
f1c82ef - Benjamin Lorentz, Mon May 8 14:58:09 2023 -0400 : update visualize ampliseq
052feff - Benjamin Lorentz, Mon May 8 14:46:56 2023 -0400 : update cleanrawtsv
c8e477e - Benjamin Lorentz, Mon May 8 14:37:36 2023 -0400 : update visual-ampliseq and cleanuprawtsv
:...skipping...
55ffde4 - Benjamin Lorentz, Mon May 8 16:17:39 2023 -0400 : update visualize-ampliseq
a92765b - Benjamin Lorentz, Mon May 8 15:59:17 2023 -0400 : update visualize ampliseq
f6c2739 - Benjamin Lorentz, Mon May 8 15:56:01 2023 -0400 : update visualize-ampliseq
258f0ba - Benjamin Lorentz, Mon May 8 15:42:25 2023 -0400 : update visualize ampliseq
5ef88b3 - Benjamin Lorentz, Mon May 8 15:34:06 2023 -0400 : fix my parens
561a770 - Benjamin Lorentz, Mon May 8 15:32:17 2023 -0400 : update visualize ampliseq
5ad1f1a - Benjamin Lorentz, Mon May 8 15:16:26 2023 -0400 : update visualize-ampliseq
2e6066a - Benjamin Lorentz, Mon May 8 15:10:03 2023 -0400 : update visualize-ampliseq
18e4b0b - Benjamin Lorentz, Mon May 8 15:06:07 2023 -0400 : update visualize-ampliseq
15c7bb3 - Benjamin Lorentz, Mon May 8 15:03:23 2023 -0400 : update visualize-ampliseq.nf
f1c82ef - Benjamin Lorentz, Mon May 8 14:58:09 2023 -0400 : update visualize ampliseq
052feff - Benjamin Lorentz, Mon May 8 14:46:56 2023 -0400 : update cleanrawtsv
c8e477e - Benjamin Lorentz, Mon May 8 14:37:36 2023 -0400 : update visual-ampliseq and cleanuprawtsv      
3d43a8b - Benjamin Lorentz, Mon May 8 14:27:49 2023 -0400 : update visualize-ampliseq.nf
d959e17 - Benjamin Lorentz, Mon May 8 14:10:26 2023 -0400 : update visualize-ampliseq.nf
fdfab57 - Benjamin Lorentz, Mon May 8 13:58:23 2023 -0400 : update srscurve.nf
c497ec2 - Benjamin Lorentz, Mon May 8 13:52:30 2023 -0400 : fix srs curve braces
3fac5dc - Benjamin Lorentz, Mon May 8 13:51:04 2023 -0400 : update modules.conf
3ef8979 - Benjamin Lorentz, Mon May 8 13:47:00 2023 -0400 : add whitespace to SRSCURVE import SRSNORMALIZE
657ccff - Benjamin Lorentz, Mon May 8 13:42:31 2023 -0400 : add SRS modules
35dc541 - Benjamin Lorentz, Mon May 8 11:43:40 2023 -0400 : update visualize ampliseq
```

#### Cycle 4 

```bash
a06f557 - Benjamin Lorentz, Mon May 8 16:31:07 2023 -0400 : update srs nc
039f777 - Benjamin Lorentz, Mon May 8 16:29:35 2023 -0400 : update ses nc
be09a0b - Benjamin Lorentz, Mon May 8 16:26:02 2023 -0400 : update srs nc
63aef6c - Benjamin Lorentz, Mon May 8 16:21:57 2023 -0400 : update srs-nc
2d9381c - Benjamin Lorentz, Mon May 8 13:44:23 2023 -0400 : update SRS NC params
cec637d - Benjamin Lorentz, Mon May 8 11:49:47 2023 -0400 : modify srs nc params
```


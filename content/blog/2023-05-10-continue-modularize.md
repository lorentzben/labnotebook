---
title: 'Continue Modularize'
date: 2023-05-10T12:33:09Z
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
    - GENERATEBIOMFORGRAPHLAN
    - COREMETRICPYTHON
    - QIIME2_EXPORT_ABSOLUTE_CORE(COREMETRICPYTHON.out.rare_table)
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

#### GENERATE BIOM FOR GRAPHLAN


Test with Yes Yes Yes

cycle 4 rev: 08aad11963ccbc54fde2d78ed50551e5b68a18c9
visualize ampliseq rev: 
slurm sub: 

```bash
```

Test with No No No

cycle 4 rev: 08aad11963ccbc54fde2d78ed50551e5b68a18c9
visualize ampliseq rev: cfaa6c78d93834361927418d09a980ac2312719c
slurm sub: 22288842

```bash
[10/5b79fd] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 10-May-2023 10:26:55
Duration    : 4m 6s
CPU hours   : 0.5 (34.5% cached)
Succeeded   : 1
Cached      : 15

$ ls /scratch/bjl34716/ade/cycle-4/work/10/5b79fd83639369dee1f7b4f4c00069/biom_tabs/
CYCL1CTRL21-otu-table-mod.biom  CYCL1INF28-otu-table-mod.biom   CYCL3INF21-otu-table-mod.biom   FRESHCTRL28-otu-table-mod.biom
CYCL1CTRL28-otu-table-mod.biom  CYCL3CTRL21-otu-table-mod.biom  CYCL3INF28-otu-table-mod.biom   FRESHINF21-otu-table-mod.biom
CYCL1INF21-otu-table-mod.biom   CYCL3CTRL28-otu-table-mod.biom  FRESHCTRL21-otu-table-mod.biom  FRESHINF28-otu-table-mod.biom
```

cycle 4 rev: db0f69f1c2c3fd5b99af338fc063b994ec997373
visualize ampliseq rev: cfaa6c78d93834361927418d09a980ac2312719c
slurm sub: 22289433

```bash
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[f7/6b3f57] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -

Completed at: 10-May-2023 10:37:09
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 4
```

The process wasn't running so I am adding in a ifEmpty()

cycle 4 rev: db0f69f1c2c3fd5b99af338fc063b994ec997373
visualize ampliseq rev: 533d3ebf6548ad6afbc88f645af06b0c6ec7f9ca
slurm sub: 22289522

```bash
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[f7/6b3f57] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[c5/ee89c6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 10-May-2023 10:45:14
Duration    : 5m 6s
CPU hours   : 0.5 (2.8% cached)
Succeeded   : 1
Cached      : 4

$ ls /scratch/bjl34716/ade/cycle-4/work/c5/ee89c6fa43ed9f07d05f8c4a39c6f3/biom_tabs/
CYCL1CTRL21-otu-table-mod.biom  CYCL3CTRL21-otu-table-mod.biom  FRESHCTRL21-otu-table-mod.biom  MOCK-otu-table-mod.biom
CYCL1CTRL28-otu-table-mod.biom  CYCL3CTRL28-otu-table-mod.biom  FRESHCTRL28-otu-table-mod.biom  NC-otu-table-mod.biom
CYCL1INF21-otu-table-mod.biom   CYCL3INF21-otu-table-mod.biom   FRESHINF21-otu-table-mod.biom
CYCL1INF28-otu-table-mod.biom   CYCL3INF28-otu-table-mod.biom   FRESHINF28-otu-table-mod.biom
```

LGTM

#### COREMETRICPYTHON

yes yes yes rare val

cycle 4 rev: e67a581540a398069791fa7e4db33a160b161d47
visualize ampliseq rev: f61ec9b7ca7e485a07e907a840afd10f225fde23
slurm sub: 22290139

```bash
[d2/6f4b58] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 10-May-2023 11:01:02
Duration    : 1m 6s
CPU hours   : 0.6 (90.3% cached)
Succeeded   : 1
Cached      : 16

$ ls /scratch/bjl34716/ade/cycle-4/work/d2/6f4b58

 ls /scratch/bjl34716/ade/cycle-4/work/d2/6f4b58fdc067f9253eb98c453ba6ae/diversity_core/
bray_curtis_distance_matrix.qza  jaccard_emperor.qzv                     unweighted_unifrac_emperor.qzv
bray_curtis_emperor.qzv          jaccard_pcoa_results.qza                unweighted_unifrac_pcoa_results.qza
bray_curtis_pcoa_results.qza     observed_features_vector.qza            weighted_unifrac_distance_matrix.qza
evenness_vector.qza              rarefied_table.qza                      weighted_unifrac_emperor.qzv
faith_pd_vector.qza              shannon_vector.qza                      weighted_unifrac_pcoa_results.qza
jaccard_distance_matrix.qza      unweighted_unifrac_distance_matrix.qza
```

no no no rareval 

cycle 4 rev: d14d116a6d94757ea288b996eebea0dc3170068b
visualize ampliseq rev: f61ec9b7ca7e485a07e907a840afd10f225fde23
slurm sub: 22290360

```bash
[f1/201e1c] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 10-May-2023 11:05:51
Duration    : 1m 6s
CPU hours   : 0.5 (91.1% cached)
Succeeded   : 1
Cached      : 5
```

no no no no rare num

cycle 4 rev: d9243112a93af9030f6122bd2dab7523bccabaf6
visualize ampliseq rev: f61ec9b7ca7e485a07e907a840afd10f225fde23
slurm sub: 22290924

```bash
Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/17/04d91a901d6054ab317808dac0a348/.command.sh", line 29, in <module>
    data = pd.read_csv('raw-feature-table.qza', sep="   ", skiprows=[0, 1], header=None)  # count table
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 688, in read_csv
    return _read(filepath_or_buffer, kwds)
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 460, in _read
    data = parser.read(nrows)
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 1198, in read
    ret = self._engine.read(nrows)
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 2157, in read
    data = self._reader.read(nrows)
  File "pandas/_libs/parsers.pyx", line 847, in pandas._libs.parsers.TextReader.read
  File "pandas/_libs/parsers.pyx", line 862, in pandas._libs.parsers.TextReader._read_low_memory
  File "pandas/_libs/parsers.pyx", line 918, in pandas._libs.parsers.TextReader._read_rows
  File "pandas/_libs/parsers.pyx", line 905, in pandas._libs.parsers.TextReader._tokenize_rows
  File "pandas/_libs/parsers.pyx", line 2042, in pandas._libs.parsers.raise_parser_error
pandas.errors.ParserError: Error tokenizing data. C error: Expected 2 fields in line 12, saw 4`, size: 1581 (max: 255)
```

cycle 4 rev: d9243112a93af9030f6122bd2dab7523bccabaf6
visualize ampliseq rev: 2e51ab8adc0538928f316ed4c90e6181b93e5eb7
slurm sub: 22291563

```bash
[a4/bfec5a] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 10-May-2023 11:35:23
Duration    : 1m 6s
CPU hours   : 0.5 (91.3% cached)
Succeeded   : 1
Cached      : 5

ls /scratch/bjl34716/ade/cycle-4/work/a4/bfec5a

head /scratch/bjl34716/ade/cycle-4/work/a4/bfec5a5378e20120b19a51b6f23791/rarefaction.txt
4
```

yes yes yes no rarefaction

cycle 4 rev: q463cd0fb663f187d140f32e8f3606b3663ea0272
visualize ampliseq rev: 2e51ab8adc0538928f316ed4c90e6181b93e5eb7
slurm sub: 22291656

```bash
```

It was a space not tabs but only from SRS? so can we go fix that...

yes yes yes no 

cycle 4 rev: 463cd0fb663f187d140f32e8f3606b3663ea0272
visualize ampliseq rev: 7aed42bdbe593971c3347e9c6442b5a84a66d81b
slurm sub: 22296633

```bash

```

no no no no 

cycle 4 rev: ed4286d7beab4c4b2bda0946f5a2d823bf404472
visualize ampliseq rev: 7aed42bdbe593971c3347e9c6442b5a84a66d81b
slurm sub: 22296879

```bash

WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/7f/75dd8991ecb14f33a7b855a57da87d/.command.sh", line 38, in <module>
    mindepth = int(sums.min())
ValueError: cannot convert float NaN to integer`, size: 459 (max: 255)
```

cycle 4 rev: ed4286d7beab4c4b2bda0946f5a2d823bf404472
visualize ampliseq rev: c17173bad14000501cf1966d33eb736df94a0892
slurm sub: 22297199

```bash
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[f7/6b3f57] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[c5/ee89c6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[28/b606ac] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 10-May-2023 13:58:38
Duration    : 1m 6s
CPU hours   : 0.6 (79.5% cached)
Succeeded   : 1
Cached      : 5
```

confirm yes yes yes no 

cycle 4 rev: e10a9b68477b3736ddfc0ec2c442ff457b753add
visualize ampliseq rev: c17173bad14000501cf1966d33eb736df94a0892
slurm sub: 22297447

```bash
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[f7/6b3f57] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9e/16fcd2] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e0/5b29df] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[83/544991] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[d6/76503a] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[1a/f1dcbe] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e0/98ef7d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[23/ee35f4] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[52/bb22cf] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[29/a57dd1] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[67/5b1b52] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[0a/b8021a] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[38/3873fb] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[f4/ac3ed3] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 10-May-2023 14:01:13
Duration    : 1m 9s
CPU hours   : 0.5 (90.3% cached)
Succeeded   : 1
Cached      : 16
```

LGTM!

#### QIIME2_EXPORT_ABSOLUTE_CORE

cycle 4 rev: fe9da702a2d2ee932595dab9f232611334e26b23
visualize ampliseq rev: fecac594bf3b4412b4cf76ac72cecb394195b616
slurm sub: 22297935

```bash
No such variable: Exception evaluating property 'norm_tsv_table' for nextflow.script.ChannelOut, Reason: groovy.lang.MissingPropertyException: No such property: norm_tsv_table for class: groovyx.gpars.dataflow.DataflowBroadcast

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 248 or see '.nextflow.log' file for more details
```


cycle 4 rev: fe9da702a2d2ee932595dab9f232611334e26b23
visualize ampliseq rev: 6113d4a752707e1b11a6ff4554a8c0f7061d5e55
slurm sub: 22298503

```bash
[ca/6cb432] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[ca/d5bfac] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
/scratch/bjl34716/ade/cycle-4/work/ca/6cb4327e374468f708d05d81d9b63b/diversity_core/rarefied_table.qza
/scratch/bjl34716/ade/cycle-4/work/ca/d5bfac16c71a7cf809b192cc9692d2/feature-table.tsv

Completed at: 10-May-2023 14:14:01
Duration    : 2m 4s
CPU hours   : 0.6 (89.7% cached)
Succeeded   : 2
Cached      : 16

bjl34716@ss-sub4 srs-test$ head /scratch/bjl34716/ade/cycle-4/work/ca/d5bfac16c71a7cf809b192cc9692d2/feature-table.tsv
# Constructed from biom file
#OTU ID LT100   LT101   LT102   LT103   LT104   LT106   LT107   LT108   LT109   LT110   LT111   LT112   LT113   LT114   LT115 LT116    LT117   LT118   LT119   LT120   LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82    LT84    LT85  LT86     LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95    LT98    LT99
```

cycle 4 rev: fe9da702a2d2ee932595dab9f232611334e26b23
visualize ampliseq rev: ae9cb02cc7e35d32674065b751b5c00769a5cabf
slurm sub: 22299069

```bash
[e1/9f35fe] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔

Completed at: 10-May-2023 14:21:09
Duration    : 1m 5s
CPU hours   : 0.6 (99.6% cached)
Succeeded   : 1
Cached      : 18
```

LGTM

#### Report Module


cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: 1a0d16e4684058aed4b3ae70b02652cd3e81f81a 
slurm sub: 22299589

```bash
Launching `https://github.com/lorentzben/visualize-ampliseq` [maniac_saha] DSL2 - revision: 1a0d16e468 [srs]
No such file: Cant find a matching module file for include: /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/renderreport.nf
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: fc7198868d424d08d0be8085d3d19ce082f20e64
slurm sub: 22299651

```bash
Launching `https://github.com/lorentzben/visualize-ampliseq` [soggy_babbage] DSL2 - revision: fc7198868d [srs]
Module compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/renderreport.nf
- cause: Unexpected input: ':' @ line 24, column 27.
       path("figures/*") emit: figures_generated
                             ^

1 error
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: e692fa643bf4055b0ed512d68d77d7fa0f112a69 
slurm sub: 22299734

```bash
Process `VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:REPORT01BARPLOT` declares 6 input channels but 5 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 259 or see '.nextflow.log' file for more details
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: daf01401f2996c0b0ee1a00929bd04363e0d8d74
slurm sub: 22299791

```bash
Error executing process > 'VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:REPORT01BARPLOT (null)'

Caused by:
  Not a valid path value: 'Treatment'
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: d3a198c9ea55b4aecca969dc75c3d0f74132944c
slurm sub: 22300191

```bash
processing file: 01_report_MbA.Rmd
Quitting from lines 38-137 (01_report_MbA.Rmd)
Error in parse(text = x, srcfile = src) : <text>:32:45: unexpected '{'
31:   write.table(new_table_df,file = paste0(mbadir,"/ASV-tab.txt"),sep='\t',row.names = F)
32: } else if(file.exists("mock-nc-removed.tsv"){
                                                ^
Calls: <Anonymous> ... <Anonymous> -> parse_all -> parse_all.character -> parse
In addition: Warning message:
In readLines(paste0("item_of_interest.csv")) :
  incomplete final line found on 'item_of_interest.csv'
Execution halted`, size: 577 (max: 255)
```

example mba table:
/scratch/bjl34716/ade/cycle-4/work/e2/ea6677922aa36ac263a78ee5de2fe5/microbiome_analyst_tmp/ASV-tab.txt

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: 5376d96bb6cb9b0b4a720c7947e81fc28cbdb174
slurm sub: 22300680

```bash
Process `VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:REPORT01BARPLOT` declares 7 input channels but 6 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 259 or see '.nextflow.log' file for more details
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: 2025e4f9b1150c913c6e574b6e47c5809399224d
slurm sub: 22300786

```bash
Command error:
  cp: cannot stat '!{table_tsv}': No such file or directory
  cp: cannot stat '!{table_qza}': No such file or directory
  Error in abs_path(input) : The file '!{report}' does not exist.
  Calls: <Anonymous> -> setwd -> dirname -> abs_path
  In addition: Warning message:
  In normalizePath(path, winslash = winslash, mustWork = mustWork) :
    path[1]="!{report}": No such file or directory
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/5f/064ee4729aa63f22d7f81ab4102e00

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `cp: cannot stat '!{table_tsv}': No such file or directory
cp: cannot stat '!{table_qza}': No such file or directory
Error in abs_path(input) : The file '!{report}' does not exist.
Calls: <Anonymous> -> setwd -> dirname -> abs_path
In addition: Warning message:
In normalizePath(path, winslash = winslash, mustWork = mustWork) :
  path[1]="!{report}": No such file or directory
Execution halted`, size: 393 (max: 255)
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: b592b959c4560f6e9a6de4c800285f62b0670de2
slurm sub: 22301090

```bash
  dt=$(date '+%d-%m-%Y_%H.%M.%S');
  Rscript -e "rmarkdown::render("${report}", output_file='$PWD/!{report}_$dt.html', output_format='html_document', clean=TRUE, knit_root_dir='$PWD')"

  #Rscript -e "rmarkdown::render("${report}", output_file='$PWD/!{report}_$dt.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='$PWD')"

Command exit status:
  1

Command output:
  (empty)

Command error:
  cp: cannot stat '': No such file or directory
  cp: cannot stat '': No such file or directory
  Error in xfun::file_ext(input) :
    argument "input" is missing, with no default
  Calls: <Anonymous> -> %in% -> tolower -> <Anonymous> -> character
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/98/b4c0bdd8fa3e9a59d7c30ace768aac

Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: 8ada34975f55ca6671422eccc962bf327083bf2b 
slurm sub: 22301229

```bash
Command output:
  (empty)

Command error:
  cp: cannot stat '!{table_tsv}': No such file or directory
  cp: cannot stat '!{table_qza}': No such file or directory
  Error in character(length(x)) : object 'report' not found
  Calls: <Anonymous> -> %in% -> tolower -> <Anonymous> -> character
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/6f/e235fecc157e32cddbe0b172d1ff03

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `cp: cannot stat '!{table_tsv}': No such file or directory
cp: cannot stat '!{table_qza}': No such file or directory
Error in character(length(x)) : object 'report' not found
Calls: <Anonymous> -> %in% -> tolower -> <Anonymous> -> character
Execution halted`, size: 256 (max: 255)
```
```


cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: baeb24279052294ade212038e7795463a7e4ee76
slurm sub: 22301758

```bash
Command error:
  Error in abs_path(input) : The file '!{report}' does not exist.
  Calls: <Anonymous> -> setwd -> dirname -> abs_path
  In addition: Warning message:
  In normalizePath(path, winslash = winslash, mustWork = mustWork) :
    path[1]="!{report}": No such file or directory
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/e9/761ef25dbec52f53d3ba78806d6223

Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `Error in abs_path(input) : The file '!{report}' does not exist.
Calls: <Anonymous> -> setwd -> dirname -> abs_path
In addition: Warning message:
In normalizePath(path, winslash = winslash, mustWork = mustWork) :
  path[1]="!{report}": No such file or directory
Execution halted`, size: 277 (max: 255)
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: 365836757fa381b411e0148099670a30d9856598
slurm sub: 22301891

```bash
Command error:
  Error in abs_path(input) : The file '' does not exist.
  Calls: <Anonymous> -> setwd -> dirname -> abs_path
  In addition: Warning message:
  In normalizePath(path, winslash = winslash, mustWork = mustWork) :
    path[1]="": No such file or directory
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/44/2a6d91e359e997fa1d1fbecf7be8e0

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `Error in abs_path(input) : The file '' does not exist.
Calls: <Anonymous> -> setwd -> dirname -> abs_path
In addition: Warning message:
In normalizePath(path, winslash = winslash, mustWork = mustWork) :
  path[1]="": No such file or directory
Execution halted`, size: 259 (max: 255)
```

cycle 4 rev: ad5af99a921d030fb1f1d7206324d6a51755997c 
visualize ampliseq rev: 66c618764be43c74a2a2212fd105f4440216e6c2 
slurm sub: 22302128

```bash
```

#### Report 01

### Todos for Tomorrow

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

### Git Commit

#### Lab Notebook

```bash
0f2f87b - Benjamin Lorentz, Wed May 10 08:39:06 2023 -0400 : add page for Wednesday
36d9512 - Benjamin Lorentz, Tue May 9 17:09:07 2023 -0400 : final notes for tuesday
```

#### Visualize Ampliseq

```bash
71d931c - Benjamin Lorentz, Wed May 10 17:01:46 2023 -0400 : remove sep
07eb54d - Benjamin Lorentz, Wed May 10 16:55:45 2023 -0400 : fix the tables out
b76cbb7 - Benjamin Lorentz, Wed May 10 16:53:10 2023 -0400 : update visualize-ampliseq
0f5d7c4 - Benjamin Lorentz, Wed May 10 16:47:30 2023 -0400 : needed to call it shell
7f28155 - Benjamin Lorentz, Wed May 10 16:39:09 2023 -0400 : add ls
a5a44d7 - Benjamin Lorentz, Wed May 10 16:28:51 2023 -0400 : update renderreport
35e46ea - Benjamin Lorentz, Wed May 10 16:15:50 2023 -0400 : single quote and !
65d2aed - Benjamin Lorentz, Wed May 10 16:13:26 2023 -0400 : single quotes and !
e38e8c9 - Benjamin Lorentz, Wed May 10 16:10:21 2023 -0400 : try dollarsign
1418d01 - Benjamin Lorentz, Wed May 10 16:01:40 2023 -0400 : escape $
3128d88 - Benjamin Lorentz, Wed May 10 15:56:43 2023 -0400 : quote the echo
5100390 - Benjamin Lorentz, Wed May 10 15:47:42 2023 -0400 : dont tell it the shell
66c6187 - Benjamin Lorentz, Wed May 10 15:40:08 2023 -0400 : just print the filename
:...skipping...
71d931c - Benjamin Lorentz, Wed May 10 17:01:46 2023 -0400 : remove sep
07eb54d - Benjamin Lorentz, Wed May 10 16:55:45 2023 -0400 : fix the tables out
b76cbb7 - Benjamin Lorentz, Wed May 10 16:53:10 2023 -0400 : update visualize-ampliseq
0f5d7c4 - Benjamin Lorentz, Wed May 10 16:47:30 2023 -0400 : needed to call it shell
7f28155 - Benjamin Lorentz, Wed May 10 16:39:09 2023 -0400 : add ls
a5a44d7 - Benjamin Lorentz, Wed May 10 16:28:51 2023 -0400 : update renderreport
35e46ea - Benjamin Lorentz, Wed May 10 16:15:50 2023 -0400 : single quote and !
65d2aed - Benjamin Lorentz, Wed May 10 16:13:26 2023 -0400 : single quotes and !
e38e8c9 - Benjamin Lorentz, Wed May 10 16:10:21 2023 -0400 : try dollarsign
1418d01 - Benjamin Lorentz, Wed May 10 16:01:40 2023 -0400 : escape $
3128d88 - Benjamin Lorentz, Wed May 10 15:56:43 2023 -0400 : quote the echo
5100390 - Benjamin Lorentz, Wed May 10 15:47:42 2023 -0400 : dont tell it the shell
66c6187 - Benjamin Lorentz, Wed May 10 15:40:08 2023 -0400 : just print the filename
434fb00 - Benjamin Lorentz, Wed May 10 15:34:49 2023 -0400 : update reportrender
3658367 - Benjamin Lorentz, Wed May 10 15:29:33 2023 -0400 : update rendereport
baeb242 - Benjamin Lorentz, Wed May 10 15:25:48 2023 -0400 : update renderreport
f068014 - Benjamin Lorentz, Wed May 10 15:17:17 2023 -0400 : update renderreport
8ada349 - Benjamin Lorentz, Wed May 10 15:12:30 2023 -0400 : update rendereport
b592b95 - Benjamin Lorentz, Wed May 10 15:08:45 2023 -0400 : update renderreport
2025e4f - Benjamin Lorentz, Wed May 10 15:02:57 2023 -0400 : update visualize ampliseq
5376d96 - Benjamin Lorentz, Wed May 10 14:59:39 2023 -0400 : update both the module and the report 01
d3a198c - Benjamin Lorentz, Wed May 10 14:45:08 2023 -0400 : update renderreport
daf0140 - Benjamin Lorentz, Wed May 10 14:41:45 2023 -0400 : update visualize
e692fa6 - Benjamin Lorentz, Wed May 10 14:39:46 2023 -0400 : update renderreport
fc71988 - Benjamin Lorentz, Wed May 10 14:37:40 2023 -0400 : forgot to add module file .
1a0d16e - Benjamin Lorentz, Wed May 10 14:34:16 2023 -0400 : update visualize ampliseq
ae9cb02 - Benjamin Lorentz, Wed May 10 14:19:40 2023 -0400 : update visualize ampliseq
6113d4a - Benjamin Lorentz, Wed May 10 14:12:02 2023 -0400 : update visualize-ampliseq
fecac59 - Benjamin Lorentz, Wed May 10 14:10:21 2023 -0400 : update visualize ampliseq
9190914 - Benjamin Lorentz, Wed May 10 14:05:56 2023 -0400 : update visualize-ampliseq
c17173b - Benjamin Lorentz, Wed May 10 13:56:38 2023 -0400 : update core metric python
7aed42b - Benjamin Lorentz, Wed May 10 13:49:08 2023 -0400 : update coremetric python
:...skipping...
71d931c - Benjamin Lorentz, Wed May 10 17:01:46 2023 -0400 : remove sep
07eb54d - Benjamin Lorentz, Wed May 10 16:55:45 2023 -0400 : fix the tables out
b76cbb7 - Benjamin Lorentz, Wed May 10 16:53:10 2023 -0400 : update visualize-ampliseq
0f5d7c4 - Benjamin Lorentz, Wed May 10 16:47:30 2023 -0400 : needed to call it shell
7f28155 - Benjamin Lorentz, Wed May 10 16:39:09 2023 -0400 : add ls
a5a44d7 - Benjamin Lorentz, Wed May 10 16:28:51 2023 -0400 : update renderreport
35e46ea - Benjamin Lorentz, Wed May 10 16:15:50 2023 -0400 : single quote and !
65d2aed - Benjamin Lorentz, Wed May 10 16:13:26 2023 -0400 : single quotes and !
e38e8c9 - Benjamin Lorentz, Wed May 10 16:10:21 2023 -0400 : try dollarsign
1418d01 - Benjamin Lorentz, Wed May 10 16:01:40 2023 -0400 : escape $
3128d88 - Benjamin Lorentz, Wed May 10 15:56:43 2023 -0400 : quote the echo
5100390 - Benjamin Lorentz, Wed May 10 15:47:42 2023 -0400 : dont tell it the shell
66c6187 - Benjamin Lorentz, Wed May 10 15:40:08 2023 -0400 : just print the filename
434fb00 - Benjamin Lorentz, Wed May 10 15:34:49 2023 -0400 : update reportrender
3658367 - Benjamin Lorentz, Wed May 10 15:29:33 2023 -0400 : update rendereport
baeb242 - Benjamin Lorentz, Wed May 10 15:25:48 2023 -0400 : update renderreport
f068014 - Benjamin Lorentz, Wed May 10 15:17:17 2023 -0400 : update renderreport
8ada349 - Benjamin Lorentz, Wed May 10 15:12:30 2023 -0400 : update rendereport
b592b95 - Benjamin Lorentz, Wed May 10 15:08:45 2023 -0400 : update renderreport
2025e4f - Benjamin Lorentz, Wed May 10 15:02:57 2023 -0400 : update visualize ampliseq
5376d96 - Benjamin Lorentz, Wed May 10 14:59:39 2023 -0400 : update both the module and the report 01
d3a198c - Benjamin Lorentz, Wed May 10 14:45:08 2023 -0400 : update renderreport
daf0140 - Benjamin Lorentz, Wed May 10 14:41:45 2023 -0400 : update visualize
e692fa6 - Benjamin Lorentz, Wed May 10 14:39:46 2023 -0400 : update renderreport
fc71988 - Benjamin Lorentz, Wed May 10 14:37:40 2023 -0400 : forgot to add module file .
1a0d16e - Benjamin Lorentz, Wed May 10 14:34:16 2023 -0400 : update visualize ampliseq
ae9cb02 - Benjamin Lorentz, Wed May 10 14:19:40 2023 -0400 : update visualize ampliseq
6113d4a - Benjamin Lorentz, Wed May 10 14:12:02 2023 -0400 : update visualize-ampliseq
fecac59 - Benjamin Lorentz, Wed May 10 14:10:21 2023 -0400 : update visualize ampliseq
9190914 - Benjamin Lorentz, Wed May 10 14:05:56 2023 -0400 : update visualize-ampliseq
c17173b - Benjamin Lorentz, Wed May 10 13:56:38 2023 -0400 : update core metric python
7aed42b - Benjamin Lorentz, Wed May 10 13:49:08 2023 -0400 : update coremetric python
2e51ab8 - Benjamin Lorentz, Wed May 10 11:33:55 2023 -0400 : update core metric python and visualize-ampliseq
f61ec9b - Benjamin Lorentz, Wed May 10 10:58:37 2023 -0400 : update visualize ampliseq
533d3eb - Benjamin Lorentz, Wed May 10 10:39:44 2023 -0400 : update visualize-ampliseq
cfaa6c7 - Benjamin Lorentz, Wed May 10 10:22:26 2023 -0400 : update visualize-ampliseq
```

#### Cycle 4

```bash
ad5af99 - Benjamin Lorentz, Wed May 10 14:35:58 2023 -0400 : update the yaml
fe9da70 - Benjamin Lorentz, Wed May 10 14:01:28 2023 -0400 : update srs nc mock
e10a9b6 - Benjamin Lorentz, Wed May 10 14:00:01 2023 -0400 : update driver
ed4286d - Benjamin Lorentz, Wed May 10 13:52:27 2023 -0400 : update driver script and litter param
071b947 - Benjamin Lorentz, Wed May 10 11:39:25 2023 -0400 : update srs nc mock
463cd0f - Benjamin Lorentz, Wed May 10 11:15:35 2023 -0400 : update driver script and SRS NC MOCK
d924311 - Benjamin Lorentz, Wed May 10 11:14:27 2023 -0400 : update litter param
d14d116 - Benjamin Lorentz, Wed May 10 11:05:12 2023 -0400 : update driver script
e67a581 - Benjamin Lorentz, Wed May 10 10:48:38 2023 -0400 : update driver script
db0f69f - Benjamin Lorentz, Wed May 10 10:36:28 2023 -0400 : update driver script
```

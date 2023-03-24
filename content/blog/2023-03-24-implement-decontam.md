---
title: 'Implement Decontam'
date: 2023-03-24T14:30:42Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "automate_16_nf"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - figure out where to implement a filtering step
  - How does the other Ben's Analysis line up with mine/ampliseq?
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

from yesterday:

#### Function to Filter the Contamination out

1. Create a function
2. Pull table in 
  2a. Read QZA -> phyloseq
3. Pull in file with the sampleIDs of the NC samples
4. How does decontam work?
5. Output Filtered table
  5a. QZA/phyloseq -> QZA/TSV for downstream analysis
6. Replace former table.qza files with filtered file.
  6a. OPT filter out Mock communities if applicable
  
cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: 54f6f11e7135e78a11d4e98376b5ce94a4e25576
slurm sub: 20076228

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 downloaded from https://github.com/lorentzben/visualize-ampliseq.git
Launching `https://github.com/lorentzben/visualize-ampliseq` [infallible_ride] DSL2 - revision: 54f6f11e71 [control]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /scratch/bjl34716/ade/cycle-4/litter
metadata : /scratch/bjl34716/ade/cycle-4/litter/metadata.tsv
item of interest : Treatment
ordered item of interest : ordered_item_of_interest.csv
outdir   : /work/sealab/bjl34716/ade/cycle-4/litter
rarefaction depth : 0
controls:
profile : slurm,singularity

Missing `fromPath` parameter
```
No control params

cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: e3e22142be3bb2f93caa3951da740ed0aa9419f7
slurm sub: 20101255

```bash
Sucess
```

With a controls file

cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: e3e22142be3bb2f93caa3951da740ed0aa9419f7
slurm sub: 20101379

```bash
Caused by:
  Process `FILTERNEGATIVECONTROL (1)` terminated with an error exit status (127)

Command executed:

  #!/usr/env R
  
  library(tidyverse)
  library(qiime2R)
  library(phyloseq)
  library(decontam)
  
  table_dada2 <- "results/qiime2/input/table.qza"
  rooted_tree <- "results/qiime2/phylogenetic_tree/rooted-tree.qza"
  taxonomy_file <- "results/qiime2/input/taxonomy.qza"
  metadata_file <- "metadata.tsv"
  
  table_phlyo <- qza_to_phyloseq(table_dada2,rooted_tree,taxonomy_file,metadata_file)

Command exit status:
  127

Command output:
  (empty)

Command error:
  .command.run: line 157: /usr/env: No such file or directory

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/cf/77c615a0d8bba48ba3dd7f151c117c
```

cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: 4aa798c75055c33f81737f3a6510486678e6e73b
slurm sub: 20101413

```bash
Caused by:
  Missing output file(s) `*.qza` expected by process `FILTERNEGATIVECONTROL (1)`

Command executed:

  #!/usr/bin/env R
  
  library(tidyverse)
  library(qiime2R)
  library(phyloseq)
  library(decontam)
  
  table_dada2 <- "results/qiime2/input/table.qza"
  rooted_tree <- "results/qiime2/phylogenetic_tree/rooted-tree.qza"
  taxonomy_file <- "results/qiime2/input/taxonomy.qza"
  metadata_file <- "metadata.tsv"
  
  table_phlyo <- qza_to_phyloseq(table_dada2,rooted_tree,taxonomy_file,metadata_file)

Command exit status:
  0

Command output:
  ARGUMENT '.command.sh' __ignored__
  
  
  R version 4.2.0 (2022-04-22) -- "Vigorous Calisthenics"
  Copyright (C) 2022 The R Foundation for Statistical Computing
  Platform: x86_64-pc-linux-gnu (64-bit)
  
  R is free software and comes with ABSOLUTELY NO WARRANTY.
  You are welcome to redistribute it under certain conditions.
  Type 'license()' or 'licence()' for distribution details.
  
    Natural language support but running in an English locale
  
  R is a collaborative project with many contributors.
  Type 'contributors()' for more information and
  'citation()' on how to cite R or R packages in publications.
  
  Type 'demo()' for some demos, 'help()' for on-line help, or
  'help.start()' for an HTML browser interface to help.
  Type 'q()' to quit R.
  
  > 

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/2d/de434d4565a69ac009d67ab16b1e66
```

We need to use decontam, then save a tsv, then use biom to convert to biom, then import to qiime then profit we can use system to make these calls from inside R.

cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: 1037373b16cfb514d7f6e8ce4737d7a2cc848aa0
slurm sub:  20102594

```bash
Caused by:
  Missing output file(s) `*.qza` expected by process `FILTERNEGATIVECONTROL (1)`

Command executed:

  #!/usr/bin/env R

  library(tidyverse)
  library(qiime2R)
  library(phyloseq)
  library(decontam)

  table_dada2 <- "results/qiime2/input/table.qza"
  rooted_tree <- "results/qiime2/phylogenetic_tree/rooted-tree.qza"
  taxonomy_file <- "results/qiime2/input/taxonomy.qza"
  metadata_file <- "metadata.tsv"

  table_phlyo <- qza_to_phyloseq(table_dada2,rooted_tree,taxonomy_file,metadata_file)

  OTU1 = as(otu_table(table_phylo), "matrix")
  if(taxa_are_rows(ps)){OTU1 <- t(OTU1)}
  # Coerce to data.frame
  OTUdf = as.data.frame(OTU1)

  write.table(OTUdf, file='table.tsv', quote=FALSE, sep='       ')

  biom_command <- "biom convert -i table.tsv -o feature-table.biom --to-hdf5"
  system(biom_command)
  
  Command exit status:
  0

Command output:
  ARGUMENT '.command.sh' __ignored__


  R version 4.2.0 (2022-04-22) -- "Vigorous Calisthenics"
  Copyright (C) 2022 The R Foundation for Statistical Computing
  Platform: x86_64-pc-linux-gnu (64-bit)

  R is free software and comes with ABSOLUTELY NO WARRANTY.
  You are welcome to redistribute it under certain conditions.
  Type 'license()' or 'licence()' for distribution details.

    Natural language support but running in an English locale

  R is a collaborative project with many contributors.
  Type 'contributors()' for more information and
  'citation()' on how to cite R or R packages in publications.

  Type 'demo()' for some demos, 'help()' for on-line help, or
  'help.start()' for an HTML browser interface to help.
  Type 'q()' to quit R.

  >
  /scratch/bjl34716/ade/cycle-4/work/1c/1362e57a5e4bc3dcdd54c12a6e29c7
```

cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: 02149945f82be2bdb4b9e3464d42379d5802c97a
slurm sub: 20102874

```bash
Command exit status:
  127

Command output:
  (empty)

Command error:
  Traceback (most recent call last):
    File "/usr/local/bin/biom", line 5, in <module>
      from biom.cli import cli
    File "/usr/local/lib/python3.8/dist-packages/biom/__init__.py", line 51, in <module>
      from .table import Table
    File "/usr/local/lib/python3.8/dist-packages/biom/table.py", line 195, in <module>
      from ._filter import _filter
    File "biom/_filter.pyx", line 1, in init biom._filter
  ValueError: numpy.ndarray size changed, may indicate binary incompatibility. Expected 96 from C header, got 88 from PyObject
  .command.sh: line 8: qiime: command not found

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/66/543a1fd2b08f910770e05964c968eb
```


cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: fad4adffc92ca676fc411cda465ee05045a08f5b
slurm sub: 20103029

```bash

Command error:
  ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
  ✔ ggplot2 3.3.6     ✔ purrr   0.3.4
  ✔ tibble  3.1.7     ✔ dplyr   1.0.9
  ✔ tidyr   1.2.0     ✔ stringr 1.4.0
  ✔ readr   2.1.2     ✔ forcats 0.5.1
  ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
  ✖ dplyr::filter() masks stats::filter()
  ✖ dplyr::lag()    masks stats::lag()
  Error in h(simpleError(msg, call)) : 
    error in evaluating the argument 'object' in selecting a method for function 'otu_table': object 'table_phylo' not found
  Calls: as -> .class1 -> otu_table -> .handleSimpleError -> h
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/58/0d139e65f939dc757d3392d0f854bb
```


cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: c96a1be8ae12df20276d2cadf1935005bb0e71c3
slurm sub: 20103177

```bash
Error executing process > 'FILTERNEGATIVECONTROL (1)'

Caused by:
  Missing output file(s) `*.qza` expected by process `FILTERNEGATIVECONTROL (1)`

Command executed:

  #!/usr/bin/env bash
  
  Rscript contam_script.r

Command exit status:
  0

Command output:
  (empty)

Command error:
  ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
  ✔ ggplot2 3.3.6     ✔ purrr   0.3.4
  ✔ tibble  3.1.7     ✔ dplyr   1.0.9
  ✔ tidyr   1.2.0     ✔ stringr 1.4.0
  ✔ readr   2.1.2     ✔ forcats 0.5.1
  ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
  ✖ dplyr::filter() masks stats::filter()
  ✖ dplyr::lag()    masks stats::lag()

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c1/30fcc4d9eb75564aa5d3d6a75c1004
```

cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: 50cda9961f7c39b221ec18d1c79a6f67dc529fe6
slurm sub: 20103381

```bash
Success!
```

We can't include qiime in the decontam image, so we will have to make a separate process that turns tsv into a qza. 

```bash
biom convert -i table.tsv -o feature-table.biom --to-hdf5

qiime tools import \
    --input-path feature-table.biom \
    --type 'FeatureTable[Frequency]' \
    --input-format BIOMV210Format \
    --output-path feature-table.qza
```

cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: e3a6abed37d5372a858250a4bde8c42e58090b21
slurm sub: 20103613

```bash
Command error:
      return ctx.invoke(self.callback, **ctx.params)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 610, in invoke
      return callback(*args, **kwargs)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/cli/table_converter.py", line 114, in convert
      table = load_table(input_fp)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/parse.py", line 672, in load_table
      table = parse_biom_table(fp)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/parse.py", line 416, in parse_biom_table
      t = Table.from_tsv(file_obj, None, None, lambda x: x)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/table.py", line 4665, in from_tsv
      return Table(data, obs_ids, sample_ids, obs_metadata, sample_metadata)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/table.py", line 475, in __init__
      shape=shape)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/table.py", line 630, in _to_sparse
      mat = list_list_to_sparse(values, dtype, shape=shape)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/table.py", line 4931, in list_list_to_sparse
      dtype=dtype)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/scipy/sparse/coo.py", line 196, in __init__
      self._check()
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/scipy/sparse/coo.py", line 285, in _check
      raise ValueError('column index exceeds matrix dimensions')
  ValueError: column index exceeds matrix dimensions
  Usage: qiime tools import [OPTIONS]
  
    Import data to create a new QIIME 2 Artifact. See https://docs.qiime2.org/
    for usage examples and details on the file types and associated semantic
    types that can be imported.
  
  Options:
    --type TEXT             The semantic type of the artifact that will be
                            created upon importing. Use --show-importable-types
                            to see what importable semantic types are available
                            in the current deployment.                [required]
    --input-path PATH       Path to file or directory that should be imported.
                                                                      [required]
    --output-path ARTIFACT  Path where output artifact should be written.
                                                                      [required]
    --input-format TEXT     The format of the data to be imported. If not
                            provided, data must be in the format expected by the
                            semantic type provided via --type.
    --show-importable-types Show the semantic types that can be supplied to
                            --type to import data into an artifact.
    --show-importable-formats
                            Show formats that can be supplied to --input-format
                            to import data into an artifact.
    --help                  Show this message and exit.
  
                      There was a problem with the command:                     
   (1/1) Invalid value for '--input-path': Path 'feature-table.biom' does not
    exist.

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c2/d246168ed0166b2ef3bb0a2eb54bc0
```

cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: bd38d8c2743da567a7eb8c8190a0e0ddb49b77ed
slurm sub: 20103992

```bash
Command error:
      return self.main(*args, **kwargs)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 782, in main
      rv = self.invoke(ctx)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 1259, in invoke
      return _process_result(sub_ctx.command.invoke(sub_ctx))
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 1066, in invoke
      return ctx.invoke(self.callback, **ctx.params)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 610, in invoke
      return callback(*args, **kwargs)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/cli/table_converter.py", line 114, in convert
      table = load_table(input_fp)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/parse.py", line 672, in load_table
      table = parse_biom_table(fp)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/parse.py", line 416, in parse_biom_table
      t = Table.from_tsv(file_obj, None, None, lambda x: x)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/table.py", line 4665, in from_tsv
      return Table(data, obs_ids, sample_ids, obs_metadata, sample_metadata)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/table.py", line 508, in __init__
      errcheck(self)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/err.py", line 474, in errcheck
      raise ret
  biom.exception.TableException: Duplicate observation IDs
  Usage: qiime tools import [OPTIONS]
  
    Import data to create a new QIIME 2 Artifact. See https://docs.qiime2.org/
    for usage examples and details on the file types and associated semantic
    types that can be imported.
```

cycle 4 rev: 88035d9864dec632bcec5507d215dd83caee3806
visualize-amplseq rev: 2cb32dc169d4a17673b2a4317fbd538e9a7fb665
slurm sub: 20104645

```bash
Command error:
      return self.main(*args, **kwargs)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 782, in main
      rv = self.invoke(ctx)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 1259, in invoke
      return _process_result(sub_ctx.command.invoke(sub_ctx))
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 1066, in invoke
      return ctx.invoke(self.callback, **ctx.params)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/click/core.py", line 610, in invoke
      return callback(*args, **kwargs)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/cli/table_converter.py", line 114, in convert
      table = load_table(input_fp)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/parse.py", line 672, in load_table
      table = parse_biom_table(fp)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/parse.py", line 416, in parse_biom_table
      t = Table.from_tsv(file_obj, None, None, lambda x: x)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/table.py", line 4665, in from_tsv
      return Table(data, obs_ids, sample_ids, obs_metadata, sample_metadata)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/table.py", line 508, in __init__
      errcheck(self)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/biom/err.py", line 474, in errcheck
      raise ret
  biom.exception.TableException: Duplicate observation IDs
  Usage: qiime tools import [OPTIONS]
  
    Import data to create a new QIIME 2 Artifact. See https://docs.qiime2.org/
    for usage examples and details on the file types and associated semantic
    types that can be imported.
```

Make sure that the colsum of these tabels line up with the unfiltered table example.
Alternatively we can go back to dada2/ASV_table.tsv and pull it into phyloseq that way. There is a Biom R package that might be really useful

### Todos for Next Week

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Check ASV count to the dada2 table 
    - Alternativley use the dada2 table
  - figure out where to implement a filtering step
  - How does the other Ben's Analysis line up with mine/ampliseq?
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
eb1a77d - Benjamin Lorentz, Fri Mar 24 10:32:48 2023 -0400 : added a page for Friday
1112f73 - Ben Lorentz, Thu Mar 23 19:52:12 2023 -0400 : post work comments
10566fd - Benjamin Lorentz, Thu Mar 23 17:09:39 2023 -0400 : final notes for thursday
```

#### Visualize Ampliseq

```bash
2cb32dc - Benjamin Lorentz, Fri Mar 24 16:25:09 2023 -0400 : update contam script
91356e0 - Benjamin Lorentz, Fri Mar 24 15:43:55 2023 -0400 : update contam script
bd38d8c - Benjamin Lorentz, Fri Mar 24 15:29:22 2023 -0400 : update contam script
08593ca - Benjamin Lorentz, Fri Mar 24 15:28:00 2023 -0400 : update contam-script and main
e3a6abe - Benjamin Lorentz, Fri Mar 24 15:00:27 2023 -0400 : update main.nf
50cda99 - Benjamin Lorentz, Fri Mar 24 14:44:21 2023 -0400 : update main.nf
c96a1be - Benjamin Lorentz, Fri Mar 24 14:38:21 2023 -0400 : update contam script
fad4adf - Benjamin Lorentz, Fri Mar 24 14:26:36 2023 -0400 : update main.nf
4c3c636 - Benjamin Lorentz, Fri Mar 24 14:17:28 2023 -0400 : update main.nf
0214994 - Benjamin Lorentz, Fri Mar 24 14:11:11 2023 -0400 : add contamination script and modify main.nf
1037373 - Benjamin Lorentz, Fri Mar 24 13:40:12 2023 -0400 : update dockerfile for biom format and update main.nf
4aa798c - Benjamin Lorentz, Fri Mar 24 11:12:04 2023 -0400 : update main.nf
e3e2214 - Benjamin Lorentz, Fri Mar 24 10:44:00 2023 -0400 : update main.nf
:...skipping...
2cb32dc - Benjamin Lorentz, Fri Mar 24 16:25:09 2023 -0400 : update contam script
91356e0 - Benjamin Lorentz, Fri Mar 24 15:43:55 2023 -0400 : update contam script
bd38d8c - Benjamin Lorentz, Fri Mar 24 15:29:22 2023 -0400 : update contam script
08593ca - Benjamin Lorentz, Fri Mar 24 15:28:00 2023 -0400 : update contam-script and main
e3a6abe - Benjamin Lorentz, Fri Mar 24 15:00:27 2023 -0400 : update main.nf
50cda99 - Benjamin Lorentz, Fri Mar 24 14:44:21 2023 -0400 : update main.nf
c96a1be - Benjamin Lorentz, Fri Mar 24 14:38:21 2023 -0400 : update contam script
fad4adf - Benjamin Lorentz, Fri Mar 24 14:26:36 2023 -0400 : update main.nf
4c3c636 - Benjamin Lorentz, Fri Mar 24 14:17:28 2023 -0400 : update main.nf
0214994 - Benjamin Lorentz, Fri Mar 24 14:11:11 2023 -0400 : add contamination script and modify main.nf
1037373 - Benjamin Lorentz, Fri Mar 24 13:40:12 2023 -0400 : update dockerfile for biom format and update main.nf
4aa798c - Benjamin Lorentz, Fri Mar 24 11:12:04 2023 -0400 : update main.nf
e3e2214 - Benjamin Lorentz, Fri Mar 24 10:44:00 2023 -0400 : update main.nf
54f6f11 - Ben Lorentz, Thu Mar 23 19:40:57 2023 -0400 : update main.nf
aa1981d - Benjamin Lorentz, Thu Mar 23 17:06:07 2023 -0400 : add decontam dockerfile and renv lockfile
```

#### Cycle 4 

```bash
b9b22ea - Benjamin Lorentz, Fri Mar 24 11:20:08 2023 -0400 : update params
88035d9 - Benjamin Lorentz, Fri Mar 24 11:02:01 2023 -0400 : update params file and add controls file
```
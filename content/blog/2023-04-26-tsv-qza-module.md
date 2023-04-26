---
title: 'TSV QZA Module'
date: 2023-04-26T14:51:14Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
  - "STAT 6220"
description: "Description for the page"
---

### Todos for Today

- Class
  - Paper?
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Make TSVTOQZA a module, and use multiple import
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
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

#### Restart analysis on Sapelo2

I built a module for TSV to QZA and then aliased it multiple times:

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: e744f5a1fd6a0bf6faabcf7c781a9c1e1f901e4f
slurm job: 21471021

```bash
Process `SRSCURVE` declares 5 input channels but 6 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 78 or see '.nextflow.log' file for more details
[-        ] process > ORDERIOI              -
[-        ] process > FILTERNEGATIVECONTROL -
```

We have to select the tsv from the metamap

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 02dc7e0f3acbcd8f31f6e33a883c06ad6710df36
slurm job: 21472701

```bash
No such variable: Exception evaluating property 'table_qza' for nextflow.script.ChannelOut, Reason: groovy.lang.MissingPropertyException: No such property: table_qza for class: groovyx.gpars.dataflow.DataflowBroadcast

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 84 or see '.nextflow.log' file for more details
[-        ] process > ORDERIOI              -
[-        ] process > FILTERNEGATIVECONTROL -
[-        ] process > TSVTOQZA              -
[-        ] process > SRSCURVE              -
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 3b84ed6b11ede90a6282bb508876756ca6432b05
slurm job: 21473864

```bash
-- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/tsvtoqza.nf' at line: 5 or see '.nextflow.log' file for more details
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: c328529632b5761c059228a5d9b4ae3eaf22f97b
slurm job: 21475015

```bash
No such variable: Exception evaluating property 'id' for java.util.ArrayList, Reason: groovy.lang.MissingPropertyException: No such property: id for class: java.lang.String

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/tsvtoqza.nf' at line: 5 or see '.nextflow.log' file for more details
[81/ed377d] Cached process > REPORT01BARPLOT (1)
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: c5bbef43a3715136e428a5478b3b38bfdd81e456
slurm job: 21476279

```bash
Error executing process > 'TSVTOQZA (Filtered-NC-Biom)'

Caused by:
  Missing output file(s) `*.qza` expected by process `TSVTOQZA (Filtered-NC-Biom)`

Command executed:

  #!/usr/bin/env bash

  biom add-metadata -i table.biom         -o md-table.biom         --observation-metadata-fp metadata.tsv

  qiime tools import         --input-path md-table.biom         --type 'FeatureTable[Frequency]'         --input-format BIOMV210Format         --output-path feature-table.qza

  cat <<-END_VERSIONS > versions.yml
  "TSVTOQZA":
      biom: $(echo $(biom --version 2>&1))
      qiime: $(echo $(qiime info 2>&1))
  END_VERSIONS

Command exit status:
  0

Command output:
  (empty)

Command error:
  Usage: biom add-metadata [OPTIONS]
  Try 'biom add-metadata -h' for help.

  Error: Invalid value for '-i' / '--input-fp': File 'table.biom' does not exist.
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
 (1/1) Invalid value for '--input-path': Path 'md-table.biom' does not exist.`, size: 1725 (max: 255)
```
```

cycle 4 rev: e2f5c2d9e6e57827bf1afacd30c2143d45e131cc
visualize ampliseq rev: 4b533b0e90de909c2c9ff40f109b8f266800892c
slurm job: 21477955

```bash
Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line



WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/c5/acd3afcc0c400c32a2ddba69165905/.command.sh", line 18, in <module>
    unrarefied_table = Artifact.load('table.qza')
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/result.py", line 66, in load
    archiver = archive.Archiver.load(filepath)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 299, in load
    archive = cls.get_archive(filepath)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/archive/archiver.py", line 264, in get_archive
    raise ValueError("%s is not a QIIME archive." % filepath)
ValueError: table.qza is not a QIIME archive.`, size: 974 (max: 255)
```

We need to figure out qzatable to just be the qza archive not the whole thing

### Todos for Tomorrow

- Class
  - Paper finalize
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Make TSVTOQZA a module, and use multiple import
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
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

### Git Commits

#### Lab Notebook

```bash
56c3862 - Benjamin Lorentz, Wed Apr 26 14:42:14 2023 -0400 : added notes on module
06206e9 - Benjamin Lorentz, Wed Apr 26 10:59:11 2023 -0400 : page for wednesday
967f285 - Benjamin Lorentz, Tue Apr 25 17:00:16 2023 -0400 : final notes for tuesday
```


#### Visualize Ampliseq

```bash
791f834 - Benjamin Lorentz, Wed Apr 26 16:54:08 2023 -0400 : update main.nf
1165e48 - Benjamin Lorentz, Wed Apr 26 16:52:53 2023 -0400 : update main.nf
4b533b0 - Benjamin Lorentz, Wed Apr 26 16:29:38 2023 -0400 : update tsvtoqza
c5bbef4 - Benjamin Lorentz, Wed Apr 26 16:07:20 2023 -0400 : update main.nf
c328529 - Benjamin Lorentz, Wed Apr 26 15:48:39 2023 -0400 : update main.nf
3b84ed6 - Benjamin Lorentz, Wed Apr 26 15:27:08 2023 -0400 : update main.nf
02dc7e0 - Benjamin Lorentz, Wed Apr 26 15:06:54 2023 -0400 : update main.nf
e744f5a - Benjamin Lorentz, Wed Apr 26 14:39:00 2023 -0400 : update main.nf
24a9321 - Benjamin Lorentz, Wed Apr 26 14:33:54 2023 -0400 : update main.nf and added module
```

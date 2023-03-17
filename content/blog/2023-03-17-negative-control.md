---
title: 'Negative Control'
date: 2023-03-17T14:38:59Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "ampliseq"
  - "automate 16 nf"
description: "Description for the page"
---

### Todos for Today

- Finalize Homework 3
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Run the same analysis with the Negative Controls to get out ahead of it. 
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Class

- email Prof ***Done***
- fill out survey ***Done***

### Ade Analysis

#### What did qiime do for negative controls?

They didn't!!! 

Ade Included negative controls and mock communities so we can look into implementing that?


from [researchgate](https://www.researchgate.net/post/How_should_we_take_into_account_negative_controls_in_lung_microbiota_16S_sequencing/565d47b37c1920fe108b4567/citation/download. )

```md
Dear Laura,
Take a look at this paper: http://www.biomedcentral.com/1741-7007/12/87. Basically, there are several steps you can take to minimize the effect of contaminant OTUs on your analysis:
1. Maximize the starting sample biomass (by filtration or enrichment). 
2. If PCR or extraction kit reagents are contaminated, replace them. If they are contaminated a second time, find another manufacturer.
3. Always sequence positive (mock) and negative controls from each batch of sample collection/storage medium, each extraction kit, and each PCR kit concurrently with the environmental samples of interest. Sequence the controls even if you don’t see a band on the gel.
4. If you have many samples, randomize or divided them so that treatment groups are evenly represented across all extraction kits and sequencing runs. Record which sample was processed with which kit so that contamination of a particular kit lot number can be traced to the final dataset.
5. After sequencing, look at taxa that are present in the negative controls, taxa that are statistically associated with a particular batch of reagents, and taxa that are unexpected biologically.
6. To qualify as "contaminants" in the samples, reads in the sample must be the exact sequence (or within the margin of sequencing error) that we find in the negative control (both reads being a “Pseudomonas” is not good enough). Furthermore, it should be present in a similar abundance relative to the other contaminants in the sample. So, if sequences A and B show up in a 2:1 ratio in the sample and in the control, it’s likely a contaminant; if it’s a 20:1 ratio in the sample and 1:2 in the control, it’s probably not a contaminant. I don't recommend “correcting” the relative abundance in the sample to remove the contaminant signal.
```

https://bmcbiol.biomedcentral.com/articles/10.1186/s12915-014-0087-z

Basically, we want to run the negative control data through and the positive control, then we can compare the abundances of the positive vs the expected (which we need from Dr. O) and then we can run an ANOVA type test to see if NC looks like our data or not. 

I did not process the negative control samples, I can process them but I need a little bit more information. 

- How were these Negative Controls constructed?
- What library was used for the positive controls?
  - https://docs.qiime2.org/2023.2/tutorials/quality-control/
  
gg-catalog ref: a25f8ce90f077864ef60572cee99e2983e44491a
slurm sub: 19918906

```bash
Command error:
  
  During handling of the above exception, another exception occurred:
  
  Traceback (most recent call last):
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/qiime2/metadata/io.py", line 109, in read
      df = df.apply(self._cast_column, axis='index',
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/pandas/core/frame.py", line 7768, in apply
      return op.get_result()
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/pandas/core/apply.py", line 185, in get_result
      return self.apply_standard()
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/pandas/core/apply.py", line 276, in apply_standard
      results, res_index = self.apply_series_generator()
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/pandas/core/apply.py", line 290, in apply_series_generator
      results[i] = self.f(v)
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/pandas/core/apply.py", line 110, in f
      return func(x, *args, **kwds)
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/qiime2/metadata/io.py", line 296, in _cast_column
      return self._to_numeric(series)
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/qiime2/metadata/io.py", line 326, in _to_numeric
      raise MetadataFileError(
  qiime2.metadata.io.MetadataFileError: Cannot convert metadata column 'Age' to numeric. The following values could not be interpreted as numeric: 'MOCK', 'NC'
  
  There may be more errors present in the metadata file. To get a full report, sample/feature metadata files can be validated with Keemei: https://keemei.qiime2.org
  
  Find details on QIIME 2 metadata requirements here: https://docs.qiime2.org/2021.8/tutorials/metadata/
  
  During handling of the above exception, another exception occurred:
  
  Traceback (most recent call last):
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/q2cli/click/type.py", line 172, in _convert_metadata
      metadata = qiime2.Metadata.load(fp)
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/qiime2/metadata/metadata.py", line 357, in load
      return MetadataReader(filepath).read(into=cls,
    File "/opt/conda/envs/qiime2-2021.8/lib/python3.8/site-packages/qiime2/metadata/io.py", line 120, in read
      raise MetadataFileError(msg, include_suffix=False)
  qiime2.metadata.io.MetadataFileError: Cannot convert metadata column 'Age' to numeric. The following values could not be interpreted as numeric: 'MOCK', 'NC'
```

gg-catalog ref: 9b90edcb464dfbc84df6a709dddf69a74ee7b9a3 
slurm sub:19919836

```bash
Command output:
  Imported results/qiime2/abundance_tables/feature-table.biom as BIOMV210Format to feature-table.qza

Command error:
    --verbose / --quiet    Display verbose output to stdout and/or stderr
                           during execution of this action. Or silence output if
                           execution is successful (silence is golden).
    --examples             Show usage examples and exit.
    --citations            Show citations and exit.
    --help                 Show this message and exit.
  
                      There was a problem with the command:                     
   (1/1) Invalid value for '--i-table': 'FRESHCTRL-filtered-table.qza' is not a
    valid filepath
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
   (1/1) Invalid value for '--input-path': File 'collapse-FRESHCTRL-table.qza'
    does not exist.
  Usage: biom convert [OPTIONS]
  Try 'biom convert -h' for help.
  
  Error: Invalid value for '-i' / '--input-fp': File 'collapse-FRESHCTRL-frequency/feature-table.biom' does not exist.
  Traceback (most recent call last):
    File ".command.sh", line 45, in <module>
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
  FileNotFoundError: [Errno 2] No such file or directory: 'otu-FRESHCTRL-table.tsv'

 /scratch/bjl34716/ade/cycle-4/work/f0/d547e1b8d2676db1fb0b265b685857
```

gg-catalog ref: 9b90edcb464dfbc84df6a709dddf69a74ee7b9a3 
slurm sub: 19919997

```bash

```

### Todos for Next Week

- Finalize Homework 3
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Run the same analysis with the Negative Controls to get out ahead of it. 
  - Meet with Dr. Ade
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
4ba1b88 - Benjamin Lorentz, Fri Mar 17 12:07:03 2023 -0400 : added notes for morning
acfbb6c - Benjamin Lorentz, Fri Mar 17 10:41:41 2023 -0400 : added page for Friday
```

#### Cycle 4

```bash
9b90edc - Benjamin Lorentz, Fri Mar 17 16:21:20 2023 -0400 : needed to convert age to numeric
a25f8ce - Benjamin Lorentz, Fri Mar 17 15:24:45 2023 -0400 : add mock and nc data
```

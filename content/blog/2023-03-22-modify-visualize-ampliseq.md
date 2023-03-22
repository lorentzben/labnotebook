---
title: 'Modify Visualize Ampliseq'
date: 2023-03-22T14:28:00Z
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
  
### Ade Analysis

#### Examine slurm 20041288

cycle 4 ref: 95a8d59b88e834c0d7dcf49c4535c5f0650bd51b
slurm sub: 20041288

```bash
Command error:
  QIIME is caching your current deployment for improved performance. This may take a few moments and should only happen once per deployment.
  Plugin error from diversity:

    Metadata does not contain any columns that satisfy this visualizer's requirements. There must be at least one metadata column that contains categorical data, isn't empty, doesn't consist of unique values, and doesn't consist of exactly one value.

  Debug info has been saved to /tmp/qiime2-q2cli-err-uf2gxyh6.log

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/37/1bcc8647931c433349da037a714c1a
```

cycle 4 ref: 4325468290a7bd2b86df83e9e55af22b75ae6e61
slurm sub: 20054810

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
  Traceback (most recent call last):
    File ".command.sh", line 7, in <module>
      tax_tab = pd.read_table('results/dada2/ASV_tax_species.tsv', sep='	')
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
  FileNotFoundError: [Errno 2] No such file or directory: 'results/dada2/ASV_tax_species.tsv'

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/37/4a59e3b8b59eb0c387fbb0960fbf79
```

I re-copied over the results dir


cycle 4 ref: 4325468290a7bd2b86df83e9e55af22b75ae6e61
slurm sub: 20055421

```bash
Command error:
  
  
  processing file: rarefaction_report.Rmd
  Quitting from lines 14-38 (rarefaction_report.Rmd) 
  Error: './results/dada2/ASV_table.tsv' does not exist in current working directory ('/scratch/bjl34716/ade/cycle-4/work/da/c15220fb640e4b6cc3e7300bca3eaa').
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/da/c15220fb640e4b6cc3e7300bca3eaa
```

cycle 4 ref: 4325468290a7bd2b86df83e9e55af22b75ae6e61
slurm sub: 20055499

```bash
Command output:
  WARNING The sampling depth of 4 seems too small for rarefaction

Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Traceback (most recent call last):
    File ".command.sh", line 50, in <module>
      rarefact = alpha_rarefaction(table=table, max_depth=mindepth, phylogeny=rooted_tree)
    File "<decorator-gen-455>", line 2, in alpha_rarefaction
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      output_types, provenance)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 452, in _callable_executor_
      ret_val = self._callable(output_dir=temp_dir, **view_args)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_diversity/_alpha/_visualizer.py", line 343, in alpha_rarefaction
      'max_depth (%d).' % (steps, possible_steps))
  ValueError: Provided number of steps (10) is greater than the steps possible between min_depth and max_depth (3).

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c5/ed95acb235cca31cca024bb8fa9711

```

Okay so it doesn't like the number of steps, did this error out for the original analysis?

this is the difference:

```bash
maxdepth=$(count_table_minmax_reads.py filtered-table.tsv maximum 2>&1)

#check values
if [ "$maxdepth" -gt "75000" ]; then maxdepth="75000"; fi
if [ "$maxdepth" -gt "5000" ]; then maxsteps="250"; else maxsteps=$((maxdepth/20)); fi
```

I need to change this logic from bash to python come back to revision f34164840eead6b6d711e1577115c9a256307bbe

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - fix the rarefaction function
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
68f4be5 - Benjamin Lorentz, Wed Mar 22 10:29:49 2023 -0400 : add page for wednesday
```

#### cycle 4

```bash
4325468 - Benjamin Lorentz, Wed Mar 22 13:43:10 2023 -0400 : update ade_params_litter.yaml
```

#### Visualize Ampliseq

```bash
f341648 - Benjamin Lorentz, Wed Mar 22 16:55:22 2023 -0400 : update main.nf NOT WORKING
```


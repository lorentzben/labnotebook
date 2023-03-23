---
title: 'Updates to Visualize Ampliseq'
date: 2023-03-23T12:39:15Z
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
  
### Ade

#### Updates to Visualize Ampliseq

From Yesterday (3/22)
  
```bash
maxdepth=$(count_table_minmax_reads.py filtered-table.tsv maximum 2>&1)

#check values
if [ "$maxdepth" -gt "75000" ]; then maxdepth="75000"; fi
if [ "$maxdepth" -gt "5000" ]; then maxsteps="250"; else maxsteps=$((maxdepth/20)); fi
```

cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: 538c70e08287197450ec5b394f65338c96bf0168
slurm sub: 20070364


```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Already-up-to-date
Launching `https://github.com/lorentzben/visualize-ampliseq` [pedantic_gutenberg] DSL2 - revision: 538c70e082 [control]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf
- cause: token recognition error at: '(' @ line 821, column 77.
   axsteps="250"; else maxsteps=$((maxdepth
                                 ^

1 error
```

cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: 60d94718c6d2361c05b07b092bf80351ffa13c92
slurm sub: 20070528

```bash
Command exit status:
  1

Command output:
  WARNING The sampling depth of 4 seems too small for rarefaction

Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Traceback (most recent call last):
    File ".command.sh", line 61, in <module>
      rarefact = alpha_rarefaction(table=table, max_depth=mindepth, phylogeny=rooted_tree, steps=maxsteps)
    File "<decorator-gen-455>", line 2, in alpha_rarefaction
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
      output_types, provenance)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 452, in _callable_executor_
      ret_val = self._callable(output_dir=temp_dir, **view_args)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_diversity/_alpha/_visualizer.py", line 343, in alpha_rarefaction
      'max_depth (%d).' % (steps, possible_steps))
  ValueError: Provided number of steps (250) is greater than the steps possible between min_depth and max_depth (3).
  
  Work dir:
  /scratch/bjl34716/ade/cycle-4/work/bb/d66aacded5f1ed3335dd71c226c7cb

Tip: view the complete command output by changing to the process work dir and entering the command `cat .command.out`


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/bb/d66aacded5f1ed3335dd71c226c7cb/.command.sh", line 61, in <module>
    rarefact = alpha_rarefaction(table=table, max_depth=mindepth, phylogeny=rooted_tree, steps=maxsteps)
  File "<decorator-gen-455>", line 2, in alpha_rarefaction
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 245, in bound_callable
    output_types, provenance)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 452, in _callable_executor_
    ret_val = self._callable(output_dir=temp_dir, **view_args)
  File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/q2_diversity/_alpha/_visualizer.py", line 343, in alpha_rarefaction
    'max_depth (%d).' % (steps, possible_steps))
ValueError: Provided number of steps (250) is greater than the steps possible between min_depth and max_depth (3).`, size: 1174 (max: 255)
```
```

So my problem is I am trying to use the code from the core-metrics analysis to determine the rare cutoff, but the code is set up to look at the max value (since its something a human is going to examine) so I need to rework the chunk to use max depth and then also save the suggested depth. 

cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: b7b1273e5057844c2d462e18d85e30fa019cfb5e
slurm sub: 20070831 

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
lorentzben/visualize-ampliseq contains uncommitted changes -- cannot pull from repository
```

cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: b7b1273e5057844c2d462e18d85e30fa019cfb5e
slurm sub: 20070851

```bash
Saving 6.5 x 4.5 in image
Saving 6.5 x 4.5 in image
Saving 6.5 x 4.5 in image
Saving 6.5 x 4.5 in image
Quitting from lines 176-197 (05_report.Rmd)
Error in scan(file = file, what = what, sep = sep, quote = quote, dec = dec,  :
  line 22 did not have 2 elements
Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.table -> scan
In addition: There were 50 or more warnings (use warnings() to see the first 50)
Execution halted`, size: 1679 (max: 255)
```

The issue is that "evenness_vector.tsv" had NA values for some samples

cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: df62a69b9f614cd51ec08cd3fde4899e01d40668
slurm sub: 20072884

```bash
Completed at: 23-Mar-2023 14:06:33
Duration    : 2m 5s
CPU hours   : 1.6 (97.9% cached)
Succeeded   : 4
Cached      : 22
```

### Dockerfile for decontam

Generated lorentzb/decontam:1.0

### Todos for Tomorrow

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

### Git Commits

#### Lab Notebook

```bash
3127c78 - Benjamin Lorentz, Thu Mar 23 10:58:32 2023 -0400 : notes before lunch
d2330ad - Benjamin Lorentz, Thu Mar 23 08:43:26 2023 -0400 : added page for thursday
```

#### visualize ampliseq

```bash
aa1981d - Benjamin Lorentz, Thu Mar 23 17:06:07 2023 -0400 : add decontam dockerfile and renv lockfile
df62a69 - Benjamin Lorentz, Thu Mar 23 13:59:47 2023 -0400 : update report 04 and 05
b7b1273 - Benjamin Lorentz, Thu Mar 23 11:24:44 2023 -0400 : update main.nf
60d9471 - Benjamin Lorentz, Thu Mar 23 10:48:08 2023 -0400 : update main.nf
538c70e - Benjamin Lorentz, Thu Mar 23 10:30:50 2023 -0400 : update main.nf
```

#### cycle 4

```bash
12bd4f8 - Benjamin Lorentz, Thu Mar 23 10:32:32 2023 -0400 : update ade-cycle-4-litter.sh and viz params
```
---
title: 'Implement Mock'
date: 2023-05-19T12:30:12Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "Mock"
  - "Module"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Positive Control Analysis
  - Mock Community Investigation
  - Run a proper analysis to send to Ade
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

#### Diagnose Filterseqs

So we are having an issue with filtering the sequences we should go back and use the steps outlied by the qiime forum:

```md

You can take your existing feature-table and rep-seqs.qza file that you got from Deblur or DADA2 and work from there.

    Filter the samples you want from your feature table using the filter-sample 11 plugin.
    Use the new filtered table to remove sequences from your rep-seqs.qza file with the filter-seqs 8 plugin.
    Then you can build your new tree with this new rep-seqs file. You can also use the fragment-insertion plugin for tree building.
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: c095176eeffbaacea1a81ed3edabfba86b76e3d6
slurm job: 22918822

```bash
Caused by:
  Missing output file(s) `*.qza` expected by process `VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_FILTERSEQS (MOCK)` (note: input files are not included in the default matching set)

Command executed:

  export XDG_CONFIG_HOME="${PWD}/HOME"
  
  qiime feature-table filter-seqs \
      --i-data filtered-sequences.qza \
      --i-table MOCK.qza \
      --o-filtered-data MOCK.qza
  
  cat <<-END_VERSIONS > versions.yml
  "VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_FILTERSEQS":
      qiime2: $( qiime --version | sed '1!d;s/.* //' )
  END_VERSIONS

Command exit status:
  0

Command output:
  Saved FeatureData[Sequence] to: MOCK.qza
```
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: fd2d0e6b68e42d2c693c4813775180f5581da37a
slurm job: 22918856

```bash
 (1/1) Invalid value for '--i-table': Expected an artifact of at least type
    FeatureTable[Frequency]. An artifact of type FeatureData[Sequence] was
    provided.
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: 127adc3365ac2178c61290cef6e56e20fef648a4
slurm job: 22919203

```bash
Command output:
  Saved FeatureTable[Frequency] to: collapsed-table.qza
  Saved FeatureTable[RelativeFrequency] to: relative-table.qza

Command error:
  QIIME is caching your current deployment for improved performance. This may take a few moments and should only happen once per deployment.
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Plugin error from quality-control:
  
    "None of [Index(['MOCK167', 'MOCK288', 'MOCK323', 'MOCK71'], dtype='object')] are in the [index]"
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: e8b403c0c21d91b5927be814f994bdb34ce72b71
slurm job: 22919255

```bash
Error executing process > 'VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_EVALUATE_COMPOSITION (1)'

Caused by:
  Process `VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_EVALUATE_COMPOSITION (1)` terminated with an error exit status (1)

Command executed:

  export XDG_CONFIG_HOME="${PWD}/HOME"

  qiime taxa collapse \
      --i-table MOCK.qza \
      --i-taxonomy taxonomy.qza \
      --p-level 7 \
      --o-collapsed-table collapsed-table.qza

  qiime feature-table relative-frequency \
      --i-table collapsed-table.qza \
            --o-relative-frequency-table relative-table.qza

  # use quality control evaluate-seqs to check mock community
  qiime quality-control evaluate-composition \
      --i-expected-features expected-taxonomy.qza \
      --i-observed-features relative-table.qza \
      --o-visualization expected-observed-comparison.qzv


  cat <<-END_VERSIONS > versions.yml
  "VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_EVALUATE_COMPOSITION":
      qiime2: $( qiime --version | sed '1!d;s/.* //' )
  END_VERSIONS

Command exit status:
  1

Command output:
  Saved FeatureTable[Frequency] to: collapsed-table.qza
  Saved FeatureTable[RelativeFrequency] to: relative-table.qza

Command error:
  QIIME is caching your current deployment for improved performance. This may take a few moments and should only happen once per deployment.
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Plugin error from quality-control:

    "None of [Index(['MOCK167', 'MOCK288', 'MOCK323', 'MOCK71'], dtype='object')] are in the [index]"

  Debug info has been saved to /tmp/qiime2-q2cli-err-ka0s8_4y.log

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/58/0765a56eaf9516771696a152861f9a

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`
```
```

I updated the reftab

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: e8b403c0c21d91b5927be814f994bdb34ce72b71
slurm job: 22919255

```bash
[0a/5a394f] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[1f/efc7b8] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
Completed at: 19-May-2023 10:31:23
Duration    : 1m 9s
CPU hours   : 2.1 (99% cached)
Succeeded   : 2
Cached      : 40
```

The reports look good

#### Fix Core Metric

From the Git Issue:

Currently the coremetric python takes in a rooted tree generated from nf-core/ampliseq, however if you want to filter out the NC or Mock samples, then you are going to need to re-generate the tree again. With 2 steps:

    Filter your feature table (already implemented)
    Filter the rep-seqs.qza with filter-seqs plugin (thanks qiime2 forum)

Then we will need to update the downstream channels for rooted tree.

We need to re-generate the rooted tree, from [qiime2forum](https://forum.qiime2.org/t/should-i-filter-out-my-mock-community/10238/7):

```md
Not needed. You can take your existing feature-table and rep-seqs.qza file that you got from Deblur or DADA2 and work from there.

    Filter the samples you want from your feature table using the filter-sample 11 plugin.
    Use the new filtered table to remove sequences from your rep-seqs.qza file with the filter-seqs 8 plugin.
    Then you can build your new tree with this new rep-seqs file. You can also use the fragment-insertion plugin for tree building.

In the future, if you just want to exclude some samples from your feature-table you can either a) use the filtering options I mentioned above or simply make a new metadata file with those samples removed. With that regards, any downstream tests you do will just draw from those samples only and ignore the rest. Some tests even let you choose specific groups within your metadata file.
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: dce224aecdb8d231eb7d39950e27aa34786c8333
slurm job: 22919962

```bash
Process `VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_BUILD_ROOTED_TREE` declares 1 input channel but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 322 or see '.nextflow.log' file for more details

```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: 4dc6f716a4eac8a8fe33549fed9450dc5eab6ac2
slurm job: 22919975

```bash
Missing process or function with name 'rootedTree'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 8 or see '.nextflow.log' file for more details
```


cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: bfe9697b00e6780ce14e2bd8697af17133289404
slurm job: 22919990

```bash
Caused by:
  No such variable: filter -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/qiime2_filtersseqs.nf' at line: 25

Source block:
  def prefix = task.ext.prefix ?: "${filter}"
  
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: 00ef8e3376a888e26571388ca17431f0a8f1e560
slurm job: 22920044

```bash
Completed at: 19-May-2023 12:00:54
Duration    : 28m 10s
CPU hours   : 2.1 (29.6% cached)
Succeeded   : 23
Cached      : 21
```

cycle 4 rev: 9e604399ce43e59f868eadd67dcb95acd67b790a
visualize ampliseq rev: 00ef8e3376a888e26571388ca17431f0a8f1e560
slurm job: 22920772

```bash
[e3/d0448c] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
Completed at: 19-May-2023 12:51:47
Duration    : 1m 8s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 5
```

cycle 4 rev: 9e604399ce43e59f868eadd67dcb95acd67b790a
visualize ampliseq rev: fc777f3df7f63e40ffaece6e774eaba893aa51ff
slurm job: 22921221

```bash
Completed at: 19-May-2023 13:46:12
Duration    : 2m 8s
CPU hours   : 0.1 (30.1% cached)
Succeeded   : 2
Cached      : 5
```

cycle 4 rev: 9e604399ce43e59f868eadd67dcb95acd67b790a
visualize ampliseq rev: 94a8456b6f59f56a88aa0621309fd8b86f4a6995
slurm job: 22921370

```bash
Launching `https://github.com/lorentzben/visualize-ampliseq` [lethal_kowalevski] DSL2 - revision: 94a8456b6f [srs]
WARN: Access to undefined parameter `refSeq` -- Initialise it to a default value eg. `params.refSeq = some_value`
WARN: Access to undefined parameter `refTab` -- Initialise it to a default value eg. `params.refTab = some_value`
```

What did I break?
This should break in an expected way

cycle 4 rev: 9e604399ce43e59f868eadd67dcb95acd67b790a
visualize ampliseq rev: 9129ba2dede7863153baeaf836ccd2441c012d82
slurm job: 22921434

```bash
No such variable: contam_script_ch

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/workflows/visualize-ampliseq.nf' at line: 173 or see '.nextflow.log' file for more details
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
```


cycle 4 rev: 2a890c2e4af8270acd98f15e5c63c272ca585c37
visualize ampliseq rev: 3f1296358fc34c9878d46e893f27d066fe0a8fb1 
slurm job: 22921499

```bash
Completed at: 19-May-2023 14:11:58
Duration    : 1m 7s
CPU hours   : 2.2 (99.5% cached)
Succeeded   : 1
Cached      : 28
```

cycle 4 rev: 2a890c2e4af8270acd98f15e5c63c272ca585c37
visualize ampliseq rev: 79a8ff1435c69eacb80a9c467d7dfce734055a89
slurm job: 22921529

```bash
Completed at: 19-May-2023 14:15:10
Duration    : 1m 5s
CPU hours   : 0.5 (100% cached)
Succeeded   : 0
Cached      : 8
```

cycle 4 rev: 2a890c2e4af8270acd98f15e5c63c272ca585c37
visualize ampliseq rev: 710fcc4b0dc6d6746b092ad3f4093e544eec7648
slurm job: 22921555

```bash
Completed at: 19-May-2023 14:17:30
Duration    : 1m 5s
CPU hours   : 2.2 (100% cached)
Succeeded   : 0
Cached      : 29
```

cycle 4 rev: 31d9fc7a87f05c1d7a03703e8b1222f097b00531
visualize ampliseq rev: 710fcc4b0dc6d6746b092ad3f4093e544eec7648
slurm job: 22921582

```bash
Completed at: 19-May-2023 14:57:32
Duration    : 39m 6s
CPU hours   : 1.9 (2.7% cached)
Succeeded   : 35
Cached      : 9
```

### Todos for Next Week

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Mock Community Investigation
  - Run a proper analysis to send to Ade
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
```

#### Visualize Ampliseq

```bash
```

#### Cycle 4

```bash
```

---
title: 'Mock Community'
date: 2023-01-11T15:36:39Z
draft: false
meta_img: "images/image.png"
tags:
  - "visualize-ampliseq"
  - "rarefaction"
  - "mock microbial community"
description: "Description for the page"
---

### Todos for Today:

- Visualize Ampliseq
  - implement the alpha-rarefaction curve
  - update path in 07 report
- Generate a Mock community M&M or other and validate pipelines
- Examine some papers collected

### Question for This Week:

Can we use a mock community to describe the common taxa in the different chicken gut segments AND can we use that community to benchmark the pipeline we have developed?

### Visualize Ampliseq

#### Report 07

We need to add a process in [for this](https://docs.qiime2.org/2022.11/plugins/available/diversity/alpha-rarefaction/) to be fed into 07_report, and this can be implemented using Python

TODO check that mindepth is the correct cutoff, or if we want maxdepth 
TODO update these save commands

```python3
from qiime2.plugins.diversity.visualizers import alpha_rarefaction
```

We are going to keep the same structure of COREMETRICPYTHON but just sub in the alpha_rarefaction command as oppsed to the diversity pipeline command.

does core metric python generate the curve and we just didn't save it?

- it does not, we must generate it.

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: eede4489f254c5cb22ac8088cd9147dde3a8127d
slurm sub: 16923200

```bash
No such variable: emit

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 766
```

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: 678b7b8054b1523fe3a1c8617af1baa9b18994f3
slurm sub: 16923247

```bash
Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Traceback (most recent call last):
    File ".command.sh", line 57, in <module>
      rarefact = alpha_rarefaction(table, rooted_tree, 9000, metadata)
    File "<decorator-gen-455>", line 2, in alpha_rarefaction
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/sdk/action.py", line 208, in bound_callable
      self.signature.check_types(**user_input)
    File "/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/qiime2/core/type/signature.py", line 342, in check_types
      name, spec.qiime_type, parameter.type))
  TypeError: Parameter 'max_depth' requires an argument of type Int % Range(1, None). An argument of type Phylogeny[Rooted] was passed.

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/9c/e5e94f76c20c4160a729d422ba09ee
```

ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
visualize-ampliseq rev: 6d87ed86ceecb9c24094959ce81b1d580667eef4
slurm sub: 16936472

```bash
```


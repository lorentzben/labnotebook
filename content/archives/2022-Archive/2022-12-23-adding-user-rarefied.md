---
title: '2022 12 23 Adding User Rarefied'
date: 2022-12-23T14:19:30Z
draft: false
meta_img: "images/image.png"
tags:
  - "visualize-ampliseq"
  - "rarefaction"
description: "Description for the page"
---

### Visualize Ampliseq

#### Rarefaction

Slurm run 15947603 completed sucessfully. 

The next step is to implement the param rarefaction cutoff in the visualize ampliseq nextflow. The best way IMO is to set the default to 0, if that is detected use the min max py from ampliseq and pass those files downstream. If not 0 then run with the user provided.

We must make a new process that takes the user-provided or calculates the ampliseq rarefaction and then runs core diversity. 

visualize ampliseq rev: 3d4c07550494e0aeec323e9aafc4c1e319fa5dd5
ampliseq-benchmarking rev: 1673084bdc0089a21c45a9c36c123efa90db100d
slurm sub: 16081320

```bash
No such variable: parmas

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 29 or see '.nextflow.log' file for more details
```

visualize ampliseq rev: 49562160fe2546a0c75cba4d39f5a73b292603e7
ampliseq-benchmarking rev: 1673084bdc0089a21c45a9c36c123efa90db100d
slurm sub: 16081336

```bash
Process `RAREFACTIONPLOT` declares 2 input channels but 3 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 58 or see '.nextflow.log' file for more details
```

visualize ampliseq rev: 295b756bd40bb143558e754c7585a6834c6eb6fb
ampliseq-benchmarking rev: 1673084bdc0089a21c45a9c36c123efa90db100d
slurm sub: 16081346

```bash
 There was a problem with the command:                     
   (1/1?) --p-sampling-depth option requires an argument
```

 /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/49/c4562b6a02058a35ab1f0a52670d37

visualize ampliseq rev: afbcf418c4ca1f5d59c9ab902420bc4f70b744d4
ampliseq-benchmarking rev: 1673084bdc0089a21c45a9c36c123efa90db100d
slurm sub: 16081354

```bash
succeeded with default params
```

Testing with a depth of 10,000

visualize ampliseq rev: afbcf418c4ca1f5d59c9ab902420bc4f70b744d4
ampliseq-benchmarking rev: 1da6e350521b02e47f2d82ef4bb9a7c3e376a559
slurm sub: 16081367

```bash
parameter rare was in the wrong spot
```

visualize ampliseq rev: afbcf418c4ca1f5d59c9ab902420bc4f70b744d4
ampliseq-benchmarking rev: 1a20ccd63bcdc0516fb5e4edcde23770f5de6f31
slurm sub: 16081370

```bash
/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is dep$
  import pandas.util.testing as pdt
/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/sklearn/metrics/pairwise.py:1761: DataConversionWarning: Data was co$
  warnings.warn(msg, DataConversionWarning)
/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/stats/ordination/_principal_coordinate_analysis.py:152: Runtim$
  RuntimeWarning
/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/stats/ordination/_principal_coordinate_analysis.py:152: Runtim$
  RuntimeWarning
/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/stats/ordination/_principal_coordinate_analysis.py:152: Runtim$
  RuntimeWarning
```

lowering rarefaction depth

visualize ampliseq rev: afbcf418c4ca1f5d59c9ab902420bc4f70b744d4
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16081380

```bash

```

We can possibly wrap the qiime call in python code to use the warnings package to ignore the warnings [seen here](https://www.tutorialexample.com/beginner-guide-to-disable-or-ignore-python-warnings-python-tutorial/)

TODO:
  check downstream diversity files.
  04
  05
  06
  07
  09
  10
  12

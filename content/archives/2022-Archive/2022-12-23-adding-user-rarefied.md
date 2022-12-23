---
title: '2022 12 23 Adding User Rarefied'
date: 2022-12-23T14:19:30Z
draft: false
meta_img: "images/image.png"
tags:
  - "one tag"
  - "another tag"
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

```

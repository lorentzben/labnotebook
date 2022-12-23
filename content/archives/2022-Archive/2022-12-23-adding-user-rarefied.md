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

visualize ampliseq rev: 5bbe71bf713f69204402fc0a74a47e4024e62c74
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082681

```bash
no such variable rare_val
```

visualize ampliseq rev: 7a649457b3ec0c840304582863a8419b32389b38
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082687

```bash

```

visualize ampliseq rev: 5a28ff3c0ec1a84efbc903b6b8e91ca613eb2868
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082696

```bash
No such variable: rare_val

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 177 or see $
[-        ] process > ORDERIOI        -
[-        ] process > RAREFACTIONPLOT -
```

visualize ampliseq rev: 5c88c6b4100448ad716d226190c0c1cc830439e0
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082706

```bash
No such variable: rare_val

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 177 or see $
[-        ] process > ORDERIOI        -
[-        ] process > RAREFACTIONPLOT -
```

visualize ampliseq rev: 9074fb626d6512e2f1d14e187c5aa1cb07e46c6a
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082719

```bash

```

visualize ampliseq rev: 3ffc245ed26fd7b02e674b32ddfe7b299dadd45d
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082734

```bash
Caused by:
  Not a valid path value type: java.lang.Integer (9000)
```

visualize ampliseq rev: 4b1451ec1f11c96888ff16fed997bc5e966717d9
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082741

```bash
Access to 'COREMETRIC.out' is undefined since the process 'COREMETRIC' has not been invoked before accessing $

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 69 or see 
[-        ] process > ORDERIOI                       -
[-        ] process > RAREFACTIONPLOT                -
[-        ] process > REPORT01BARPLOT                -
[-        ] process > REFORMATANDQZATAX              -
[-        ] process > GENERATEBIOMFORGRAPHLAN        -
```

visualize ampliseq rev: fbd72c3c387f45dbd6888136aaa180d14574c924
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082868

```bash
  status : 255
  message:
    FATAL:   While making image from oci registry: error fetching image to cache: failed to get checksum for docker://docker:#lorentzb/automate_16_nf:2.0: unable to parse image name docker://docker:#lorentzb/automate_16_nf:2.0: invalid reference format




[ea/1734be] Cached process > REPORT02GRAPHLANPHYLOGENETICTREE (1)
[d9/331ec3] Cached process > LEFSEANALYSIS (1)
```

visualize ampliseq rev: fbd72c3c387f45dbd6888136aaa180d14574c924
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082955

```bash
FATAL:   While making image from oci registry: error fetching image to cache: failed to get checksum for docker://docker:#lorentzb/automate_16_nf:2.0: unable to parse image name docker://docker:#lorentzb/automate_16_nf:2.0: invalid reference format
```

visualize ampliseq rev: c11d532c1db4f4e6a72fd313b94a0358f8765efe
ampliseq-benchmarking rev: 206827a145d901fa96b94695644a688d4fac6241
slurm sub: 16082958

```bash
#!/usr/bin/env python3
  
  print(9000)
  
  # if (( 9000 == 0 )); then 
  
  #     uncompress_table='results/qiime2/abundance_tables/feature-table.tsv'
  
  #     mindepth=$(python3 count_table_minmax_reads.py "$uncompress_table" minimum 2>&1)
  #     if [ "$mindepth" -gt "10000" ]; then echo $mindepth >"Use the sampling depth of $mindepth for rarefaction.txt" ; fi
  #     if [ "$mindepth" -lt "10000" -a "$mindepth" -gt "5000" ]; then echo $mindepth >"WARNING The sampling depth of $mindepth is quite small for rarefaction.txt" ; fi
  #     if [ "$mindepth" -lt "5000" -a "$mindepth" -gt "1000" ]; then echo $mindepth >"WARNING The sampling depth of $mindepth is very small for rarefaction.txt" ; fi
  #     if [ "$mindepth" -lt "1000" ]; then echo $mindepth >"WARNING The sampling depth of $mindepth seems too small for rarefaction.txt" ; fi
  
  #     qiime diversity core-metrics-phylogenetic     #         --m-metadata-file rarefaction_metadata.tsv     #         --i-phylogeny results/qiime2/phylogenetic_tree/rooted-tree.qza     #         --i-table feature-table.qza     #         --p-sampling-depth $mindepth     #         --output-dir diversity_core     #         --p-n-jobs-or-threads 1     #         --verbose
  # else
  #     qiime diversity core-metrics-phylogenetic     #         --m-metadata-file rarefaction_metadata.tsv     #         --i-phylogeny results/qiime2/phylogenetic_tree/rooted-tree.qza     #         --i-table feature-table.qza     #         --p-sampling-depth 9000     #         --output-dir diversity_core     #         --p-n-jobs-or-threads 1     #         --verbose
  # fi

Command exit status:
  0

Command output:
  9000
```

So the python code can take in values and paths no problem, the next step is to add in the steps 
to actually run the process and save the file to disk

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

---
title: 'Visualize Ampliseq Custom Rarefaction'
date: 2023-01-04T14:03:38Z
draft: false
meta_img: "images/image.png"
tags:
  - "visualize-ampliseq"
  - "core-metric"
  - "rarefaction"
description: "Description for the page"
---

### Todos for tomorrow:

- Visualize Ampliseq
  - ensure all diversity files downstream are from the newly generated core-metric
    - search for results/diversity and change to emit etc.
- Generate a Mock community M&M or other and validate pipelines
- Open Up Space on the Lacie drive

### Open Up Space on Lacie Drive

Started windirstat at 9am 

### Visualize Ampliseq

#### Checking Downstream uses of core metric results

visualize-ampliseq rev: 5491747280ad4641ebe17a368de7d02e4f8b8516
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16448309

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
    File ".command.sh", line 50
      core = diversity.pipelines.core_metrics_phylogenetic(unrarefied_table, rooted_tree, mindepth, metadata)
                                                                                                            ^
  IndentationError: unindent does not match any outer indentation level

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/33/3efc89d43ddd096a75943146c4fd6c
```

visualize-ampliseq rev: 835ae525e7cf7978d54335ffd4f1a8b6866d7301
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16448327

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
    File ".command.sh", line 53
      core = diversity.pipelines.core_metrics_phylogenetic(unrarefied_table, rooted_tree, mindepth, metadata)
                                                                                                            ^
  IndentationError: unindent does not match any outer indentation level

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/a4/653fc70b3d70a2f127df8a4526a19b
```

visualize-ampliseq rev: 6fb77fe68df25cae7dc5211958d9b6ab07144c72
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16448346

```bash
suceeded
python core metric:  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/64/305d11cbbaf4e4d01845d5fa6c1e1f
```

I want to output the tsv versions of the diversity measures and the pcoa/distance.

we can make a function that will take in a dir of the qza's and output the tsvs.

We can pass the dir of tsv's and run as each and then use the .collect() at the out to emit the tsv's together. 

Testing qza to tsv process

visualize-ampliseq rev: 728a572b4834eb8c96140702ebe6c8cfb81838bb
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16470441

```bash
No such variable: table_qza

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 59 or see '.nextflow.log' file for more details
[-        ] process > ORDERIOI        -
[-        ] process > RAREFACTIONPLOT -
```
visualize-ampliseq rev: 1943e2803e8182f737ba7fae836e2033f14e8146
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16470644

```bash
ordered item of interest : ordered_item_of_interest.csv
outdir   : /work/sealab/bjl34716/ampliseq-benchmarking/rarefaction_test/
rarefaction depth : 9000
profile : slurm,singularity

No such variable: tax_qza

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 59 or see '.nextflow.log' file for more details
[-        ] process > ORDERIOI 
```

visualize-ampliseq rev: aad2cd6fdcfa9ebcd8f2d258aa468abb0df24910
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16470676

```bash
suceeded but no qza to tsv 
```

I added a diagnostic view 

visualize-ampliseq rev: 000b1338f367ea7902cab1723b49d9b9c974436d 
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16471243

```bash
Error executing process > 'QZATOTSV (1)'

Caused by:
  No such variable: Exception evaluating property 'split' for nextflow.util.BlankSeparatedList, Reason: groovy.lang.MissingPropertyException: No such property: split for class: nextflow.processor.TaskPath -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 239
```

visualize-ampliseq rev: 2cd9da5e4669ced14a6c6b62f9b8e7120a03e446
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16471842

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [angry_yalow] DSL2 - revision: 2cd9da5e46 [rarefact]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf
- cause: token recognition error at: '\.' @ line 255, column 30.
       filename = str($diversity\.split('.')[0]+'.tsv')
                                ^

1 error
```

visualize-ampliseq rev: 2a1b7fab522007ac2b1958a29cc4849249cbba3d
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16476010

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
    File ".command.sh", line 15
      artifact_name = bray_curtis_distance_matrix.qza jaccard_distance_matrix.qza unweighted_unifrac_distance_matrix.qza weighted_unifrac_distance_matrix.qza
                                                                            ^
  SyntaxError: invalid syntax

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/bb/93be2d8ca6cd06ec905b87fd4901be
```


visualize-ampliseq rev: 6e56c083f99b5bbaffb432c3863855c73b71dcc5
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16476849

```bash
V I S U A L I Z E   P I P E L I N E
===================================
input    : /scratch/bjl34716/nf_dev/ampliseq-benchmark/rarefaction_test
metadata : /scratch/bjl34716/nf_dev/ampliseq-benchmark/rarefaction_test/rarefaction_metadata.tsv
item of interest : condition
ordered item of interest : ordered_item_of_interest.csv
outdir   : /work/sealab/bjl34716/ampliseq-benchmarking/rarefaction_test/
rarefaction depth : 9000
profile : slurm,singularity

No such variable: diversity

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 231 or see '.nextflow.log' f$[ERROR] Terminal initialization failed; falling back to unsupported
```

visualize-ampliseq rev: cbac8af477afd0fb8a0777b9086a52c403f9dea7
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16477426

```bash
Caused by:
  Not a valid path value type: groovyx.gpars.dataflow.DataflowBroadcast (DataflowBroadcast around DataflowStream[?])
```

visualize-ampliseq rev: 218f2541da81ba41c6ff0e3d34671b03feaa3cf3
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16479255

```bash
same error
```

visualize-ampliseq rev: 664743d0caece36f73e356270f00ffa47450412d
ampliseq-benchmark rev: 206827a145d901fa96b94695644a688d4fac6241
slurm: 16479596

```bash
```

### Todos for tomorrow:

- Visualize Ampliseq
  - ensure all diversity files downstream are from the newly generated core-metric
    - search for results/diversity and change to emit etc.
  - fix qza to tsv
- Generate a Mock community M&M or other and validate pipelines

### Git Commits

#### Lab notebook

```bash
530cfad - Benjamin Lorentz, Wed Jan 4 09:06:03 2023 -0500 : inital commit for the day
```

#### Visualize-Ampliseq

```bash
664743d - Benjamin Lorentz, Wed Jan 4 17:00:01 2023 -0500 : update main.nf
218f254 - Benjamin Lorentz, Wed Jan 4 16:42:36 2023 -0500 : update main.nf
cbac8af - Benjamin Lorentz, Wed Jan 4 16:19:49 2023 -0500 : update main.nf
6e56c08 - Benjamin Lorentz, Wed Jan 4 15:58:14 2023 -0500 : update main.nf
2a1b7fa - Benjamin Lorentz, Wed Jan 4 15:31:20 2023 -0500 : update main.nf
2cd9da5 - Benjamin Lorentz, Wed Jan 4 15:15:30 2023 -0500 : update main.nf
000b133 - Benjamin Lorentz, Wed Jan 4 14:50:35 2023 -0500 : update main.nf
aad2cd6 - Benjamin Lorentz, Wed Jan 4 14:39:11 2023 -0500 : update main.nf
1943e28 - Benjamin Lorentz, Wed Jan 4 14:31:53 2023 -0500 : update main.nf
728a572 - Benjamin Lorentz, Wed Jan 4 14:19:15 2023 -0500 : update main.nf
6fb77fe - Benjamin Lorentz, Wed Jan 4 10:24:13 2023 -0500 : update main.nf
835ae52 - Benjamin Lorentz, Wed Jan 4 10:10:05 2023 -0500 : update main.nf
```


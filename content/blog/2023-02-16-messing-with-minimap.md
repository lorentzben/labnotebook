---
title: 'Messing With Minimap'
date: 2023-02-16T14:50:11Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - create a minimap process (either concat or separate)
    - check for read loss (does it match the paper?)
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Class
  - read pages 168-178 before class tomorrow

### gg-catalog

#### why do we only have one process?

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 140806a8417d0ec73a9486084aaf1ed3f90e6a07
slurm sub: 19081711

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'collect'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 124 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or s
ee '.nextflow.log' file for more details
[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 4fb85dc5a725273b6aa0cf413f59020a114bce74
slurm sub: 19082563

```bash
[[id:SRR15214153, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR19683890, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19683890, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19683890, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19732729, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19732729, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19732729, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19683891, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19683891, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19683891, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19736685, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19736685, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19736685, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19726169, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19726169, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19726169, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19732514, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
[[id:SRR19732514, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
[[id:SRR19732514, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
[['id':'SRR15214153', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fastq.gz, ['id':'SRR19683890', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.fastq.gz, ['id':'SRR19732729', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/a3/c70037853d4f88163ea1c618a68d60/SRR19732729.fastq.gz, ['id':'SRR19683891', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/52/bb6f1fa9fb318ce7d5d2b310f7e3f8/SRR19683891.fastq.gz, ['id':'SRR19726169', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/1d/c59eb7024e0a571948d79f0eec1d88/SRR19726169.fastq.gz, ['id':'SRR19736685', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/59/57c131e5fb722bd82ff40e4a9888d1/SRR19736685.fastq.gz, ['id':'SRR19732514', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/ba/34a78b499f64f76e7272bd6635a6ee/SRR19732514.fastq.gz]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 565ce5d3f7ee2c7642824ae55b050b300c9c10aa
slurm sub: 19085359

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4udUeIHyYwKqn7
executor >  slurm (1)
[ba/34a78b] process > FILTLONG (SRR19732514)       [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)           [100%] 1 of 1, cached: 1 ✔
[c3/1a623b] process > MINIMAP2_ALIGN (SRR19683890) [  0%] 0 of 1
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR19683890, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19732729, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19683891, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19736685, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19726169, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19732514, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
[[id:SRR19683890, single_end:true], [scratch, bjl34716, nf_dev, gg-catalog, work, 34, 7e432c4a79d99155b72110f4f0496f, SRR19683890.fastq.gz]]
```

This is still only taking in one thing, but maybe theres a way to mod it. 

I think we don't want flatten!

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: a6ea2d1f4496c135b5a3129910c3eddaa075878e
slurm sub: 19086785

```bash
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR19683890, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19732729, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19683891, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19736685, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19726169, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19732514, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fastq.gz]
[['id':'SRR15214153', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fastq.gz, ['id':'SRR19683890', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.fastq.gz, ['id':'SRR19732729', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/a3/c70037853d4f88163ea1c618a68d60/SRR19732729.fastq.gz, ['id':'SRR19683891', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/52/bb6f1fa9fb318ce7d5d2b310f7e3f8/SRR19683891.fastq.gz, ['id':'SRR19726169', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/1d/c59eb7024e0a571948d79f0eec1d88/SRR19726169.fastq.gz, ['id':'SRR19736685', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/59/57c131e5fb722bd82ff40e4a9888d1/SRR19736685.fastq.gz, ['id':'SRR19732514', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/ba/34a78b499f64f76e7272bd6635a6ee/SRR19732514.fastq.gz]
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 155402f29ebef668d38e608d34c77ede337dc0e0
slurm sub: 19088067

```bash
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR19683890, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19732729, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19683891, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19736685, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19726169, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19732514, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
[['id':'SRR19683890', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR196838$[[id:null, single_end:null], [/scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.fastq.gz]]
```

looks oddly similar

This isn't it either since the name is null

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 2c498b911f1384bce1dbf9b4febc14620782de2a 
slurm sub: 19090548

```bash
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR19683890, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19732729, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19683891, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19736685, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19726169, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19732514, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
[[id:SRR15214153, single_end:true], [/scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fastq.gz]]
[[id:SRR19683890, single_end:true], [/scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.fastq.gz]]
[[id:SRR19732729, single_end:true], [/scratch/bjl34716/nf_dev/gg-catalog/work/a3/c70037853d4f88163ea1c618a68d60/SRR19732729.fastq.gz]]
[[id:SRR19683891, single_end:true], [/scratch/bjl34716/nf_dev/gg-catalog/work/52/bb6f1fa9fb318ce7d5d2b310f7e3f8/SRR19683891.fastq.gz]]
[[id:SRR19736685, single_end:true], [/scratch/bjl34716/nf_dev/gg-catalog/work/59/57c131e5fb722bd82ff40e4a9888d1/SRR19736685.fastq.gz]]
[[id:SRR19726169, single_end:true], [/scratch/bjl34716/nf_dev/gg-catalog/work/1d/c59eb7024e0a571948d79f0eec1d88/SRR19726169.fastq.gz]]
[[id:SRR19732514, single_end:true], [/scratch/bjl34716/nf_dev/gg-catalog/work/ba/34a78b499f64f76e7272bd6635a6ee/SRR19732514.fastq.gz]]
[['id':'SRR15214153', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fastq.gz, ['id':'SRR19683890', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.fastq.gz, ['id':'SRR19732729', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/a3/c70037853d4f88163ea1c618a68d60/SRR19732729.fastq.gz, ['id':'SRR19683891', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/52/bb6f1fa9fb318ce7d5d2b310f7e3f8/SRR19683891.fastq.gz, ['id':'SRR19736685', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/59/57c131e5fb722bd82ff40e4a9888d1/SRR19736685.fastq.gz, ['id':'SRR19726169', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/1d/c59eb7024e0a571948d79f0eec1d88/SRR19726169.fastq.gz, ['id':'SRR19732514', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/ba/34a78b499f64f76e7272bd6635a6ee/SRR19732514.fastq.gz]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 2ae5ce9325a8fccbf84a6489f1b35ace7f9d021c
slurm sub: 19092594


```bash
[[[id:SRR15214153, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.$[[[id:SRR19683890, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.$
[[[id:SRR19683891, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/52/bb6f1fa9fb318ce7d5d2b310f7e3f8/SRR19683891.$
[[[id:SRR19736685, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/59/57c131e5fb722bd82ff40e4a9888d1/SRR19736685.$[[[id:SRR19732729, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/a3/c70037853d4f88163ea1c618a68d60/SRR19732729.$[[[id:SRR19726169, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/1d/c59eb7024e0a571948d79f0eec1d88/SRR19726169.$[[[id:SRR19732514, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/ba/34a78b499f64f76e7272bd6635a6ee/SRR19732514.$
[['id':'SRR15214153', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR152141$


```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: ddfa0f2d807953c5d298853a47481028720985b9
slurm sub: 19092820


```bash
No signature of method: nextflow.script.WorkflowBinding.String() is applicable for argument types: () values: []
Possible solutions: toString(), toString(), toString(), print(java.lang.Object), print(java.io.PrintWriter), stream()
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: a7bb27dd14dbb81bdf3e1aeab0ee7bca1913fb11
slurm sub: 19092923


```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [furious_brahmagupta] DSL2 - revision: a7bb27dd14 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 67, column 9.
   workflow{
           ^

1 error
```

It didnt like that

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: d577383123c6cdcd6dc1f433f31cc9c935db8d61
slurm sub:  19093048


```bash
Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [furious_brahmagupta] DSL2 - revision: a7bb27dd14 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 67, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 8d62d8e55e394f1e0382e502cee34fc3e54a261c
slurm sub:  19093190


```bash
a7bb27dd14 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 67, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 26a2c72287625a5ba8e08c1f5b0258fa29f33379
slurm sub:  19093273


```bash
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR19683890, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19732729, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19683891, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19736685, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19726169, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19732514, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
Execution cancelled -- Finishing pending tasks before exit
WARN: Input tuple does not match input set cardinality declared by process `MINIMAP2_ALIGN` -- offending value: DataflowBroadcast around DataflowStream[?]
Execution aborted due to an unexpected error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 
slurm sub:  


```bash
```

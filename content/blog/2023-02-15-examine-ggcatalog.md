---
title: 'Examine Ggcatalog'
date: 2023-02-15T15:30:29Z
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
    - follow up on slurm process 18670379 (2/9/23)
    - create a minimap process (either concat or separate)
      - read about what a meta map is and if we can implement it
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
  
### gg-catalog-nf

#### examin slurm 18670379 (2/9/23)

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 480361d1c9e2f273bbfbe290d489a985f1a28940
slurm sub: 18670379

```bash
Command error:
  [WARNING][1;31m Indexing parameters (-k, -w or -H) overridden by parameters used in the prebuilt index.[0m
  [WARNING][1;31m For a multi-part index, no @SQ lines will be outputted. Please use --split-prefix.[0m
  [M::main::63.751*0.23] loaded/built the index for 507 target sequence(s)
  [M::mm_mapopt_update::67.003*0.27] mid_occ = 500
  [M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 507
  [M::mm_idx_stat::69.171*0.29] distinct minimizers: 113152470 (39.56% are singletons); average occurrences: 6.599; average spacing: 5.372; total length: 4011685380
  [E::sam_parse1] no SQ lines present in the header
  [W::sam_read1_sam] Parse error at line 1758
  samtools sort: truncated file. Aborting
  [main_samview] fail to read the header from "-".

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/7d/00357575ad21eaf2c570d99e676a00
```

The filtering and indexing steps worked fine, but the align step failed. I want to pass the concatenated fasta in as opposed to the index. 

#### Pass reads in as opposed to index

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: ad53d79ad2690e43ab66d0da6e6832b8aa2c80c6
slurm sub: 19014151

```bash
[[id:combined, single_end:true], [/scratch/bjl34716/gg-catalog/refs/concat-gal-zea-glycine.fna.gz]]
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fas$[[id:combined, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/fa/8985309130258a2e58dc2c8d66168e/concat-gal-zea-gly$Execution cancelled -- Finishing pending tasks before exit
[[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.fas$Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/minimap2/align/main.nf' at line: 2 $
[a3/c70037] Cached process > FILTLONG (SRR19732729)
```

I need to map the reads like I did for the other channels

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 402c280b9d0c3f465ca48092daf356f60660fdb0
slurm sub: 19015137

```bash
Command error:
  [M::mm_idx_gen::75.742*1.60] collected minimizers
  [M::mm_idx_gen::82.654*1.95] sorted minimizers
  [WARNING][1;31m For a multi-part index, no @SQ lines will be outputted. Please use --split-prefix.[0m
  [M::main::82.654*1.95] loaded/built the index for 507 target sequence(s)
  [M::mm_mapopt_update::85.186*1.92] mid_occ = 500
  [M::mm_idx_stat] kmer size: 19; skip: 19; is_hpc: 0; #seq: 507
  [M::mm_idx_stat::86.603*1.91] distinct minimizers: 203018761 (87.88% are singletons); average occurrences: 1.970; average spacing: 10.030; total length: 4011685380
  [E::sam_parse1] no SQ lines present in the header
  [W::sam_read1_sam] Parse error at line 1678
  samtools sort: truncated file. Aborting
  [main_samview] fail to read the header from "-".

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/c2/bc40ecc6bc16c600c007d9641b1bc9
```

What is the --split-prefix?



gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 37a7a60e144fccc14ef18c70b5e16a4351d20532
slurm sub: 19018732

```bash
 minimap2 \
      -ax map-hifi --split-prefix \
      -t 6 \
      "concat-gal-zea-glycine.fna.gz" \
      "SRR15214153.fastq.gz" \
       \
      -L \
      -a | samtools sort | samtools view -@ 6 -b -h -o SRR15214153.bam
      
Command error:
  [ERROR] failed to open file '6': No such file or directory
  samtools sort: failed to read header from "-"
  [main_samview] fail to read the header from "-".

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/97/52995fc0450b0c4af69a6ded78df8f

```

Based on [this github reply](https://github.com/lh3/minimap2/issues/548#issuecomment-580545383) I think you need to tell the minimap what to call the prefixes. 

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 0274457dfb83a74a26d4d0edb9d9b1f73e1e0066
slurm sub: 19020095

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5NVRa98uwzqOJx
executor >  slurm (1)
[59/57c131] process > FILTLONG (SRR19736685)       [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)           [100%] 1 of 1, cached: 1 ✔
[9c/44d690] process > MINIMAP2_ALIGN (SRR15214153) [100%] 1 of 1 ✔
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/9c/44d690451cc63e56e300d6c1ec3211/SRR15214153.bam]Completed at: 15-Feb-2023 16:13:40
Duration    : 1h 19m 6s
CPU hours   : 353.7 (97.8% cached)
Succeeded   : 1
Cached      : 8
```

It seems that minimap2 is happy with this parameter submission, it suceeded! but only for one sequence ...

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 0a87e61a1bfdf4156ad98e99c77776ede436b92b
slurm sub: 19027073

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or s$Access to 'FILTLONG.out' is undefined since the process 'FILTLONG' has not been invoked before accessing the output attribute

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 105 or see '.nextflow.log' file f$No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or $[ERROR] Terminal initialization failed; falling back to unsupported
java.lang.IllegalStateException: Shutdown in progress
        at java.base/java.lang.ApplicationShutdownHooks.add(ApplicationShutdownHooks.java:66)
        at java.base/java.lang.Runtime.addShutdownHook(Runtime.java:213)
        at jline.internal.ShutdownHooks.addHook(ShutdownHooks.java:79)
        at jline.internal.ShutdownHooks.add(ShutdownHooks.java:43)
        at jline.TerminalSupport.init(TerminalSupport.java:46)
        at jline.UnixTerminal.init(UnixTerminal.java:47)
        at jline.TerminalFactory.create(TerminalFactory.java:101)
        at jline.TerminalFactory.get(TerminalFactory.java:159)
        at nextflow.trace.AnsiLogObserver.renderProcesses(AnsiLogObserver.groovy:249)
        at nextflow.trace.AnsiLogObserver.renderProgress(AnsiLogObserver.groovy:289)
        at nextflow.trace.AnsiLogObserver.render0(AnsiLogObserver.groovy:184)
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 56c3a27678cc49309945413f8b348fcb5bca7bda
slurm sub: 19027202

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `MINIMAP2_ALIGN` declares 5 input channels but 7 were specified
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: be29e419848934c2fd3875e9f658c1887f7ee75d
slurm sub: 19027371

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: Exception evaluating property 'out' for nextflow.script.ChannelOut, Reason: groovy.lang.MissingPropertyException: No such property: out for class: groovyx.gpars.dataflow.DataflowBroadcast

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 113 or see '.nextflow.log' file for more details
[-        ] process > MINIMAP2_INDEX -
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: d7fe19d29de454daf670c6db9fb88ad6535e4a2a
slurm sub: 19028001

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: bam

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 115 or see '.nextflow.log' file for more details
[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
[-        ] process > MINIMAP2_ALIGN -
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: fa840eda6d59dbc673e367355165c7a19cedd3c7
slurm sub: 19028366

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2bbRPUSUTYfIAT
[ba/34a78b] process > FILTLONG (SRR19732514)       [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)           [100%] 1 of 1, cached: 1 ✔
[9c/44d690] process > MINIMAP2_ALIGN (SRR15214153) [100%] 1 of 1, cached: 1 ✔
Completed at: 15-Feb-2023 16:40:52
Duration    : 1m 6s
CPU hours   : 353.7 (100% cached)
Succeeded   : 0
Cached      : 9
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: be4f4b9b09bd5d1f950d978b624330a5f60ee2ad
slurm sub: 19028800

```bash
[fa/898530] process > MINIMAP2_INDEX (1)           [100%] 1 of 1, cached: 1 ✔
[9c/44d690] process > MINIMAP2_ALIGN (SRR15214153) [100%] 1 of 1, cached: 1 ✔

Completed at: 15-Feb-2023 16:43:53
Duration    : 1m 5s
CPU hours   : 353.7 (100% cached)
Succeeded   : 0
Cached      : 9
```

[This](https://bioinformatics.stackexchange.com/questions/18549/nextflow-dsl-v2-how-to-best-synchronize-multiple-outputs-from-a-single-proces) might be a helpful thing

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: de0eec0100852afbd5a2128d471fdaa746fc595
slurm sub: 19029689

```bash
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fastq.gz]
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/9c/44d690451cc63e56e300d6c1ec3211/SRR15214153.bam]
[[id:SRR19732729, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/a3/c70037853d4f88163ea1c618a68d60/SRR19732729.fastq.gz]
[[id:SRR19683891, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/52/bb6f1fa9fb318ce7d5d2b310f7e3f8/SRR19683891.fastq.gz]
[[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/34/7e432c4a79d99155b72110f4f0496f/SRR19683890.fastq.gz]
[[id:SRR19726169, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/1d/c59eb7024e0a571948d79f0eec1d88/SRR19726169.fastq.gz]
[[id:SRR19736685, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/59/57c131e5fb722bd82ff40e4a9888d1/SRR19736685.fastq.gz]
[[id:SRR19732514, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/ba/34a78b499f64f76e7272bd6635a6ee/SRR19732514.fastq.gz]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 4a412d8c45d800ed3c8325eed69e2d8487fabffd
slurm sub: 19030831

```bash
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: collect

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 116 or see '.nextflow.log' file for more details
[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: fcc274d678b747f29452469806dd9337fdadf29a
slurm sub: 19031298

```bash
```

I want it to output 7 things and then process them one by one.

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: dbbafe4c34186aa5b5f9dcc3f5196d92f86a77e6
slurm sub: 19032936

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'collect'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 120 or see '.nextflow.log' file for more details
No such variable: info
```

### Git Commits

#### Lab Notebook 

```bash
a54eb04 - Benjamin Lorentz, Wed Feb 15 15:26:28 2023 -0500 : added notes about minimap2
6e8e085 - Benjamin Lorentz, Wed Feb 15 10:32:32 2023 -0500 : add page for wednesday
```

#### gg-catalog-nf

```bash
dbbafe4 - Benjamin Lorentz, Wed Feb 15 17:02:38 2023 -0500 : update main.nf
fcc274d - Benjamin Lorentz, Wed Feb 15 16:55:45 2023 -0500 : update main.nf
4a412d8 - Benjamin Lorentz, Wed Feb 15 16:52:51 2023 -0500 : update main.nf
de0eec0 - Benjamin Lorentz, Wed Feb 15 16:46:40 2023 -0500 : update main.nf
be4f4b9 - Benjamin Lorentz, Wed Feb 15 16:42:45 2023 -0500 : update main.nf
fa840ed - Benjamin Lorentz, Wed Feb 15 16:39:50 2023 -0500 : update main.nf
d7fe19d - Benjamin Lorentz, Wed Feb 15 16:36:22 2023 -0500 : update main.nf
743b3d3 - Benjamin Lorentz, Wed Feb 15 16:35:42 2023 -0500 : update main.nf
be29e41 - Benjamin Lorentz, Wed Feb 15 16:31:50 2023 -0500 : update main.nf
56c3a27 - Benjamin Lorentz, Wed Feb 15 16:29:22 2023 -0500 : update main.nf
0a87e61 - Benjamin Lorentz, Wed Feb 15 16:27:02 2023 -0500 : update main.nf
4787adc - Benjamin Lorentz, Wed Feb 15 16:22:07 2023 -0500 : update main.nf
:...skipping...
dbbafe4 - Benjamin Lorentz, Wed Feb 15 17:02:38 2023 -0500 : update main.nf
fcc274d - Benjamin Lorentz, Wed Feb 15 16:55:45 2023 -0500 : update main.nf
4a412d8 - Benjamin Lorentz, Wed Feb 15 16:52:51 2023 -0500 : update main.nf
de0eec0 - Benjamin Lorentz, Wed Feb 15 16:46:40 2023 -0500 : update main.nf
be4f4b9 - Benjamin Lorentz, Wed Feb 15 16:42:45 2023 -0500 : update main.nf
fa840ed - Benjamin Lorentz, Wed Feb 15 16:39:50 2023 -0500 : update main.nf
d7fe19d - Benjamin Lorentz, Wed Feb 15 16:36:22 2023 -0500 : update main.nf
743b3d3 - Benjamin Lorentz, Wed Feb 15 16:35:42 2023 -0500 : update main.nf
be29e41 - Benjamin Lorentz, Wed Feb 15 16:31:50 2023 -0500 : update main.nf
56c3a27 - Benjamin Lorentz, Wed Feb 15 16:29:22 2023 -0500 : update main.nf
0a87e61 - Benjamin Lorentz, Wed Feb 15 16:27:02 2023 -0500 : update main.nf
4787adc - Benjamin Lorentz, Wed Feb 15 16:22:07 2023 -0500 : update main.nf
0274457 - Benjamin Lorentz, Wed Feb 15 14:52:44 2023 -0500 : update modules.config
37a7a60 - Benjamin Lorentz, Wed Feb 15 14:40:33 2023 -0500 : update modules.config
402c280 - Benjamin Lorentz, Wed Feb 15 14:12:33 2023 -0500 : update main.nf
ad53d79 - Benjamin Lorentz, Wed Feb 15 14:07:51 2023 -0500 : update main.nf
```
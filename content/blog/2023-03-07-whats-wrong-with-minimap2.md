---
title: 'What's Wrong With Minimap2'
date: 2023-03-07T13:56:43Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---


### Todos for Today


- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
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

#### Minimap2 by hand

From 02-23:

It's weird that the mapped reads do not decrease at all, I am going to look through the logfiles to see what it says. 

What was the original data labeled as?

So maybe my mapping was the issue? 

```bash
minimap2 chicken_and_feed_genomes.fa Duodenum.fq.gz -o Duodenum.fq.gz.host.paf  -x map-hifi -t 40 
```

I want to look at this command vs the one the pipeline completed and see what the difference is.


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: ce88e8c67c6e309dab3403d2d22a3b9d3138b49d
slurm sub: 19737647 

```bash
[59/57c131] process > FILTLONG (SRR19736685)         [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)             [100%] 1 of 1, cached: 1 ✔
[d4/783587] process > MINIMAP2_ALIGN (SRR19732514)   [100%] 7 of 7, cached: 7 ✔
[03/84e265] process > SAMTOOLS_FASTQ (SRR19736685)   [100%] 7 of 7, cached: 7 ✔
[30/87d180] process > SAMTOOLS_FASTA (SRR19732514)   [100%] 7 of 7, cached: 7 ✔
[20/4394fe] process > SEQKIT_STATS (SRR19726169)     [100%] 7 of 7, cached: 7 ✔
[bd/fde0b4] process > CSVTK_CONCAT (raw)             [100%] 1 of 1, cached: 1 ✔
[42/e00011] process > SEQKIT_STATS_FILT (SRR19736... [100%] 7 of 7, cached: 7 ✔
[f2/ad6f8c] process > CSVTK_CONCAT_FILT (filtlong)   [100%] 1 of 1, cached: 1 ✔
[c8/a59441] process > SEQKIT_STATS_UNMAP (SRR1973... [100%] 21 of 21, cached:...
[6b/ac1604] process > CSVTK_CONCAT_UNMAP (minimap)   [100%] 1 of 1, cached: 1 ✔
Completed at: 07-Mar-2023 10:40:06
Duration    : 1m 11s
CPU hours   : 666.2 (100% cached)
Succeeded   : 0
Cached      : 67
```

srun --pty  --cpus-per-task=8 --job-name=interact_MINI --ntasks=1 --nodes=1 --partition=inter_p --time=12:00:00 --mem=64GB /bin/bash -l

We are going to jump into the container:
  /scratch/bjl34716/nf_dev/gg-catalog/work/d4/7835874af2e5e6aa52f3b8e8c14ea1/
  
This is the command I am running
  
```bash
singularity shell https://depot.galaxyproject.org/singularity/mulled-v2-66534bcbb7031a148b13e2ad42583020b9cd25c4:1679e915ddb9d6b4abda91880c4b48857d471bd8-0
minimap2 concat-gal-zea-glycine.fna.gz SRR19732514.fastq.gz -o SRR19732514.fq.gz.host.paf  -x map-hifi -t 8
```

paf format does not seem like what we want to do since there is no interchange between this and sam/bam

so instead we are trying this: 

```bash
minimap2 concat-gal-zea-glycine.fna.gz SRR19732514.fastq.gz -x map-hifi -t 8 -a -Q > SRR19732514_test.sam
```

I think we need to do a samtools view step in between the map and fastq steps.

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 3588ac2bceabb9cf6091abce81d23b2b6a288644
slurm sub: 19741249

```bash

[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SAMTOOLS_VIEW` declares 3 input channels but 1 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 116 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: e8f4593552dd38e5688df22416d4ec74ba892f4d
slurm sub: 19741331

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SAMTOOLS_VIEW` declares 3 input channels but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 116 or see '.nextflow.log' file for more details

```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: c68ea57984188184ef0b10a2251c41fdafcfec39
slurm sub: 19741563

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SAMTOOLS_VIEW` declares 3 input channels but 1 were specified
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 4eea30f493ab9f4b3e9e57f4299080d958142628
slurm sub: 19741596

```bash

[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SAMTOOLS_VIEW` declares 3 input channels but 1 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 123 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60:
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 475fb15655b570ff2a6483a5110516519c674e3c
slurm sub: 19741695

```bash
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/17/bd5cefca2fdcc5dc6a4aa2958a3449/SRR15214153.bam]
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/17/bd5cefca2fdcc5dc6a4aa2958a3449/SRR15214153.bam, []]
[[id:SRR19732729, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/18/7e567a1ae81b73ba4738a8d889d38f/SRR19732729.bam, []]
[[id:SRR19732729, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/18/7e567a1ae81b73ba4738a8d889d38f/SRR19732729.bam]
[[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d5/0b8e76db44d5cabe7fda4a9424a1d0/SRR19683890.bam, []]
[[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d5/0b8e76db44d5cabe7fda4a9424a1d0/SRR19683890.bam]
[[id:SRR19683891, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d6/0c1ec12dfa45e21230a653dfb08843/SRR19683891.bam]
[[id:SRR19683891, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d6/0c1ec12dfa45e21230a653dfb08843/SRR19683891.bam, []]
[[id:SRR19732514, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d4/7835874af2e5e6aa52f3b8e8c14ea1/SRR19732514.bam, []]
[[id:SRR19732514, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d4/7835874af2e5e6aa52f3b8e8c14ea1/SRR19732514.bam]
[[id:SRR19736685, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/92/5bf0c7ed2a654d7192ec008ebf9c9f/SRR19736685.bam]
[[id:SRR19736685, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/92/5bf0c7ed2a654d7192ec008ebf9c9f/SRR19736685.bam, []]
[[id:SRR19726169, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d1/8f1170168509123a135c953edff01f/SRR19726169.bam, []]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: b06e1f7938fdf8c5144bc8083d51917197c5793e
slurm sub: 19741784

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SAMTOOLS_VIEW` declares 3 input channels but 1 were specified
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 396eb8222d5db3e3af94bdb19386b4a7146b8509
slurm sub: 19741806

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'getAt'

```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 95416d8c9fce3f7b43e707617ee1e04d88463015 
slurm sub:  19741829

```bash
Execution cancelled -- Finishing pending tasks before exit
WARN: Input tuple does not match input set cardinality declared by process `SAMTOOLS_VIEW` -- offending value: [[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d5/0b8e76db44d5cabe7fda4a9424a1d0/SRR19683890.bam]
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/samtools/view/main.nf' at line: 2 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 048ce6face1750f1cab94e73d1dfff2b2947fc80
slurm sub:  19741872

```bash
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SAMTOOLS_VIEW` declares 3 input channels but 1 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 123 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: b2e7bef4c9cf0b02553e5ef7f9593e42cc001424
slurm sub:  19741893

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SAMTOOLS_VIEW` declares 3 input channels but 1 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 123 or see '.nextflow.log' file for more details
No such variable: info
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 88edd0faac6f882a487ab35aec0951bc855a9be2
slurm sub: 19741915

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SAMTOOLS_VIEW` declares 3 input channels but 1 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 122 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: ceba8dfbf5bb6986c56bfa949690f839ad5ac0ba
slurm sub: 19741943

```bash
WARN: Input tuple does not match input set cardinality declared by process `SAMTOOLS_VIEW` -- offending value: [[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d5/0b8e76db44d5cabe7fda4a9424a1d0/SRR19683890.bam]
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/samtools/view/main.nf' at line: 2 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: b30a4ad5a9cc50486a166920e1a9bc3c0c30bfad 
slurm sub: 19741964

```bash
Execution cancelled -- Finishing pending tasks before exit
WARN: Input tuple does not match input set cardinality declared by process `SAMTOOLS_VIEW` -- offending value: [[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/d5/0b8e76db44d5cabe7fda4a9424a1d0/SRR19683890.bam]
Execution aborted due to an unexpected error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 4b8d3d0f707275d92d20ea584fd4517d08c48f15
slurm sub: 19742015

```bash
Execution cancelled -- Finishing pending tasks before exit
Error executing process > 'SAMTOOLS_VIEW (SRR15214153)'

Caused by:
  Input and output names are the same, use "task.ext.prefix" to disambiguate!

Source block:
  def args = task.ext.args ?: ''
  def args2 = task.ext.args2 ?: ''
  def prefix = task.ext.prefix ?: "${meta.id}"
  def reference = fasta ? "--reference ${fasta}" : ""
  def readnames = qname ? "--qname-file ${qname}": ""
  def file_type = args.contains("--output-fmt sam") ? "sam" :
                      args.contains("--output-fmt bam") ? "bam" :
                      args.contains("--output-fmt cram") ? "cram" :
                      input.getExtension()
  if ("$input" == "${prefix}.${file_type}") error "Input and output names are the same, use \"task.ext.prefix\" to disambiguate!"
  """
      samtools \\
```
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 951e3e0671a1d2db76c2fb33946bf371eba0452b 
slurm sub: 19742101

```bash
 def args = task.ext.args ?: ''
  def args2 = task.ext.args2 ?: ''
  def prefix = task.ext.prefix ?: "${meta.id}"
  def reference = fasta ? "--reference ${fasta}" : ""
  def readnames = qname ? "--qname-file ${qname}": ""
  def file_type = args.contains("--output-fmt sam") ? "sam" :
                      args.contains("--output-fmt bam") ? "bam" :
                      args.contains("--output-fmt cram") ? "cram" :
                      input.getExtension()
  if ("$input" == "${prefix}.${file_type}") error "Input and output names are the same, use \"task.ext.prefix\" to disambiguate!"
  """
      samtools \\
          view \\
          --threads ${task.cpus-1} \\
          ${reference} \\
          ${readnames} \\
          $args \\
          -o ${prefix}.${file_type} \\
          $input \\
          $args2

      cat <<-END_VERSIONS > versions.yml
      "${task.process}":
          samtools: \$(echo \$(samtools --version 2>&1) | sed 's/^.*samtools //; s/Using.*\$//')
      END_VERSIONS
      """

Tip: you can try to figure out whats wrong by chang
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: baa43921ad60d52048fb4842662f28e8668d9b57
slurm sub: 19742122

```bash
```
### Todos for Tomorrow


- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Git commits

#### Lab notebook

```bash
e18a999 - Benjamin Lorentz, Tue Mar 7 08:59:39 2023 -0500 : added page for tuesday
```

#### gg-catalog-nf

```bash
951e3e0 - Benjamin Lorentz, Tue Mar 7 17:04:34 2023 -0500 : update main.nf
b3a9178 - Benjamin Lorentz, Tue Mar 7 16:56:57 2023 -0500 : update main.nf
4b8d3d0 - Benjamin Lorentz, Tue Mar 7 16:51:08 2023 -0500 : update main.nf
b30a4ad - Benjamin Lorentz, Tue Mar 7 16:44:12 2023 -0500 : update main.nf
ceba8df - Benjamin Lorentz, Tue Mar 7 16:42:03 2023 -0500 : update main.nf
88edd0f - Benjamin Lorentz, Tue Mar 7 16:38:05 2023 -0500 : update main.nf
b2e7bef - Benjamin Lorentz, Tue Mar 7 16:35:06 2023 -0500 : update main.nf
048ce6f - Benjamin Lorentz, Tue Mar 7 16:31:35 2023 -0500 : update main.nf
95416d8 - Benjamin Lorentz, Tue Mar 7 16:27:30 2023 -0500 : update main.nf
396eb82 - Benjamin Lorentz, Tue Mar 7 16:24:53 2023 -0500 : update main.nf
b06e1f7 - Benjamin Lorentz, Tue Mar 7 16:21:15 2023 -0500 : update main.nf
475fb15 - Benjamin Lorentz, Tue Mar 7 16:14:16 2023 -0500 : update main.nf
f3c4220 - Benjamin Lorentz, Tue Mar 7 16:13:36 2023 -0500 : update main.nf
:...skipping...
951e3e0 - Benjamin Lorentz, Tue Mar 7 17:04:34 2023 -0500 : update main.nf
b3a9178 - Benjamin Lorentz, Tue Mar 7 16:56:57 2023 -0500 : update main.nf
4b8d3d0 - Benjamin Lorentz, Tue Mar 7 16:51:08 2023 -0500 : update main.nf
b30a4ad - Benjamin Lorentz, Tue Mar 7 16:44:12 2023 -0500 : update main.nf
ceba8df - Benjamin Lorentz, Tue Mar 7 16:42:03 2023 -0500 : update main.nf
88edd0f - Benjamin Lorentz, Tue Mar 7 16:38:05 2023 -0500 : update main.nf
b2e7bef - Benjamin Lorentz, Tue Mar 7 16:35:06 2023 -0500 : update main.nf
048ce6f - Benjamin Lorentz, Tue Mar 7 16:31:35 2023 -0500 : update main.nf
95416d8 - Benjamin Lorentz, Tue Mar 7 16:27:30 2023 -0500 : update main.nf
396eb82 - Benjamin Lorentz, Tue Mar 7 16:24:53 2023 -0500 : update main.nf
b06e1f7 - Benjamin Lorentz, Tue Mar 7 16:21:15 2023 -0500 : update main.nf
475fb15 - Benjamin Lorentz, Tue Mar 7 16:14:16 2023 -0500 : update main.nf
f3c4220 - Benjamin Lorentz, Tue Mar 7 16:13:36 2023 -0500 : update main.nf
4eea30f - Benjamin Lorentz, Tue Mar 7 16:06:24 2023 -0500 : update main.nf
c68ea57 - Benjamin Lorentz, Tue Mar 7 16:02:02 2023 -0500 : update main.nf
e8f4593 - Benjamin Lorentz, Tue Mar 7 15:57:11 2023 -0500 : update main.nf
3588ac2 - Benjamin Lorentz, Tue Mar 7 15:50:21 2023 -0500 : update main.nf and modules.config
d4e7807 - Benjamin Lorentz, Tue Mar 7 15:44:08 2023 -0500 : added samtools view
```
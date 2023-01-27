---
title: '2023 01 27 Minimap Implement'
date: 2023-01-27T15:31:43Z
draft: true
meta_img: "images/image.png"
tags:
  - "one tag"
  - "another tag"
description: "Description for the page"
---

### Todos for Tomorrow

- Homework 1 Stat 6220
- gg-catalog
  - Zhang
    - collect data
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Summarize info for meeting with Aggrey

### gg-catalog

Data is collected

#### make minimap index and save to cloud

I put together a script to index the 3 reference genomes, and pushed it to the server 

gg-catalog rev: d2652b15b34949bc5531ffebf0aea8358367c6e3
gg-catalog-nf rev: 32f86f9cf6eb4998eef54f164a581da3e3a28695
slurm sub: 17964829

```bash
INFO:    Using cached SIF image
[M::mm_idx_gen::22.442*1.82] collected minimizers
[M::mm_idx_gen::27.178*2.03] sorted minimizers
[M::main::34.993*1.78] loaded/built the index for 214 target sequence(s)
[M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 214
[M::mm_idx_stat::36.002*1.76] distinct minimizers: 70434703 (49.99% are singletons); average occurrences: 2.795; average spacing: $[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -d galgal.mmi /scratch/bjl34716/gg-catalog/refs/GalGal-reference.fna.gz
[M::main] Real time: 36.094 sec; CPU: 63.405 sec; Peak RSS: 4.697 GB
INFO:    Using cached SIF image
[M::mm_idx_gen::54.369*1.75] collected minimizers
[M::mm_idx_gen::67.709*1.99] sorted minimizers
[M::main::77.321*1.86] loaded/built the index for 687 target sequence(s)
[M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 687
[M::mm_idx_stat::78.275*1.85] distinct minimizers: 60811177 (55.20% are singletons); average occurrences: 6.712; average spacing: $[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -d zeamays.mmi /scratch/bjl34716/gg-catalog/refs/ZeaMays-reference.fna.gz
[M::main] Real time: 78.491 sec; CPU: 144.695 sec; Peak RSS: 9.315 GB
INFO:    Using cached SIF image
[M::mm_idx_gen::25.835*1.78] collected minimizers
[M::mm_idx_gen::30.919*1.98] sorted minimizers
[M::main::36.648*1.82] loaded/built the index for 284 target sequence(s)
[M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 284
[M::mm_idx_stat::37.149*1.81] distinct minimizers: 47120889 (53.64% are singletons); average occurrences: 3.818; average spacing: $[M::main] Version: 2.24-r1155-dirty
[M::main] CMD: /usr/local/bin/minimap2 -d glycinemax.mmi /scratch/bjl34716/gg-catalog/refs/GlycineMax-reference.fna.gz
[M::main] Real time: 37.418 sec; CPU: 67.348 sec; Peak RSS: 5.764 GB
```
Sucess! this was a fast process just memory intensive, good to know!

Next step is since we have all the seqs, is to maybe try to get the process to go through!

#### Nextflow Implement Filtlong

how do you use a process more than once?

While searching, I found that there are modules for filtlong and minimap, and since I have not implemented the code yet, it might make sense to use them. 

I will stash my current development with tag 0.1 so that if I need to come back to it I can.

I was able to add the filtlong and minimap2 modules to my project and I added the parse_input subworkflow. Next is to use the steps implemented to properly use the code. 

I implememnted the nextflow input parser:

gg-catalog rev: e3db9691baab2c41be159423fadd1b2b1a2e37c7
gg-catalog-nf rev: c71805d9018d9fd7f0b7d7dcbbf0416ea94a74f6
slurm sub: 17968834

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/1UCFtrTsAX0TlS
executor >  slurm (1)
[6c/862ef1] process > TEST (1) [100%] 1 of 1 ✔
Completed at: 27-Jan-2023 15:53:10
Duration    : 1m 2s
CPU hours   : (a few seconds)
Succeeded   : 1
```

Next test

gg-catalog rev: fcc50d26324c7335c5d7cbb284596cca97d97c30
gg-catalog-nf rev: 52d854d00b7b0cbf3074b9f75f21a740d51d0833
slurm sub: 17969202

```bash
ignore!
```

gg-catalog rev: f6b47f8c4cb7885e86baed82282da0c106270dc5
gg-catalog-nf rev: 52d854d00b7b0cbf3074b9f75f21a740d51d0833
slurm sub: 17969209

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [nauseous_pike] DSL2 - revision: 52d854d00b [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Invalid process definition -- Make sure the process ends with a script wrapped by quote characters @ line 138, column 1.
   process READTABLE{
   ^

1 error
```

gg-catalog rev: f6b47f8c4cb7885e86baed82282da0c106270dc5
gg-catalog-nf rev: 28ad3c4d136f559fedd82fdc531e93fa13cbd8f3
slurm sub: 17969282

```bash
V I S U A L I Z E   P I P E L I N E
===================================
input    : /home/bjl34716/my_utils/gg-catalog/code/metadata.tsv
single_end : null
pacbio : true
iontorrent : null
multiple seq runs: false
extension : /*.fastq
outdir   : results
profile : slurm,singularity

No such file: Can't find a matching module file for include: ../modules/nf-core/filtlong/main

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 51 or see '.nextflow.log' file for more details
```

gg-catalog rev: f6b47f8c4cb7885e86baed82282da0c106270dc5
gg-catalog-nf rev: 566eab5ed91c60afc81c18cae842bbabd8214b9b
slurm sub: 17970137

```bash
Module path must start with / or ./ prefix -- Offending module: ${moduleDir}/modules/nf-core/filtlong/main

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 53 or see '.nextflow.log' file for mo
```

gg-catalog rev: f6b47f8c4cb7885e86baed82282da0c106270dc5
gg-catalog-nf rev:  1b6002c022d2c7ff82b72d6a21e285d3ae72e217
slurm sub: 17971157

```bash
No such file: Can't find a matching module file for include: /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf'/modules/nf-$

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf'
```

gg-catalog rev: f6b47f8c4cb7885e86baed82282da0c106270dc5
gg-catalog-nf rev: 564b0012f1f3a79aab7dfd71fd89b8f754774d02
slurm sub: 17971245

```bash
ofile : slurm,singularity

Missing process or function with name 'PARSE_INPUT'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 66 or see '.nextflow.log' file for mo$

```

gg-catalog rev: f6b47f8c4cb7885e86baed82282da0c106270dc5
gg-catalog-nf rev: 9c6a5c22d098d1be35d5198d39c522b088225c7e
slurm sub:  17971360

```bash
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 64 or see '$
Process `TEST` declares 2 input channels but 1 were specified

```

gg-catalog rev: f6b47f8c4cb7885e86baed82282da0c106270dc5
gg-catalog-nf rev: a1dda39623acb63453bafdc22931af9a6cb89601
slurm sub: 17971481

```bash

[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/153bNKZG5O49eS
[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/153bNKZG5O49eS
[-        ] process > TEST -
WARN: Access to undefined parameter `metadata` -- Initialise it to a default value eg. `params.metadata = some_value`

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/153bNKZG5O49eS
[-        ] process > TEST -
WARN: Access to undefined parameter `metadata` -- Initialise it to a default value eg. `params.metadata = some_value`
Please review data input, sample IDs are not unique! First IDs are [[cecum], [colorectum], [duodenum], [ileum], [jejunum]]

```


gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0 
gg-catalog-nf rev: ac06719dcbd2dab201317b58dd568b21741d1506
slurm sub: 17972046

```bash

[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/seicCJPfpZ2Us
[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/seicCJPfpZ2Us
[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/seicCJPfpZ2Us
[-        ] process > TEST -
Completed at: 27-Jan-2023 16:54:14
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
```

to force a dir 

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0 
gg-catalog-nf rev: 04320e5534af81c48e56086d773c8cfa69097ee6
slurm sub: 17972433

```bash
[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/seicCJPfpZ2Us
[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/seicCJPfpZ2Us
[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/seicCJPfpZ2Us
[-        ] process > TEST -
Completed at: 27-Jan-2023 16:54:14
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0 
gg-catalog-nf rev: fe51517eddf9c3f7830148cb985df818098cdb8c
slurm sub: 17972716

```bash
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0 
gg-catalog-nf rev: 02b6bd8b45787b280866b27ceab600f15ef35ce1
slurm sub: 17972717

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/13SaNk8lYguZqV
[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/13SaNk8lYguZqV
[-        ] process > TEST -
Completed at: 27-Jan-2023 17:06:12
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
```
```
I cannot see the files output from PARSE_INPUT so this needs to be examined next time.

### Todos for Next Week

- Homework 1 Stat 6220
- gg-catalog
  - Zhang
    - try to pass reads into filtlong
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Summarize info for meeting with Aggrey

### Git Commits

#### Lab notebook

```bash
7450bb9 - Benjamin Lorentz, Fri Jan 27 11:46:23 2023 -0500 : more notes before lunch
9c71e65 - Benjamin Lorentz, Fri Jan 27 10:32:58 2023 -0500 : added page for friday
```

#### gg-catalog

```bash
7606009 - Benjamin Lorentz, Fri Jan 27 16:52:29 2023 -0500 : added mapping and metadata files
f6b47f8 - Benjamin Lorentz, Fri Jan 27 16:17:21 2023 -0500 : needed to add a \
fcc50d2 - Benjamin Lorentz, Fri Jan 27 16:14:58 2023 -0500 : updated 00_zhang_nextflow
e3db969 - Benjamin Lorentz, Fri Jan 27 15:52:01 2023 -0500 : added metadata
1e4fd25 - Benjamin Lorentz, Fri Jan 27 15:45:02 2023 -0500 : updated test_params.yaml
d2652b1 - Benjamin Lorentz, Fri Jan 27 11:34:03 2023 -0500 : update 00_generate_minimap_indicies
b193185 - Benjamin Lorentz, Fri Jan 27 11:31:58 2023 -0500 : add 00_generate-minimap_indicies.sh
```

#### gg-catalog-nf

```bash
02b6bd8 - Benjamin Lorentz, Fri Jan 27 17:05:27 2023 -0500 : we need to be using nextflow vars
fe51517 - Benjamin Lorentz, Fri Jan 27 17:02:51 2023 -0500 : dont make it work in a container
04320e5 - Benjamin Lorentz, Fri Jan 27 16:58:11 2023 -0500 : update main.nf
ac06719 - Benjamin Lorentz, Fri Jan 27 16:52:53 2023 -0500 : added metadata params
a1dda39 - Benjamin Lorentz, Fri Jan 27 16:43:55 2023 -0500 : update main.nf
9c6a5c2 - Benjamin Lorentz, Fri Jan 27 16:42:40 2023 -0500 : needed to add the parse input code
564b001 - Benjamin Lorentz, Fri Jan 27 16:40:33 2023 -0500 : messed up quote
1b6002c - Benjamin Lorentz, Fri Jan 27 16:38:18 2023 -0500 : update main.nf
566eab5 - Benjamin Lorentz, Fri Jan 27 16:33:39 2023 -0500 : update main.nf
28ad3c4 - Benjamin Lorentz, Fri Jan 27 16:24:39 2023 -0500 : update main.nf
52d854d - Benjamin Lorentz, Fri Jan 27 16:13:29 2023 -0500 : update main.nf
c71805d - Benjamin Lorentz, Fri Jan 27 15:44:41 2023 -0500 : added pacbio and iontorrent
1de90bb - Benjamin Lorentz, Fri Jan 27 15:41:10 2023 -0500 : added diagnostic prints
a0e03b3 - Benjamin Lorentz, Fri Jan 27 15:39:31 2023 -0500 : added a lib and updated main
a123be9 - Benjamin Lorentz, Fri Jan 27 14:35:28 2023 -0500 : added subworkflows dir
:...skipping...
02b6bd8 - Benjamin Lorentz, Fri Jan 27 17:05:27 2023 -0500 : we need to be using nextflow vars 
fe51517 - Benjamin Lorentz, Fri Jan 27 17:02:51 2023 -0500 : dont make it work in a container  
04320e5 - Benjamin Lorentz, Fri Jan 27 16:58:11 2023 -0500 : update main.nf
ac06719 - Benjamin Lorentz, Fri Jan 27 16:52:53 2023 -0500 : added metadata params
a1dda39 - Benjamin Lorentz, Fri Jan 27 16:43:55 2023 -0500 : update main.nf
9c6a5c2 - Benjamin Lorentz, Fri Jan 27 16:42:40 2023 -0500 : needed to add the parse input code
564b001 - Benjamin Lorentz, Fri Jan 27 16:40:33 2023 -0500 : messed up quote
1b6002c - Benjamin Lorentz, Fri Jan 27 16:38:18 2023 -0500 : update main.nf
566eab5 - Benjamin Lorentz, Fri Jan 27 16:33:39 2023 -0500 : update main.nf
28ad3c4 - Benjamin Lorentz, Fri Jan 27 16:24:39 2023 -0500 : update main.nf
52d854d - Benjamin Lorentz, Fri Jan 27 16:13:29 2023 -0500 : update main.nf
c71805d - Benjamin Lorentz, Fri Jan 27 15:44:41 2023 -0500 : added pacbio and iontorrent       
1de90bb - Benjamin Lorentz, Fri Jan 27 15:41:10 2023 -0500 : added diagnostic prints
a0e03b3 - Benjamin Lorentz, Fri Jan 27 15:39:31 2023 -0500 : added a lib and updated main      
a123be9 - Benjamin Lorentz, Fri Jan 27 14:35:28 2023 -0500 : added subworkflows dir
a086fc7 - Benjamin Lorentz, Fri Jan 27 14:20:27 2023 -0500 : update main.nf add modules
```


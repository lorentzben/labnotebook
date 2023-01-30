---
title: 'First Two Gg Catalog Nf Steps'
date: 2023-01-30T15:40:36Z
draft: false
meta_img: "images/image.png"
tags:
  - "filtlong"
  - "minimap2"
  - "nextflow"
description: "Description for the page"
---

### Todos for Today

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
  
### gg-catalog-nf

I want to try to use the import function and then pass the result files into the next process

#### Filtlong task

I "wrote my own process", but since I imported my own process, then I might need to just pass my params through

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: 526b1dd6f053be28b88a6a82bb32d17e2d07de5b
slurm sub: 18039828

```bash
Error executing process > 'FILTLONG (2)'

Caused by:
  Not a valid path value type: java.util.LinkedHashMap ([id:SRR19683890, single_end:true, run:A])


Tip: you can try to figure out whats wrong by changing to the process work dir and showing the script file named `.command.sh`
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: 6360d30ede5a8124044c997172103d3f13d43c9c 
slurm sub: 18039840

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4SMVjDsEhZwDnT
[-        ] process > TEST     -
[-        ] process > FILTLONG -
Completed at: 30-Jan-2023 11:09:42
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 0
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: 70cc1016b3943ef3e331385404554af5c84074e6
slurm sub: 18040505

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4fIRIXjLz9XY9k
[-        ] process > TEST     -
[-        ] process > FILTLONG -
Completed at: 30-Jan-2023 11:17:43
Duration    : 1m 6s
CPU hours   : (a few seconds)
Succeeded   : 0
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: a3e03aab9700da2b6d4d3c542e3a79816a76660d
slurm sub: 18041294

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 64 or s$Process `FILTLONG` declares 1 input channel but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 74 or see '.nextflow.log' file fo$[-        ] process > TEST -
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: a4142f408ffccae3ad2c9d8c16acc30fb2e4de05
slurm sub: 18042183

```bash
Process `FILTLONG` declares 1 input channel but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 74 or see '.nextflow.log' file fo$No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 64 or s$
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: c796c0dfb56478c7a0c8e54dd06a70e9e5e0db4f
slurm sub: 18042194

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5tERuhmHwWxH1F
[-        ] process > TEST     -
[-        ] process > FILTLONG -
Execution cancelled -- Finishing pending tasks before exit
WARN: Input tuple does not match input set cardinality declared by process `FILTLONG` -- offending value: [[id:SRR15214153, single_end:true, run:A], [/scratch/bjl34716/gg-catalog/zhang/reads/c
$Execution aborted due to an unexpected error
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: ff0b4812fe1e869c7ba43b5723ded31ad16edaa0
slurm sub: 18042205

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 64 or see '.nextflow.log' file for more de$Missing process or function with name 'getAt'
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: 94021bfdb16573ff4899de4026e7c71aadeb67a6
slurm sub: 18048849

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 64 or see '.nextflow.log' file for more de$Missing process or function with name 'getAt'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 74 or see '.nextflow.log' file for more details
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: 7b32d29036e33340c913a52b585ecfd1c0759b36
slurm sub: 18048931

```bash
-- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 64 or see '.nextflow.log' file for more de$Process `FILTLONG` declares 1 input channel but 0 were specified
```

gg-catalog rev: 7606009902ee6fc4dd95f262cb54e39cf4ec7ad0
gg-catalog-nf rev: 13defd76b03b44d0fc63fa1018902566df354ac5
slurm sub: 18048935

```bash
WARN: Input tuple does not match input set cardinality declared by process `FILTLONG` -- offending value: [[id:SRR15214153, single_end:true, run:A], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
Execution aborted due to an unexpected error
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 13defd76b03b44d0fc63fa1018902566df354ac5
slurm sub: 18048949

```bash
[-        ] process > FILTLONG -
WARN: Input tuple does not match input set cardinality declared by process `FILTLONG` -- offending value: [[id:SRR15214153, single_end:true, run:1], [/scratch/bj$Execution aborted due to an unexpected error
```

It adds a value if runs is not suggested. I went into the parse_input.nf file and removed references to run.

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 7b690b27ddf76cda17efdd6245ff4b8e58bf0c15
slurm sub: 18049219

```bash
Workflow `PARSE_INPUT` declares 4 input channels but 5 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 69 or see '.nextflow.log' file for more details

```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 26b37af83b000624e39fcecc6ea86b9a5081915f
slurm sub: 18049299

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/3IPcHg1x6hUOnY
[-        ] process > FILTLONG -
WARN: Input tuple does not match input set cardinality declared by process `FILTLONG` -- offending value: [[id:SRR15214153, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
Execution aborted due to an unexpected error
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 60e44d461a12b5471569914b8af01e95b3e06305 
slurm sub: 18049409

```bash
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'getAt'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 73 or see '.nextflow.log' file for more details
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 6d8f506d658354e311e0ac5579cd59e24e1b14d0
slurm sub: 18053888

```bash
Missing process or function with name 'getAt'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 73 or see '.nextflow.log' file for more details
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 7b6aca611e6833ff227750f9abc9ae956ab34723
slurm sub: 18053893

```bash
THE SAME ISSUE
```

Since we are unable to use the "get" method, we can maybe make a new map using this:
https://stackoverflow.com/questions/73204784/how-to-get-first-items-in-channel-of-tuples-in-nextflow

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 7be06bccd09d54ae032fb6ddc91677b7b16ce325
slurm sub: 18056715

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `FILTLONG` declares 1 input channel but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 75 or see '.nextflow.log' file for more details
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: e374c2a011fe51b18e389a93d26ce3e86d674e0a
slurm sub: 18056732

```bash
[-        ] process > FILTLONG -
WARN: Input tuple does not match input set cardinality declared by process `FILTLONG` -- offending value: [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/filtlong/main.nf' at line: 2 or see '.nextflow.log' file for more details

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5QFnTsAq8lKUe3
[-        ] process > FILTLONG -
Execution cancelled -- Finishing pending tasks before exit
WARN: Input tuple does not match input set cardinality declared by process `FILTLONG` -- offending value: [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]
Execution aborted due to an unexpected error
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 9e51a762fb1a72d8f3e0477596e1838f7ee94703
slurm sub: 18056804

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [naughty_faggin] DSL2 - revision: 9e51a762fb [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 62, column 10.
   workflow {
            ^

1 error
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 08fe3a77104bcc100cd79bc14f2ed2eac748877f
slurm sub: 18056818

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/filtlong/main.nf' at line: 2 or see '.nextflow.log' file for more details

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/eSQ9veXwqW3x
[-        ] process > FILTLONG -
Execution cancelled -- Finishing pending tasks before exit
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/filtlong/main.nf' at line: 2 or see '.nextflow.log' file for more details
 
 java.lang.NullPointerException: Cannot get property 'id' on null object
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: d9c769d721e17cb5babbacfa256b807d70134ce8
slurm sub: 18056971

```bash
java.lang.NullPointerException: Cannot get property 'id' on null object
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: fb0ce8e29e9e235c1c798405ec1adfd8a3a9f7bd
slurm sub: 18057154

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more de$No such variable: id_map
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 10cc178114038c56b14313b13ed24e6e7fe14f09
slurm sub: 18057238

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4kzNkSK2HTl53x
[-        ] process > FILTLONG -
Invalid method invocation `call` with arguments: [[id:SRR15214153, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]] (java.util.ArrayList) on _closure5 type



Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4kzNkSK2HTl53x
[-        ] process > FILTLONG -
Invalid method invocation `call` with arguments: [[id:SRR15214153, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]] (java.util.ArrayList) on _closure5 type
```

I cannot get the method to work with their module. I am going to write my own process.

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 841d321ec68fada1e5af3858c907dc259c596dec
slurm sub: 18057387

```bash
java.lang.NullPointerException: Cannot get property 'id' on null object
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 8142fbbf91eb9048dab5a89ca46fde1ff520617e
slurm sub: 18057609 

```bash
java.lang.NullPointerException: Cannot get property 'id' on null object
```

We need to write a process that runs:

```bash
filtlong --min_length 2000 --keep_percent 99 ../zhang/reads/duodenum/SRR19683891.fastq | gzip > SRR19683891.fastq.gz
```

### Todos for Tomorrow

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
  
### Git Commits

#### lab notebook

```bash
6da41bc - Benjamin Lorentz, Mon Jan 30 14:54:19 2023 -0500 : notes throughout the day
dc14977 - Benjamin Lorentz, Mon Jan 30 10:44:49 2023 -0500 : add page for monday
```

#### gg-catalog

```bash
82c851f - Benjamin Lorentz, Mon Jan 30 13:39:46 2023 -0500 : remove the run column
```

#### gg-catalog-nf

```bash
8142fbb - Benjamin Lorentz, Mon Jan 30 16:53:29 2023 -0500 : update main.nf
841d321 - Benjamin Lorentz, Mon Jan 30 16:48:10 2023 -0500 : update main.nf
10cc178 - Benjamin Lorentz, Mon Jan 30 16:44:27 2023 -0500 : update main.nf
fb0ce8e - Benjamin Lorentz, Mon Jan 30 16:42:51 2023 -0500 : update main.nf
7b9cd06 - Benjamin Lorentz, Mon Jan 30 16:41:46 2023 -0500 : update main.nf
d9c769d - Benjamin Lorentz, Mon Jan 30 16:37:45 2023 -0500 : update main.nf
08fe3a7 - Benjamin Lorentz, Mon Jan 30 16:33:17 2023 -0500 : update main.nf
4ee0397 - Benjamin Lorentz, Mon Jan 30 16:32:16 2023 -0500 : update main.nf
9e51a76 - Benjamin Lorentz, Mon Jan 30 16:29:01 2023 -0500 : update main.nf
46f5505 - Benjamin Lorentz, Mon Jan 30 16:28:06 2023 -0500 : update main.nf
e374c2a - Benjamin Lorentz, Mon Jan 30 16:21:20 2023 -0500 : update main.nf
7be06bc - Benjamin Lorentz, Mon Jan 30 16:18:04 2023 -0500 : update main.nf
```
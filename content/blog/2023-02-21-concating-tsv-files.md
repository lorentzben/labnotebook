---
title: 'Concating Tsv Files'
date: 2023-02-21T13:27:11Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---

Happy Mardi Gras

### Todos for Today

- Stat 6220 
  - Homework 2
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
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

#### Remaking the channels for concating tsvs

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: c6e57168fff7edc63ebcb73cbbd02da8cf91d791
slurm sub: 19247663

```bash
[[id:SRR15214153, single_end:true], [scratch, bjl34716, nf_dev, gg-catalog, work, a2, 6b074f14a308af0195566b786c09d5, SRR152141
53.tsv]]
[[id:SRR19683890, single_end:true], [scratch, bjl34716, nf_dev, gg-catalog, work, 22, 80c79296235eb54fcf5e0e566a1165, SRR196838
90.tsv]]
[[id:SRR19732729, single_end:true], [scratch, bjl34716, nf_dev, gg-catalog, work, 1f, 983172df307510c23f415c319bbd8b, SRR197327
29.tsv]]
[[id:SRR19683891, single_end:true], [scratch, bjl34716, nf_dev, gg-catalog, work, f4, 45ed941f60c1cebefe70838b21d939, SRR196838
91.tsv]]
[[id:SRR19736685, single_end:true], [scratch, bjl34716, nf_dev, gg-catalog, work, 22, b242a25e150577c8a295ed7f312eb7, SRR19736685.tsv]]
[[id:SRR19726169, single_end:true], [scratch, bjl34716, nf_dev, gg-catalog, work, 20, 4394fe97be04c534a01073955ac750, SRR19726169.tsv]]
[[id:SRR19732514, single_end:true], [scratch, bjl34716, nf_dev, gg-catalog, work, cc, 434a78f20aaec4fb36598c9a3dc61d, SRR197325
14.tsv]]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 2729ba4b9213c79e8383ce7c8fac096f84b0510c
slurm sub: 19247680

```bash
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 3851b8726856db9909f9df24b880eeb85b356f10
slurm sub: 19247714

```bash
[[[id:SRR15214153, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv]]
[[[id:SRR19683890, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv]]
[[[id:SRR19683891, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv]]
[[[id:SRR19732729, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv]]
[[[id:SRR19726169, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv]]
[[[id:SRR19736685, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv]]
[[[id:SRR19732514, single_end:true]], [/scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: cfba35fd81104f978ae7fca5d7d043b2f85c085d
slurm sub: 19247732

```bash
[['id':'SRR19683890', 'single_end':true], ['id':'SRR19732729', 'single_end':true], ['id':'SRR15214153', 'single_end':true], ['id':'SRR19683891', 'single_end':true], ['id':'SRR19726169', 'single_end':true], ['id':'SRR19736685', 'single_end':true], ['id':'SRR19732514', 'single_end':true]]
[/scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]
```




gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: abae4662f99cfbaefe7a486ed7eeaaad782dae84
slurm sub: 19247742

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/csvtk/concat/main.nf' at line: 2 or see '.nextflow.log' file for more details
[34/7e432c] Cached process > FILTLONG (SRR19683890)
```
gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 504e62b2815f5e826751dc792b0e77c4daba58a7
slurm sub: 19247829

```bash
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [stupefied_hopper] DSL2 - revision: 504e62b281 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: d9bb8e4087b9a53889c496fda56dd1f0666a5d90
slurm sub: 19247840

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [amazing_goldstine] DSL2 - revision: d9bb8e4087 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 095c342cf104e926f6ddee0e0759d51768c5f215
slurm sub: 19247845

```bash
Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [amazing_goldstine] DSL2 - revision: d9bb8e4087 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 27866b9d80872ed1e4d01e54208137a14da6aeaa
slurm sub: 19247855

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [sick_stone] DSL2 - revision: 27866b9d80 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 27866b9d80872ed1e4d01e54208137a14da6aeaa
slurm sub: 19247855

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [sick_stone] DSL2 - revision: 27866b9d80 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error


```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: c14e3578fd20ec4c938ae3ad597f6809bff70719
slurm sub: 19247858

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4qtpzk7SFWsogp
[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
[-        ] process > MINIMAP2_ALIGN -
[-        ] process > SAMTOOLS_FASTQ -
[-        ] process > SAMTOOLS_FASTA -
[-        ] process > SEQKIT_STATS   -
[-        ] process > CSVTK_CONCAT   -
Execution cancelled -- Finishing pending tasks before exit
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/csvtk/concat/main.nf' at line: 2 or see '.nextflow.log' file for more details
[22/80c792] Cached process > SEQKIT_STATS (SRR19683890)
[a2/6b074f] Cached process > SEQKIT_STATS (SRR15214153)
[04/9731d4] Cached process > FILTLONG (SRR15214153)
[fa/898530] Cached process > MINIMAP2_INDEX (1)
[34/7e432c] Cached process > FILTLONG (SRR19683890)
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 8e0a6d482456811d2d16630e03bcea4213737d1b
slurm sub: 19247958

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Cannot invoke method view() on null object

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 140 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: f3235b743452ceeb6ed43d43fe6d462935b1f863
slurm sub: 19247994

```bash
[id:raw, single_end:true]
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/csvtk/concat/main.nf' at line: 2 or$

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5jxkKmVHDTgrwA
[34/7e432c] process > FILTLONG (SRR19683890)     [100%] 2 of 2, cached: 2
[fa/898530] process > MINIMAP2_INDEX (1)         [100%] 1 of 1, cached: 1 ✔
[-        ] process > MINIMAP2_ALIGN             -
[-        ] process > SAMTOOLS_FASTQ             -
[-        ] process > SAMTOOLS_FASTA             -
[a2/6b074f] process > SEQKIT_STATS (SRR15214153) [100%] 2 of 2, cached: 2
[-        ] process > CSVTK_CONCAT               -
[id:raw, single_end:true]
Execution cancelled -- Finishing pending tasks before exit
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/csvtk/concat/main.nf' at line: 2 or$
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 9b06a517b129b1803f50d1451de3e23ba9f229d1
slurm sub: 19248026

```bash
[id:raw, single_end:true]
[/scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 9b06a517b129b1803f50d1451de3e23ba9f229d1
slurm sub: 19248026

```bash
[id:raw, single_end:true]
[/scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 48c964be5bf62ec4e233b3694e29c3357071fea6
slurm sub: 19248454

```bash
[DataflowVariable(value=null), [/scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: dc25f3966eb1f61229a22b566f530c3ce1c1a919
slurm sub: 19248460

```bash
[DataflowBroadcast around DataflowStream[?], [/scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: a6bcb49507a57ad01bd28d3d38cec06e735ff229
slurm sub: 19248475


```bash
[[id:raw, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv]
```
gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 32809a0c491bba72ded03447a1bcfeed8d8c3c29
slurm sub: 19248481


```bash
CSVTK_CONCAT (raw)

Command


csvtk \
    concat \
     \
    --num-cpus 2 \
    --delimiter "	" \
    --out-delimiter "	" \
    --out-file raw.tsv \
    SRR19683890.tsv

cat <<-END_VERSIONS > versions.yml
"CSVTK_CONCAT":
    csvtk: $(echo $( csvtk version | sed -e "s/csvtk v//g" ))
END_VERSIONS

Status

Exit: 255 (FAILED) Attempts: 1 (action: FINISH)

Work directory

/scratch/bjl34716/nf_dev/gg-catalog/work/c4/ae0dc11a63bf31a192d52d1f01bf03
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 080afa6f7208b8eb5edaeafe870e40a3a742fbfe
slurm sub: 19248537


```bash
Error executing process > 'CSVTK_CONCAT (raw)'

Caused by:
  Process `CSVTK_CONCAT (raw)` terminated with an error exit status (255)

Command executed:

  csvtk \
      concat \
       \
      --num-cpus 2 \
      --delimiter "	" \
      --out-delimiter "	" \
      --out-file raw.tsv \
      SRR15214153.tsv
  
  cat <<-END_VERSIONS > versions.yml
  "CSVTK_CONCAT":
      csvtk: $(echo $( csvtk version | sed -e "s/csvtk v//g" ))
  END_VERSIONS

Command exit status:
  255

Command output:
  (empty)

Command error:
  [31m[ERRO][0m xopen: no content

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/43/be9342322ea4df75bc5d3d55812187
```
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: c2154380c849e86cf106403fc20f77d72b95f238
slurm sub: 19248541


```bash
Error executing process > 'CSVTK_CONCAT (raw)'

Caused by:
  Process `CSVTK_CONCAT (raw)` terminated with an error exit status (255)

Command executed:

  csvtk \
      concat \
       \
      --num-cpus 2 \
      --delimiter "	" \
      --out-delimiter "	" \
      --out-file raw.tsv \
      SRR15214153.tsv
  
  cat <<-END_VERSIONS > versions.yml
  "CSVTK_CONCAT":
      csvtk: $(echo $( csvtk version | sed -e "s/csvtk v//g" ))
  END_VERSIONS

Command exit status:
  255

Command output:
  (empty)

Command error:
  [31m[ERRO][0m xopen: no content

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/3c/407923fdb96df36328150c7e3089d1

Tip: view the complete command output by changing to the process work dir and entering the command `cat .command.out`
```
```

How would I do this by hand?

### Can we just pass all the reads in?

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 2d57dd7789f8c9134d92d9e678f7976d8add3c72
slurm sub: 19248937


```bash
Error executing process > 'CSVTK_CONCAT (raw)'

Caused by:
  Process `CSVTK_CONCAT (raw)` terminated with an error exit status (255)

Command executed:

  csvtk \
      concat \
       \
      --num-cpus 2 \
      --delimiter "     " \
      --out-delimiter " " \
      --out-file raw.tsv \
      SRR15214153.tsv

  cat <<-END_VERSIONS > versions.yml
  "CSVTK_CONCAT":
      csvtk: $(echo $( csvtk version | sed -e "s/csvtk v//g" ))
  END_VERSIONS

Command exit status:
  255

Command output:
```
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: c1b90f1a56d174921965e0c1b004cc837abb8ab7
slurm sub: 19249033


```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'view'
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 454f41dd333a5a94e71cb5ba8ca3eb52455145ad
slurm sub: 19249053


```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'view'
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 4f52afa59c0cd493ae8e8559baff08ab9ae795fd
slurm sub: 19249127


```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'getAt'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 137 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 01f1aacae661ba8e58eacb8ec6a7415e967c1bd2
slurm sub: 19249136


```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `CSVTK_CONCAT` declares 3 input channels but 4 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 139 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 342d659cc095dea39e95c50343512bab0dae912e
slurm sub: 19249141


```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [golden_becquerel] DSL2 - revision: 342d659cc0 [main]
Script compilation error
- file : /home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf
- cause: Unexpected input: '{' @ line 71, column 9.
   workflow{
           ^

1 error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: fd9d8b84f379457162ce2c224f0f2900006fb1a9
slurm sub: 19249146


```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'Tuple'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 139 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 19249152
slurm sub: 370c17c6dcadc26c1e0ed99eb3c5422c54e74b0f


```bash
[DataflowBroadcast around DataflowStream[?], DataflowVariable(value=null)]
[['id':'SRR15214153', 'single_end':true], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq], ['id':'SRR19683890', 'single_end':true], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq], ['id':'SRR19732729', 'single_end':true], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq], ['id':'SRR19683891', 'single_end':true], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq], ['id':'SRR19736685', 'single_end':true], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq], ['id':'SRR19726169', 'single_end':true], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq], ['id':'SRR19732514', 'single_end':true], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
Execution cancelled -- Finishing pending tasks before exit
Execution aborted due to an unexpected error
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 217fcf0c900f2c73f34ae328507beeb5f090dc12
slurm sub: 19249173


```bash
[a2/6b074f] Cached process > SEQKIT_STATS (SRR15214153)
[34/7e432c] Cached process > FILTLONG (SRR19683890)
[fa/898530] Cached process > MINIMAP2_INDEX (1)
[22/80c792] Cached process > SEQKIT_STATS (SRR19683890)
[04/9731d4] Cached process > FILTLONG (SRR15214153)
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/58YXwP2Micutba
[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
[-        ] process > MINIMAP2_ALIGN -
[-        ] process > SAMTOOLS_FASTQ -
[-        ] process > SAMTOOLS_FASTA -
[-        ] process > SEQKIT_STATS   -
[-        ] process > CSVTK_CONCAT   -
Execution cancelled -- Finishing pending tasks before exit
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/csvtk/concat/main.nf' at line: 2 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 2626e1522637d4e6dfdd2b98c78702df4418f675 
slurm sub: 19249193

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/61neCirQ1LfLzo
[ba/34a78b] process > FILTLONG (SRR19732514)       [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)           [100%] 1 of 1, cached: 1 ✔
[d4/783587] process > MINIMAP2_ALIGN (SRR19732514) [100%] 7 of 7, cached: 7 ✔
[25/d1bf49] process > SAMTOOLS_FASTQ (SRR19683891) [100%] 7 of 7, cached: 7 ✔
[30/87d180] process > SAMTOOLS_FASTA (SRR19732514) [100%] 7 of 7, cached: 7 ✔
[20/4394fe] process > SEQKIT_STATS (SRR19726169)   [100%] 7 of 7, cached: 7 ✔
[/scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: e9919e40223c5973b7a8bb0935140a6805a96eb1
slurm sub: 19249214

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'set'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 136 or see '.nextflow.log' file for more details
No such variable: info
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 3a939a22fe35b92180ed2ad3dd0d04078a6498af
slurm sub: 19249220

```bash

[-        ] process > FILTLONG -
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'Channel'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 136 or see '.nextflow.log' file for more details
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: cfb4635ff8d6d559a29ec36cb70c55f4c6aac08c
slurm sub: 19249226

```bash
[[id:raw, single_end:true], DataflowBroadcast around DataflowStream[?]]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: a7b441c958abc6d9a741a6d251461e1cbdb70832
slurm sub: 19249238

```bash
[[id:raw, single_end:true], DataflowVariable(value=null)]
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: e1b4adef820c5caaca7499dcedd8be82f62b02a6
slurm sub: 19249252

```bash
[[id:raw, single_end:true], DataflowVariable(value=null)]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 2ad3a785062fdb37549d528e8084bba04d87a42e
slurm sub: 19249286

```bash
DataflowVariable(value=null)
WARN: The operator `first` is useless when applied to a value channel which returns a single value by definition -- check channel `ch_raw_table_loc`

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/1m9XhkNRv3eNIu
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 62b9e9541d9e70fa1f0e3986578774acb39d878b
slurm sub: 19249312

```bash
DataflowVariable(value=null)
[[id:raw, single_end:true], DataflowVariable(value=null)]
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: be5a9f4121260ec4b4ce341a0de801d503b61f43
slurm sub: 19249331

```bash
[[id:raw, single_end:true], DataflowVariable(value=null)]
[/scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev:  71f730d47cb772863eee05fe29b6c3cb017365bc 
slurm sub: 19249415

```bash
[[id:raw, single_end:true], [/scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]]
```
gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 10b514bbc54db137206443143e01004f9f734434 
slurm sub: 19249435

```bash
 The exit status of the task that caused the workflow execution to fail was: 255

Error executing process > 'CSVTK_CONCAT (raw)'

Caused by:
  Process `CSVTK_CONCAT (raw)` terminated with an error exit status (255)

Command executed:

  csvtk \
      concat \
       \
      --num-cpus 2 \
      --delimiter "	" \
      --out-delimiter "	" \
      --out-file raw.tsv \
      SRR19683890.tsv SRR15214153.tsv SRR19732729.tsv SRR19683891.tsv SRR19736685.tsv SRR19732514.tsv SRR19726169.tsv
  
  cat <<-END_VERSIONS > versions.yml
  "CSVTK_CONCAT":
      csvtk: $(echo $( csvtk version | sed -e "s/csvtk v//g" ))
  END_VERSIONS

Command exit status:
  255

Command output:
  (empty)

Command error:
  [31m[ERRO][0m xopen: no content

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/2e/9e78cb3bec8e02d825438e162909ba

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`
```
```

IT WORKS 

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 10b514bbc54db137206443143e01004f9f734434 
slurm sub: 19249454

```bash
bjl34716@ss-sub2 code$ head /scratch/bjl34716/nf_dev/gg-catalog/work/bd/fde0b430dbf4805f623081d71e552a/raw.tsv
file    format  type    num_seqs        sum_len min_len avg_len max_len Q1      Q2      Q3      sum_gap N50     Q20(%)  Q30(%)
SRR19726169.fastq       FASTQ   DNA     521405  8598356757      2016    16490.7 44765   14342.0 15708.0 17875.0 0       16188 99.14    97.89
SRR19683891.fastq       FASTQ   DNA     2872317 22416650091     467     7804.4  46626   4426.0  6885.0  10361.0 0       9726  98.90    97.38
SRR15214153.fastq       FASTQ   DNA     1984390 33649253344     493     16957.0 52396   12960.0 15970.0 19871.0 0       17635 97.96    95.12
SRR19732729.fastq       FASTQ   DNA     1932693 35894296324     508     18572.2 50558   15004.0 17375.0 21061.0 0       18640 98.19    95.76
SRR19732514.fastq       FASTQ   DNA     2147916 35960758459     2006    16742.2 50018   14440.0 15921.0 18255.0 0       16474 98.61    96.60
SRR19683890.fastq       FASTQ   DNA     3933708 75997734768     715     19319.6 65014   15555.0 18196.0 22033.0 0       19546 98.21    95.70
SRR19736685.fastq       FASTQ   DNA     4282202 72828594344     2000    17007.3 53591   14333.0 16113.0 18791.0 0       16856 98.61    96.67
bjl34716@ss-sub2 code$
```

### Stat 6220 

#### Homework 2 

I was able to get parts 1-2 setup and have part 3 on to go. 


### Ben Jackwood

Add in a better error handle for no database present but user asks for one.

### Todos for Tomorrow

- Stat 6220 
  - Homework 2
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
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
  
### Git Commits

#### Lab Notebook

```bash
e3a6689 - Benjamin Lorentz, Tue Feb 21 12:18:35 2023 -0500 : notes before lunch
4a68813 - Benjamin Lorentz, Tue Feb 21 08:29:14 2023 -0500 : added page for tuesday
1b21f7b - Benjamin Lorentz, Mon Feb 20 17:03:47 2023 -0500 : end of monday
```

#### gg-catalog-nf

```bash
10b514b - Benjamin Lorentz, Tue Feb 21 15:12:35 2023 -0500 : update main.nf
71f730d - Benjamin Lorentz, Tue Feb 21 15:08:37 2023 -0500 : update main.nf
be5a9f4 - Benjamin Lorentz, Tue Feb 21 15:01:24 2023 -0500 : update main.nf
62b9e95 - Benjamin Lorentz, Tue Feb 21 14:58:11 2023 -0500 : update main.nf
2ad3a78 - Benjamin Lorentz, Tue Feb 21 14:55:07 2023 -0500 : update main.nf
e1b4ade - Benjamin Lorentz, Tue Feb 21 14:45:14 2023 -0500 : update main.nf
a7b441c - Benjamin Lorentz, Tue Feb 21 14:40:34 2023 -0500 : update main.nf
cfb4635 - Benjamin Lorentz, Tue Feb 21 14:36:20 2023 -0500 : update main.nf
3a939a2 - Benjamin Lorentz, Tue Feb 21 14:34:06 2023 -0500 : update this to a channel
e9919e4 - Benjamin Lorentz, Tue Feb 21 14:32:31 2023 -0500 : update main.nf
2626e15 - Benjamin Lorentz, Tue Feb 21 14:28:45 2023 -0500 : update main.nf
217fcf0 - Benjamin Lorentz, Tue Feb 21 14:25:29 2023 -0500 : update main.nf
370c17c - Benjamin Lorentz, Tue Feb 21 14:19:34 2023 -0500 : update main.nf
fd9d8b8 - Benjamin Lorentz, Tue Feb 21 14:17:48 2023 -0500 : update main.nf
342d659 - Benjamin Lorentz, Tue Feb 21 14:14:26 2023 -0500 : update main.nf
01f1aac - Benjamin Lorentz, Tue Feb 21 14:12:49 2023 -0500 : update main.nf
4f52afa - Benjamin Lorentz, Tue Feb 21 14:10:37 2023 -0500 : update main.nf
454f41d - Benjamin Lorentz, Tue Feb 21 13:55:15 2023 -0500 : update main.nf
c1b90f1 - Benjamin Lorentz, Tue Feb 21 13:49:36 2023 -0500 : update main.nf
2d57dd7 - Benjamin Lorentz, Tue Feb 21 13:36:20 2023 -0500 : update main.nf
c215438 - Benjamin Lorentz, Tue Feb 21 12:15:03 2023 -0500 : update main.nf
080afa6 - Benjamin Lorentz, Tue Feb 21 12:11:50 2023 -0500 : update main.nf
32809a0 - Benjamin Lorentz, Tue Feb 21 12:06:22 2023 -0500 : update main.nf
a6bcb49 - Benjamin Lorentz, Tue Feb 21 12:02:57 2023 -0500 : update main.nf
dc25f39 - Benjamin Lorentz, Tue Feb 21 11:57:02 2023 -0500 : update main.nf
48c964b - Benjamin Lorentz, Tue Feb 21 11:52:37 2023 -0500 : update main.nf
9b06a51 - Benjamin Lorentz, Tue Feb 21 10:35:08 2023 -0500 : update main.nf
f3235b7 - Benjamin Lorentz, Tue Feb 21 10:31:02 2023 -0500 : update main.nf
8e0a6d4 - Benjamin Lorentz, Tue Feb 21 10:24:59 2023 -0500 : update main.nf
c14e357 - Benjamin Lorentz, Tue Feb 21 10:21:15 2023 -0500 : update main.nf
27866b9 - Benjamin Lorentz, Tue Feb 21 10:19:06 2023 -0500 : update main.nf
095c342 - Benjamin Lorentz, Tue Feb 21 10:17:20 2023 -0500 : update main.nf
d9bb8e4 - Benjamin Lorentz, Tue Feb 21 10:15:26 2023 -0500 : update main.nf
504e62b - Benjamin Lorentz, Tue Feb 21 10:11:52 2023 -0500 : update main.nf
abae466 - Benjamin Lorentz, Tue Feb 21 10:00:16 2023 -0500 : update main.nf
cfba35f - Benjamin Lorentz, Tue Feb 21 09:55:09 2023 -0500 : update main.nf
```

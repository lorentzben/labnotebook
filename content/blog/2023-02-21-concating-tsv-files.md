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
  [31m[ERRO][0m xopen: no content

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/3c/407923fdb96df36328150c7e3089d1

Tip: view the complete command output by changing to the process work dir and entering the command `cat .command.out`
```
```

How would I do this by hand?




### Stat 6220 

#### Homework 2 


### Ben Jackwood

Add in a better error handle for no database present but user asks for one.


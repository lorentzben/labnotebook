---
title: 'Compare Read Counts Before After Filter'
date: 2023-02-20T16:11:41Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
description: "Description for the page"
---

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

#### Process to compare read counts

How did I previously count the reads?

Fastqs:

gzipped:

```bash
gzip -dc $FILENAME.fastq.gz |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }' 
```

just fastq 

```bash
cat 	/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
```

We want to go from 

Raw reads -> Filtlong Reads -> mini-unmapped bams -> mini-unmapped reads
fastq -> fastq.gz -> bam -> fastq/fasta

Looks like we might want the other file? not the singleton or fasta?

### Implementation

I have the SEQKIT_STATS module and the CSV_CONCAT module loaded and a test table to see what the result looks like:

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 01982ede77e31f88362a8c177720d010224fe600
slurm sub: 19236396

```bash
[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'view'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 123 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 184e3d1b02fec9ccd075ca54134ce9cf773e4340
slurm sub: 19236448

```bash
-- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or s$No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or $Missing process or function with name 'view'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 123 or see '.nextflow.log' file f
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 628ba9c5f2d85ab3c6e47b3cf2ddfc4495d7f00a
slurm sub: 19236485

```bash
WARNING: While bind mounting '/scratch/bjl34716/nf_dev/gg-catalog/work/36/ed70f642f8c67fb48c62e29e828bf2:/scratch/bjl34716/nf_dev/gg-catalog/work/36/ed70f642f8c67fb48c62e29e828bf2': destination is already in the mount point list
^[[31m[ERRO]^[[0m -: fastx: stdin not detected
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 85d771a15d60b34eb109c2c84b943753cd267c2c
slurm sub: 19236637

```bash
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
[[id:SRR19683890, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]]
[[id:SRR19732729, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]]
[[id:SRR19683891, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]]
[[id:SRR19736685, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]]
[[id:SRR19726169, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]]
[[id:SRR19732514, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 81be794194ba63a8c536042251ebd7b1aab1e828
slurm sub: 19236690

```bash

[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `SEQKIT_STATS` declares 1 input channel but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 121 or see '.nextflow.log' file for more details
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 86d4ba96e8e73d82dc69c28819c95949aef15548
slurm sub: 19236731

```bash
sucessfully make 7 tsv files
```

can we collect the reads first before counting them?

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 8e6db9ae78393ade4eccd290ae8cefc4f8585331
slurm sub: 19237116


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 22fabf06464cd9b27175e72926eb9c7bdd87b6fd
slurm sub: 19237153

```bash
Caused by:
  Process `CSVTK_CONCAT (SRR15214153)` terminated with an error exit status (255)

Command executed:

  csvtk \
      concat \
       \
      --num-cpus 2 \
      --delimiter "     " \
      --out-delimiter " " \
      --out-file SRR15214153.tsv \
      SRR15214153.tsv

  cat <<-END_VERSIONS > versions.yml
  "CSVTK_CONCAT":
      csvtk: $(echo $( csvtk version | sed -e "s/csvtk v//g" ))
  END_VERSIONS

Command exit status:
  255
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: c307b78ccaf1f098efed2acbaa6cd154172c46c9
slurm sub: 19237245

```bash
[-        ] process > FILTLONG -
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'view'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 123 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see .nextflow.log file for more details
```
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 1e980eada285669e736e4e9a06bdf3750fe08e51
slurm sub: 19237255

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'collect'
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 7e2d3b049497ea3dde08f2e40fff543fc7e05193
slurm sub: 19237358 

```bash
[['id':'SRR19732514', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]
WARN: Input tuple does not match input set cardinality declared by process `CSVTK_CONCAT` -- offending value: [[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, [id:SRR19732729, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, [id:SRR19683891, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, [id:SRR19736685, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, [id:SRR19726169, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, [id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, [id:SRR19732514, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 901f82cee80bece8a119b706613ded08ad0f17f3
slurm sub: 19237364

```bash
[['id':'SRR19732514', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]
```

Right now I am stuck trying to pass just the paths of tables into the code. I think what we need is to re-tuple so that the list makes sense.

```bash
[['id':'SRR15214153', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/a2/6b074f14a308af0195566b786c09d5/SRR15214153.tsv, ['id':'SRR19683890', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/22/80c79296235eb54fcf5e0e566a1165/SRR19683890.tsv, ['id':'SRR19732729', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/1f/983172df307510c23f415c319bbd8b/SRR19732729.tsv, ['id':'SRR19683891', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/f4/45ed941f60c1cebefe70838b21d939/SRR19683891.tsv, ['id':'SRR19736685', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/22/b242a25e150577c8a295ed7f312eb7/SRR19736685.tsv, ['id':'SRR19726169', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/20/4394fe97be04c534a01073955ac750/SRR19726169.tsv, ['id':'SRR19732514', 'single_end':true], /scratch/bjl34716/nf_dev/gg-catalog/work/cc/434a78f20aaec4fb36598c9a3dc61d/SRR19732514.tsv]
```

[this might be something](https://stackoverflow.com/questions/67746419/how-to-merge-multiple-grouped-output-files-in-nextflow)


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
d282b78 - Benjamin Lorentz, Mon Feb 20 11:13:28 2023 -0500 : added page for monday
```

#### gg-catalog-nf

```bash
116b1ec - Benjamin Lorentz, Mon Feb 20 16:56:11 2023 -0500 : update main.nf
4ba4f10 - Benjamin Lorentz, Mon Feb 20 16:52:37 2023 -0500 : update main.nf
73e1e99 - Benjamin Lorentz, Mon Feb 20 16:44:39 2023 -0500 : update main.nf
5f28e45 - Benjamin Lorentz, Mon Feb 20 16:31:53 2023 -0500 : update main.nf
901f82c - Benjamin Lorentz, Mon Feb 20 16:28:51 2023 -0500 : update main.nf
7e2d3b0 - Benjamin Lorentz, Mon Feb 20 16:25:15 2023 -0500 : update main.nf
1e980ea - Benjamin Lorentz, Mon Feb 20 16:17:00 2023 -0500 : update main.nf
c307b78 - Benjamin Lorentz, Mon Feb 20 16:12:23 2023 -0500 : update main.nf
22fabf0 - Benjamin Lorentz, Mon Feb 20 16:06:15 2023 -0500 : update main.nf
8e6db9a - Benjamin Lorentz, Mon Feb 20 15:42:02 2023 -0500 : update main.nf
86d4ba9 - Benjamin Lorentz, Mon Feb 20 15:34:06 2023 -0500 : update main.nf
81be794 - Benjamin Lorentz, Mon Feb 20 15:30:38 2023 -0500 : update main.nf
:...skipping...
116b1ec - Benjamin Lorentz, Mon Feb 20 16:56:11 2023 -0500 : update main.nf
4ba4f10 - Benjamin Lorentz, Mon Feb 20 16:52:37 2023 -0500 : update main.nf
73e1e99 - Benjamin Lorentz, Mon Feb 20 16:44:39 2023 -0500 : update main.nf
5f28e45 - Benjamin Lorentz, Mon Feb 20 16:31:53 2023 -0500 : update main.nf
901f82c - Benjamin Lorentz, Mon Feb 20 16:28:51 2023 -0500 : update main.nf
7e2d3b0 - Benjamin Lorentz, Mon Feb 20 16:25:15 2023 -0500 : update main.nf
1e980ea - Benjamin Lorentz, Mon Feb 20 16:17:00 2023 -0500 : update main.nf
c307b78 - Benjamin Lorentz, Mon Feb 20 16:12:23 2023 -0500 : update main.nf
22fabf0 - Benjamin Lorentz, Mon Feb 20 16:06:15 2023 -0500 : update main.nf
8e6db9a - Benjamin Lorentz, Mon Feb 20 15:42:02 2023 -0500 : update main.nf
86d4ba9 - Benjamin Lorentz, Mon Feb 20 15:34:06 2023 -0500 : update main.nf
81be794 - Benjamin Lorentz, Mon Feb 20 15:30:38 2023 -0500 : update main.nf
85d771a - Benjamin Lorentz, Mon Feb 20 15:24:02 2023 -0500 : update main.nf
628ba9c - Benjamin Lorentz, Mon Feb 20 15:11:33 2023 -0500 : update main.nf
184e3d1 - Benjamin Lorentz, Mon Feb 20 15:07:58 2023 -0500 : update main.nf
01982ed - Benjamin Lorentz, Mon Feb 20 14:59:09 2023 -0500 : update main.nf
0b26db9 - Benjamin Lorentz, Mon Feb 20 14:32:04 2023 -0500 : update main.nf
9fb25e2 - Benjamin Lorentz, Mon Feb 20 14:29:12 2023 -0500 : update main.nf and add seqkit and csvtk
```
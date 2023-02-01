---
title: 'Minimap2 Implement'
date: 2023-02-01T15:22:23Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Finalize Homework 1 Stat 6220
- gg-catalog
  - Zhang
    - check in on slurm process 18102373
    - create an index process if the current index is not provided
    - create a minimap process
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

#### filtlong sequences

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 18246d0679dbaa18dba1f3bfd0e6c58b60a7e3f3
slurm sub: 18102373

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4SFcaf3eTKgfIn
executor >  slurm (6)
[77/dd425f] process > FILTLONG (2) [100%] 7 of 7, cached: 1 ✔

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4SFcaf3eTKgfIn
executor >  slurm (6)
[77/dd425f] process > FILTLONG (2) [100%] 7 of 7, cached: 1 ✔
Completed at: 31-Jan-2023 19:20:27
Duration    : 6h 6m 5s
CPU hours   : 445.5 (0.2% cached)
Succeeded   : 6
Cached      : 1
```

The process succeeded! I want to just grep to see how much is lost, then we can implement minimap2. 

```bash
# ceca
cat /scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'

gzip -dc /scratch/bjl34716/nf_dev/gg-catalog/work/bf/cd0e9d90cf34cdb99a3d93ff058a35/SRR15214153.fastq.gz |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
# colon 1
cat /scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
              
gzip -dc /scratch/bjl34716/nf_dev/gg-catalog/work/77/dd425f456f21a3fbacf529ba5a640b/SRR19683890.fastq.gz |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
# colon 2              
cat /scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
              
gzip -dc /scratch/bjl34716/nf_dev/gg-catalog/work/1f/d0449c3c31ded5272c2e65a75454f4/SRR19732729.fastq.gz |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'              

# duodenum
cat 	/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
              
gzip -dc /scratch/bjl34716/nf_dev/gg-catalog/work/c3/cb0257b83096676fb0a8827dff4344/SRR19683891.fastq.gz |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'              

# ileum

cat 	/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
              
gzip -dc /scratch/bjl34716/nf_dev/gg-catalog/work/19/ce4c3b7acedd6b572844513c172bbb/SRR19736685.fastq.gz |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'              
# jeju 1

cat /scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
              
gzip -dc /scratch/bjl34716/nf_dev/gg-catalog/work/9b/5c36f0555a56c569e799dd2713cf2b/SRR19726169.fastq.gz  |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'    

# jeju 2

cat /scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
              
gzip -dc /scratch/bjl34716/nf_dev/gg-catalog/work/4c/f37e696ab820873a38f3eb52fddeee/SRR19732514.fastq.gz |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'    
```

| ID | raw-fastq-records | filtlong-fastq-records | raw-bases | filtlong-bases |
| --- | --- | --- | --- | --- |
| SRR15214153 | 1984390 | 1965108 | 33649253344 | 33312767376 | 
| SRR19683890 | 3933708 | 3896255 | 75997734768 | 75237772044 |
| SRR19732729 | 1932693 | 1914473 | 35894296324 | 35535370004 |
| SRR19683891 | 2872317 | 2730287 | 22416650091 | 22192490145 |
| SRR19736685 | 4282202 | 4240693 | 72828594344 | 72100323222 |
| SRR19726169 | 521405 | 516348 | 8598356757 |  8512378786 | 
| SRR19732514 | 2147916 | 2126922 | 35960758459 | 35601162605 | 

#### Minimap2

I want to re-generate the indices to test out the module before trying to align the reads. 

gg-catalog rev: a9cec6072cfbe08b36108527501d5cd4b96b31ae
gg-catalog-nf rev: e9f11c46372401acd2eabc8710c225dbb138f029
slurm sub: 18145926

```bash
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `MINIMAP2_INDEX` declares 1 input channel but 0 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 80 or see '.nextflow.log' file for more details
[-        ] process > FILTLONG -
```

gg-catalog rev: a9cec6072cfbe08b36108527501d5cd4b96b31ae
gg-catalog-nf rev: c163ac97df060d61192ea029b1dec8660bba17e3
slurm sub: 18145989

```bash

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/eI4QuGjsolBRW
[4c/f37e69] process > FILTLONG (7) [100%] 7 of 7, cached: 7 ✔

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/eI4QuGjsolBRW
[4c/f37e69] process > FILTLONG (7) [100%] 7 of 7, cached: 7 ✔
Completed at: 01-Feb-2023 16:24:55
Duration    : 1m 5s
CPU hours   : 445.5 (100% cached)
Succeeded   : 0
Cached      : 7
```

gg-catalog rev: a9cec6072cfbe08b36108527501d5cd4b96b31ae
gg-catalog-nf rev: e9c16431fc4c7d2460d79e42ef9542c6f4823412
slurm sub: 18146210

```bash

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `MINIMAP2_INDEX` declares 1 input channel but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 88 or see '.nextflow.log' file for
 more details
[-        ] process > FILTLONG -
```

gg-catalog rev: a9cec6072cfbe08b36108527501d5cd4b96b31ae
gg-catalog-nf rev: 7a5622f5c9ca9c3400ea10914c72bd423e1f428f
slurm sub: 18146218

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/1Q5y3r2MinYTmY
executor >  slurm (3)
[9b/5c36f0] process > FILTLONG (6)       [100%] 7 of 7, cached: 7 ✔
[b1/d11106] process > MINIMAP2_INDEX (3) [  0%] 0 of 3

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/1Q5y3r2MinYTmY
executor >  slurm (3)
[9b/5c36f0] process > FILTLONG (6)       [100%] 7 of 7, cached: 7 ✔
[b1/d11106] process > MINIMAP2_INDEX (3) [ 66%] 2 of 3

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/1Q5y3r2MinYTmY
executor >  slurm (3)
[9b/5c36f0] process > FILTLONG (6)       [100%] 7 of 7, cached: 7 ✔
[9d/7f1d16] process > MINIMAP2_INDEX (2) [100%] 3 of 3 ✔
Completed at: 01-Feb-2023 16:36:03
Duration    : 3m 5s
CPU hours   : 445.7 (99.9% cached)
Succeeded   : 3
Cached      : 7
```

success!

gg-catalog rev: a9cec6072cfbe08b36108527501d5cd4b96b31ae
gg-catalog-nf rev: 13c5a642f6cebcbac7b45761b1bb515fe9e9fc35
slurm sub: 18146295

```bash

[-        ] process > FILTLONG -
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: Exception evaluating property 'meta' for nextflow.script.ChannelOut, Reason: groovy.lang.MissingPropertyException: No such property: meta for class: groovyx.gpars.dataflow.DataflowBroadcast
Possible solutions: head

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 89 or see '.nextflow.log' file for more details
No such variable: info
```

gg-catalog rev: a9cec6072cfbe08b36108527501d5cd4b96b31ae
gg-catalog-nf rev: 79914efbc4d640ec85010f16f471334739e98347
slurm sub: 18146340 

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Process `MINIMAP2_ALIGN` declares 5 input channels but 3 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 89 or see '.nextflow.log' file for more details
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or s
ee '.nextflow.log' file for more details
[-        ] process > FILTLONG -
```

We need to set up three processes, first run MINIMAP2 on the first host, then align the output to the second host and then align the output to the third host. 

### Todos for Tomorrow

- Finalize Homework 1 Stat 6220
  - include notes from Dr. Chohurdy
- gg-catalog
  - Zhang
    - create a minimap process
      - create a channel/process for each screening reference
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
4652ff2 - Benjamin Lorentz, Wed Feb 1 10:24:32 2023 -0500 : added page for wednesday
0254a3f - Benjamin Lorentz, Tue Jan 31 16:57:14 2023 -0500 : notes for tuesday
```

#### gg-catalog-nf 

```bash
79914ef - Benjamin Lorentz, Wed Feb 1 16:48:09 2023 -0500 : update main.nf
13c5a64 - Benjamin Lorentz, Wed Feb 1 16:45:56 2023 -0500 : update main.nf
7a5622f - Benjamin Lorentz, Wed Feb 1 16:32:24 2023 -0500 : update main.nf
e9c1643 - Benjamin Lorentz, Wed Feb 1 16:28:43 2023 -0500 : update main.nf
c163ac9 - Benjamin Lorentz, Wed Feb 1 16:23:34 2023 -0500 : update main.nf
e9f11c4 - Benjamin Lorentz, Wed Feb 1 16:05:41 2023 -0500 : add contam_input.nf and update main.nf
```

#### gg-catalog

```bash
a9cec60 - Benjamin Lorentz, Wed Feb 1 16:19:05 2023 -0500 : add contam.tsv and update test_params.yaml
```
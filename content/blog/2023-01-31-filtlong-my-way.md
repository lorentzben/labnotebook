---
title: 'Filtlong My Way'
date: 2023-01-31T13:53:11Z
draft: false
meta_img: "images/image.png"
tags:
  - "filtlong"
  - "nextflow"
  - "MAGs"
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

#### filtlong method

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: b6a282a44c39815a487bc043889f2acda506471b
slurm sub: 18088106

```bash
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Unqualified input value declaration has been deprecated - replace `tuple meta,..` with `tuple val(meta),..`

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 82 or see '.nextflow.log' file for more details
```

I updated the tuple val(meta) as opposed to just tuple(meta)

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 9c00bdc39899f0fc2e08215e814d7358f8ef8069
slurm sub: 18088261

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2D5suUy3CKU4Dj
executor >  slurm (6)
[50/34d5be] process > FILTLONG (6) [  0%] 0 of 7



Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2D5suUy3CKU4Dj
executor >  slurm (6)
[ab/3653da] process > FILTLONG (3) [ 42%] 3 of 7

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2D5suUy3CKU4Dj
executor >  slurm (6)
[50/34d5be] process > FILTLONG (6) [ 85%] 6 of 7

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2D5suUy3CKU4Dj
executor >  slurm (7)
[84/b1d0ad] process > FILTLONG (7) [ 85%] 6 of 7

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2D5suUy3CKU4Dj
executor >  slurm (7)
[84/b1d0ad] process > FILTLONG (7) [100%] 7 of 7 ✔
Completed at: 31-Jan-2023 09:42:57
Duration    : 2m 5s
CPU hours   : (a few seconds)
Succeeded   : 7
```

It looks like the process worked! just need to check that the filenames were correct. 

```bash
bjl34716@ss-sub3 code$ ls /scratch/bjl34716/nf_dev/gg-catalog/work/e9/3340702b8bfaf7751baa81ce33bc35
!{meta[1]}.fastq.gz  SRR15214153.fastq
```

They were not so we updated the meta now and we are gonna see if that makes a difference

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 3a15e249a62fdb21f0733c07555b15c017179581
slurm sub: 18088965

```bash
Caused by:
  Missing output file(s) `*.fastq.gz` expected by process `FILTLONG (1)`

Command executed:

  #!/usr/bin/env bash

  filtlong --min_length 2000 --keep_percent 99 !{reads} | gzip > $(!{meta}).fastq.gz

Command exit status:
  0
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 32c4ffbb099a0eee429492413e2f8b9d1a24ec7a
slurm sub: 18089014

```bash
bjl34716@ss-sub3 code$ ls /scratch/bjl34716/nf_dev/gg-catalog/work/59/cd56e1d4376da662a1826169114673
!{meta}.fastq.gz  SRR15214153.fastq
```

I changed the tuple to a val to see what that's saved as. 

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 5013937ec2c534d8655ea45699a11b50b5da6b38
slurm sub: 18089761

```bash
bjl34716@ss-sub3 code$ ls /scratch/bjl34716/nf_dev/gg-catalog/work/59/cd56e1d4376da662a1826169114673
!{meta}.fastq.gz  SRR15214153.fastq
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 265ae8c55077c8630e9810a9ef56654a992edf19
slurm sub: 18090526

```bash
bjl34716@ss-sub3 code$ ls /scratch/bjl34716/nf_dev/gg-catalog/work/f1/48bc62524c5dad4015072dcf511a89
!{meta}.fastq.gz  SRR15214153.fastq
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: f563221539ac1a70dad2bb2b8500401c157e9707
slurm sub: 18091707

```bash
bjl34716@ss-sub3 code$ ls /scratch/bjl34716/nf_dev/gg-catalog/work/e7/30e6363d79f7afe750ea5635db07ec
!{meta}.fastq.gz  SRR15214153.fastq
```

I tried to subset the id name

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: ef6084c5517fcfb90bb8284f0c7a361a37dcbef8
slurm sub: 18092022

```bash
 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'getAt'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 74 or see '.nextflow.log' file for more details
```


gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 49b67dd796e0db232065ee9c511fa93ece5bcd0c
slurm sub: 18092156

```bash
bjl34716@ss-sub3 code$ ls /scratch/bjl34716/nf_dev/gg-catalog/work/b9/28a3e2df5771d04532ebecb23e222c
out.fastq.gz  SRR15214153.fastq
nano /scratch/bjl34716/nf_dev/gg-catalog/work/b9/28a3e2df5771d04532ebecb23e222c/.command.out
!{meta}
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 23631e19b7fcdffda0c7f936d1307608b685c50e
slurm sub: 18092883

```bash

Caused by:
  No such variable: id -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 90

Source block:
  def prefix = task.ext.prefix ?: "${meta.id}"
  '''
      #!/usr/bin/env bash

      echo ${prefix}

      filtlong --min_length 2000 --keep_percent 99 !{reads} | gzip > out.fastq.gz

      '''

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line
```

so im gonna try to slice the map since it will print out to error term

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 02f91146b1310ca20548eafc8ce9d2fd25f11ef4
slurm sub: 18092985

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4tpiFMNKtFlzij
[-        ] process > FILTLONG -
Completed at: 31-Jan-2023 10:53:47
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
```

???

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: a0863d45e84305f23a546f821d16f28e08222569
slurm sub: 18093169

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/1LUCInBj6clhqI
[-        ] process > FILTLONG -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/1LUCInBj6clhqI
[-        ] process > FILTLONG -
Completed at: 31-Jan-2023 10:59:22
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: c525aaa9edd34822e8cf9b95496a4759bc4499dc
slurm sub: 18093727

```bash
Caused by:
  No such variable: id -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 90

Source block:
  def prefix = task.ext.prefix ?: "${meta.id}"
  '''
      #!/usr/bin/env bash
  
      echo ${prefix}
  
      filtlong --min_length 2000 --keep_percent 99 !{reads} | gzip > out.fastq.gz
  
      '''
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: a19d03914932a2770bff16109500d4e45be5c633
slurm sub: 18093975

```bash
cached the output :(
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 7cd6bbf42f0257700a8827b841499a2ac4ef4e01
slurm sub: 18094934

```bash
it doesnt show the dirs
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: eb5139b7f96705881e7f4d24516f3a5b1433a8f3
slurm sub: 18095327

```bash
bjl34716@ss-sub3 code$ ls /scratch/bjl34716/nf_dev/gg-catalog/work/ea/7639d813df1b9d0bb104d1e55f68fa
out.fastq.gz  SRR15214153.fastq

nano /scratch/bjl34716/nf_dev/gg-catalog/work/ea/7639d813df1b9d0bb104d1e55f68fa/.command.out
!{reads}
!{meta}
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 8de6983356049fed7fee23e7d384c97a8b1e7902
slurm sub:  18095412

```bash
???
```


gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 9177c1740a5595db857e3dd1b5d8b3f8b82f2713
slurm sub: 18095556  

```bash
This was running for like 20 mins
```

I updated the outname and I wanted to see if that works

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 530bf63bbdb4d06a86a25c96ed4cca4252131362
slurm sub: 18097629

```bash
1/7 finished but 6 ended with error code 140

bjl34716@ss-sub3 code$ ls -lah /scratch/bjl34716/nf_dev/gg-catalog/work/9b/5c36f0555a56c569e799dd2713cf2b
total 5.4G
drwxr-xr-x. 2 bjl34716 sealab 4.0K Jan 31 12:34 .
drwxr-xr-x. 4 bjl34716 sealab 4.0K Jan 31 11:51 ..
-rw-r--r--. 1 bjl34716 sealab    0 Jan 31 11:52 .command.begin
-rw-r--r--. 1 bjl34716 sealab 524K Jan 31 12:34 .command.err
-rw-r--r--. 1 bjl34716 sealab 524K Jan 31 12:34 .command.log
-rw-r--r--. 1 bjl34716 sealab    0 Jan 31 11:52 .command.out
-rw-r--r--. 1 bjl34716 sealab  11K Jan 31 11:52 .command.run
-rw-r--r--. 1 bjl34716 sealab  169 Jan 31 11:52 .command.sh
-rw-r--r--. 1 bjl34716 sealab  249 Jan 31 12:34 .command.trace
-rw-r--r--. 1 bjl34716 sealab    1 Jan 31 12:34 .exitcode
lrwxrwxrwx. 1 bjl34716 sealab   66 Jan 31 11:52 SRR19726169.fastq -> /scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq
-rw-r--r--. 1 bjl34716 sealab 5.4G Jan 31 12:34 SRR19726169.fastq.gz
```

gg-catalog rev: 82c851fc4a65d5974162775f6fba1a0a00cd937e 
gg-catalog-nf rev: 18246d0679dbaa18dba1f3bfd0e6c58b60a7e3f3
slurm sub: 18102373

```bash
```

This run has been going for 3 hours so far, and has 2 seqs left to examine. 

### homework 1

I have one question remaining for homework 1 which is for the MLE model, do we keep age in the model and just add in the other two variables?

### Todos for Tomorrow

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
  
### Git commits

#### Labnotebook

```bash
3bdd79f - Benjamin Lorentz, Tue Jan 31 08:54:26 2023 -0500 : page for tuesday
095da01 - Benjamin Lorentz, Mon Jan 30 16:59:04 2023 -0500 : end of monday
```

#### gg-catalog-nf

```bash
18246d0 - Benjamin Lorentz, Tue Jan 31 13:13:27 2023 -0500 : update main.nf
530bf63 - Benjamin Lorentz, Tue Jan 31 11:33:08 2023 -0500 : update main.nf
9177c17 - Benjamin Lorentz, Tue Jan 31 11:28:35 2023 -0500 : update main.nf
8de6983 - Benjamin Lorentz, Tue Jan 31 11:23:09 2023 -0500 : update main.nf
eb5139b - Benjamin Lorentz, Tue Jan 31 11:19:22 2023 -0500 : update main.nf
7cd6bbf - Benjamin Lorentz, Tue Jan 31 11:16:45 2023 -0500 : update main.nf
5369008 - Benjamin Lorentz, Tue Jan 31 11:11:18 2023 -0500 : try this last one
a9c6f82 - Benjamin Lorentz, Tue Jan 31 11:09:51 2023 -0500 : try this
aa101fe - Benjamin Lorentz, Tue Jan 31 11:08:43 2023 -0500 : try to not surround meta
a19d039 - Benjamin Lorentz, Tue Jan 31 11:06:49 2023 -0500 : update main.nf
c525aaa - Benjamin Lorentz, Tue Jan 31 11:03:26 2023 -0500 : update main.nf
a0863d4 - Benjamin Lorentz, Tue Jan 31 10:58:29 2023 -0500 : update main.nf
:...skipping...
18246d0 - Benjamin Lorentz, Tue Jan 31 13:13:27 2023 -0500 : update main.nf
530bf63 - Benjamin Lorentz, Tue Jan 31 11:33:08 2023 -0500 : update main.nf
9177c17 - Benjamin Lorentz, Tue Jan 31 11:28:35 2023 -0500 : update main.nf
8de6983 - Benjamin Lorentz, Tue Jan 31 11:23:09 2023 -0500 : update main.nf
eb5139b - Benjamin Lorentz, Tue Jan 31 11:19:22 2023 -0500 : update main.nf
7cd6bbf - Benjamin Lorentz, Tue Jan 31 11:16:45 2023 -0500 : update main.nf
5369008 - Benjamin Lorentz, Tue Jan 31 11:11:18 2023 -0500 : try this last one       
a9c6f82 - Benjamin Lorentz, Tue Jan 31 11:09:51 2023 -0500 : try this
aa101fe - Benjamin Lorentz, Tue Jan 31 11:08:43 2023 -0500 : try to not surround meta
a19d039 - Benjamin Lorentz, Tue Jan 31 11:06:49 2023 -0500 : update main.nf
c525aaa - Benjamin Lorentz, Tue Jan 31 11:03:26 2023 -0500 : update main.nf
a0863d4 - Benjamin Lorentz, Tue Jan 31 10:58:29 2023 -0500 : update main.nf
02f9114 - Benjamin Lorentz, Tue Jan 31 10:52:08 2023 -0500 : update main.nf
23631e1 - Benjamin Lorentz, Tue Jan 31 10:48:28 2023 -0500 : update main.nf
49b67dd - Benjamin Lorentz, Tue Jan 31 10:41:52 2023 -0500 : update main.nf
ef6084c - Benjamin Lorentz, Tue Jan 31 10:36:14 2023 -0500 : update main.nf
f563221 - Benjamin Lorentz, Tue Jan 31 10:32:15 2023 -0500 : update main.nf
265ae8c - Benjamin Lorentz, Tue Jan 31 10:22:15 2023 -0500 : update main.nf
5013937 - Benjamin Lorentz, Tue Jan 31 10:17:29 2023 -0500 : update main.nf
32c4ffb - Benjamin Lorentz, Tue Jan 31 10:09:35 2023 -0500 : update main.nf
3a15e24 - Benjamin Lorentz, Tue Jan 31 10:04:06 2023 -0500 : update main.nf
9c00bdc - Benjamin Lorentz, Tue Jan 31 09:38:19 2023 -0500 : update main.nf
b6a282a - Benjamin Lorentz, Tue Jan 31 09:30:36 2023 -0500 : update main.nf
```

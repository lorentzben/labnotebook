---
title: 'Ade Old Method'
date: 2023-03-02T13:58:42Z
draft: false
meta_img: "images/image.png"
tags:
  - "ade"
  - "nextflow"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Tomorrow

- Admin
  - add delegate on oneusg (Done)
- Ade 
  - set up the old pipeline analysis to send the feature table over
    - script for 21
    - script for 28
  - send code 
- Stat 6220 
  - Review for Midterm
  - Examine the Group Proposal
- Jackwood Blast
  - meet Ben and Brian TBD
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
  
### Ade 

#### Script for 21

First method, we can just copy over the nextflow dir from the home dir

If this doesn't work we can just call it as a nextflow script. 

automate_16_nf rev: 82bf6d435ddb6d4467708e21fc1920d57cd8ad11
cycle 4 rev: 1db501273745aa4d57af7413dcc421b7a847a0fd
slurm sub: 19586422

```bash
cp: cannot stat ‘/work/sealab/bjl34716/ade/automate_16_nf/*’: No such file or directory
/var/lib/slurmd/job19586422/slurm_script: line 18: cd: /scratch/bjl34716/ade/cycle-4/old-day-21: No such file or directory
N E X T F L O W  ~  version 20.04.1
Not a valid project name: main.nf
cat: out.txt: No such file or directory
cp: missing destination file operand after ‘report.Rmd’
Try 'cp --help' for more information.
cat: out.txt: No such file or directory
cp: missing destination file operand after ‘make_report.sh’
Try 'cp --help' for more information.
cat: out.txt: No such file or directory
cp: missing destination file operand after ‘init_and_refresh.R’
Try 'cp --help' for more information.
cat: out.txt: No such file or directory
cp: missing destination file operand after ‘renv.lock’
Try 'cp --help' for more information.
cat: out.txt: No such file or directory
find: ‘lefse/result/’: No such file or directory
INFO:    Converting OCI blobs to SIF format
INFO:    Starting build...
Getting image source signatures
Copying blob sha256:2aa31e5eaa2f63b21f0a451e58e0bdf8a356a365b4a0edc3cb0f7699c463a538
Copying blob sha256:325ff13b0eefc7ca0ea6a59d56312d8a542da9ce0ccfc03079fa42ed1d39368c
Copying blob sha256:0fe0fc85dce36a81438e072642d4d5b7a5cc8ef1788fc169617e974198b203f9
Copying blob sha256:2bf26c06398db24f9776d9f5d45b49e4ffcb7f4bc90ac9a522c7dd510deca688
Copying blob sha256:b246d31b57592efb5f6bd3a98cceef4ae29e9b4f0e52c72a7b7162a541f4b489
Copying blob sha256:75c82d8e4bbf1f0dc2618a59f2490f97a8831b991129b72c268d9327d2604705
Copying blob sha256:debce101a705a0b612a556daedb6d93ca5b3ec0d8cc3b20b57b8e22ca7e64d1b
Copying blob sha256:ca3708d6ea91658b28ae14d97f41ed44ec3a8d41b4bc042f668d49ef6a4fd196
```

automate_16_nf rev: 82bf6d435ddb6d4467708e21fc1920d57cd8ad11
cycle 4 rev: 69e393dad8c09a10672c480cd45cfec37b1f4f00
slurm sub: 19586915

```bash
cp: target ‘/scratch/bjl34716/ade/cycle-4/old-day-21’ is not a directory
/var/lib/slurmd/job19586915/slurm_script: line 18: cd: /scratch/bjl34716/ade/cycle-4/old-day-21: No such file or directory
N E X T F L O W  ~  version 20.04.1
Not a valid project name: main.nf
/var/lib/slurmd/job19586915/slurm_script: line 29: -resume: command not found
cat: out.txt: No such file or directory
cp: missing destination file operand after ‘report.Rmd’
Try 'cp --help' for more information.
cat: out.txt: No such file or directory
cp: missing destination file operand after ‘make_report.sh’
Try 'cp --help' for more information.
cat: out.txt: No such file or directory
cp: missing destination file operand after ‘init_and_refresh.R’
Try 'cp --help' for more information.
cat: out.txt: No such file or directory
cp: missing destination file operand after ‘renv.lock’
Try 'cp --help' for more information.
cat: out.txt: No such file or directory
find: ‘lefse/result/’: No such file or directory
INFO:    Converting OCI blobs to SIF format
```

automate_16_nf rev: 82bf6d435ddb6d4467708e21fc1920d57cd8ad11
cycle 4 rev: 6ef9f022997aa62afb8526e88489b2fca2de5d80
slurm sub: 19587306

```bash

```


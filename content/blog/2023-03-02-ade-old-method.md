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

### Todos for Today

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
executor >  local (15)
[-        ] process > SetupRPackages             -
[4d/c6a253] process > VerifyManifest (1)         [100%] 1 of 1 ✔
[49/c9a952] process > CheckSinglePaired (1)      [100%] 1 of 1 ✔
[62/f444d9] process > GenerateSeqObject (1)      [100%] 1 of 1 ✔
[64/9921bc] process > QualControl (1)            [100%] 1 of 1 ✔
[8b/99c241] process > FindCutoffs (1)            [100%] 1 of 1 ✔
[d8/f8a093] process > Denoise (1)                [100%] 1 of 1 ✔
[5a/f79c93] process > FeatureVisualization (1)   [100%] 1 of 1 ✔
[6d/ccfb49] process > TreeConstruction (1)       [100%] 1 of 1 ✔
[a6/84b066] process > ExportTable (1)            [100%] 1 of 1 ✔
[cb/a516c2] process > DetermineDepth (1)         [100%] 1 of 1 ✔
[-        ] process > AlphaDiversityMeasure (1)  -
[a3/59d2c3] process > AssignTaxonomy (1)         [100%] 1 of 1, failed: 1 ✘
[79/b7c9cb] process > CalcRareDepth (1)          [100%] 1 of 1 ✔
[-        ] process > RareCurveCalc              -
[-        ] process > AlphaDiversitySignificance -
[-        ] process > BetaDiversitySignificance  -
[-        ] process > GeneratePhylogeneticTrees  -
[-        ] process > LefseFormat                -
[-        ] process > LefseAnalysis              -
[2b/72881f] process > ExportSetup (1)            [100%] 1 of 1 ✔
[-        ] process > GenerateReport             -
WARN: Killing pending tasks (2)
Error executing process > 'AssignTaxonomy (1)'

Caused by:
  Process `AssignTaxonomy (1)` terminated with an error exit status (1)
Command executed:

  #!/usr/bin/env bash

  if [ ! -f "16s-whole-seq-classifier.qza" ]; then
  echo "Error, download the classifier from readme"
  exit 1
  fi
  if [ ! -f "515-806-classifier.qza" ]; then
  echo "Error, download the classifier from readme"
  exit 1
  fi

  qiime feature-classifier classify-sklearn     --i-classifier 16s-whole-seq-classifier.qza     --i-reads rep-seqs-dada2.qza     --p-confidence 0.6     --o-classification taxonomy.qza

  qiime metadata tabulate     --m-input-file taxonomy.qza     --o-visualization taxonomy.qzv

Command exit status:
  1

Command output:
  Error, download the classifier from readme

Command wrapper:
  Error, download the classifier from readme

Work dir:
  /scratch/bjl34716/ade/cycle-4/old-day-21/work/a3/59d2c3d6b56157479858f0f1e6c662

Tip: view the complete command output by changing to the process work dir and entering the command `cat .command.out`

/var/lib/slurmd/job19587306/slurm_script: line 30: -resume: command not found
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
INFO:    Using cached SIF image
Fatal error: cannot open file 'init_and_refresh.R': No such file or directory
```

I copied the classifiers over:

automate_16_nf rev: 82bf6d435ddb6d4467708e21fc1920d57cd8ad11
cycle 4 rev: 6ef9f022997aa62afb8526e88489b2fca2de5d80
slurm sub: 19590971

```bash
```

automate_16_nf rev: 82bf6d435ddb6d4467708e21fc1920d57cd8ad11
cycle 4 rev: ce3cee01e5826dc2fb51eef86db5089eba069ab4
slurm sub: 19597932

```bash
```

### Todos for Tomorrow

- Stat 6220 
  - midterm exam
- Ade 
  - review slurm 19590971
  - review slurm 19597932
  - send code 
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


### Git Commits

#### Lab Notebook

```bash
6866df7 - Benjamin Lorentz, Thu Mar 2 11:01:01 2023 -0500 : notes to get 21 setup and run 11 minutes
b17c950 - Benjamin Lorentz, Thu Mar 2 08:59:59 2023 -0500 : added page for thursday
e5238ee - Benjamin Lorentz, Wed Mar 1 17:00:39 2023 -0500 : updates for end of wednesday
```

#### cycle 4 

```bash
ce3cee0 - Benjamin Lorentz, Thu Mar 2 14:03:16 2023 -0500 : update day 28 script and metadata
6ef9f02 - Benjamin Lorentz, Thu Mar 2 10:48:13 2023 -0500 : update old_methods/slurm-21-submission.sh
69e393d - Benjamin Lorentz, Thu Mar 2 10:45:37 2023 -0500 : update old_methods/slurm-21-submission.sh
56239bc - Benjamin Lorentz, Thu Mar 2 10:43:14 2023 -0500 : update old_method/slurm-21-submission.sh
1db5012 - Benjamin Lorentz, Thu Mar 2 10:40:11 2023 -0500 : add new script for old method ade
088364c - Benjamin Lorentz, Wed Mar 1 16:59:00 2023 -0500 : added slurm-submission.sh
```
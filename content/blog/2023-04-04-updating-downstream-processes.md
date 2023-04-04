---
title: 'Updating Downstream Processes'
date: 2023-04-04T12:59:54Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Today

- Class
  - Examine Comments on Word Doc
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Examine HQ analysis
  - Examine How SRS changes result vs rarefying
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Ade

#### Future Tools

SRS: Alternative to Rarefaction

FIGARO: https://github.com/Zymo-Research/figaro
Method to objectively select forward and reverse cutoffs for DADA2 

#### Updating Downstream Analysis

01

work dir: /scratch/bjl34716/ade/cycle-4/work/b3/db8cbf275a0639d380315ba704b50b

cycle 4 rev: 68787bd90aaa83c0aae9193946f37af83eede6e3
visualize ampliseq rev: c85baf8228021af7259b6edd0e6a551541624793
slurm sub: 20701450

```bash
processing file: 01_report_MbA.Rmd
  Quitting from lines 38-125 (01_report_MbA.Rmd) 
  Error in parse(text = x, srcfile = src) : <text>:23:4: unexpected symbol
  22: # if filtered table is provided:
  23: if file.exists
         ^
  Calls: <Anonymous> ... <Anonymous> -> parse_all -> parse_all.character -> parse
  In addition: Warning message:
  In readLines(paste0("item_of_interest.csv")) :
    incomplete final line found on 'item_of_interest.csv'
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/c3/73d320967e4e6440d9119ae4cb2b0a

Tip: you can try to figure out whats wrong by changing to the process work dir and showing the script file named .command.sh
```

cycle 4 rev: 68787bd90aaa83c0aae9193946f37af83eede6e3
visualize ampliseq rev: ece17a893a011822e814b1b53a79bfc92731dcb5
slurm sub: 20701695

```bash
Completed at: 04-Apr-2023 10:02:36
Duration    : 2m 7s
CPU hours   : 1.9 (99.2% cached)
Succeeded   : 1
Cached      : 27
```

02

This is the graphlan trees which come from the graphlan process
which need a biom table so we have the generate biom function

cycle 4 rev: 68787bd90aaa83c0aae9193946f37af83eede6e3
visualize ampliseq rev: 5c37ccc393e10a36538942ac80e40b4c003ef8a4
slurm sub: 20702859

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
    File ".command.sh", line 16
      if [[! -f feature-table.qza]]; then
           ^
  SyntaxError: invalid syntax

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/9c/b73a1f38ca6efc63f96dff38020a8e
```

cycle 4 rev: 68787bd90aaa83c0aae9193946f37af83eede6e3
visualize ampliseq rev: 6ee38537f6265f0a90c7501e20c693533f47a72e
slurm sub: 20703269

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
  Traceback (most recent call last):
    File ".command.sh", line 16, in <module>
      if not os.path.isfile(feature-table.qza):
  NameError: name 'os' is not defined

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/ea/b6c29b5be565c37793239816c950fd
```

cycle 4 rev: 68787bd90aaa83c0aae9193946f37af83eede6e3
visualize ampliseq rev: 22c4d21010222a6bae72c7d5b8519685a2f2177e
slurm sub: 20703474

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
  Traceback (most recent call last):
    File ".command.sh", line 17, in <module>
      if not os.path.isfile(feature-table.qza):
  NameError: name 'feature' is not defined

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/21/7fbdfb095c3172355ec938d7b4e0f1
```

cycle 4 rev: 68787bd90aaa83c0aae9193946f37af83eede6e3
visualize ampliseq rev: cd6f0204569ac99073929bf87b6487b1e4c92e2c
slurm sub: 20703809

```bash
Completed at: 04-Apr-2023 11:18:46
Duration    : 8m 6s
CPU hours   : 1.8 (95.2% cached)
Succeeded   : 3
Cached      : 25
```

03

Looks good the if uses qza table and the else uses table qza

04

Looks good, uses the Core metric out vectors which uses the filtered table if its in the if


05

Looks good, uses the Core metric out vectors which uses the filtered table if its in the if

Testing updated ordioi and samplenames 

cycle 4 rev: 2259deb3df703ac33b914312d295379c729b73c8 
visualize ampliseq rev: 2d5a58f2b3a77eef458fa67291d4d553ebedda92
slurm sub: 20705688

```bash
```

06

Looks good uses updated table for phyloseq object and core metric out.

TODO possibly update to NMDS in the future

07



08

09

10

11

12

13


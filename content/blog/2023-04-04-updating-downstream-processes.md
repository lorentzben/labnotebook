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
Completed at: 04-Apr-2023 12:20:38
Duration    : 1m 7s
CPU hours   : 1.8 (99.6% cached)
Succeeded   : 1
Cached      : 27
```

06

Looks good uses updated table for phyloseq object and core metric out.

TODO possibly update to NMDS in the future

Make a 6b that uses phyloseq and NMDS

07

cycle 4 rev: 2259deb3df703ac33b914312d295379c729b73c8 
visualize ampliseq rev: 44da9169e2a3b844f9f6306ffc1df8012f559097
slurm sub: 20708045

```bash
Completed at: 04-Apr-2023 14:18:19
Duration    : 2m 9s
CPU hours   : 1.8 (99% cached)
Succeeded   : 2
Cached      : 26
```

Looks good, updated with an if else.

08

Updated previously and looks good


09

Looks good, comes from core metric python

10

Looks good, could rebuild to include read_qza but not needed right now.

TODO fix the x axis 

11

Looks good, previously updated 


12

Looks good, previously updated 

TODO update x axis names

13

Looks good, previously updated 

All together

cycle 4 rev: 2259deb3df703ac33b914312d295379c729b73c8 
visualize ampliseq rev: 44da9169e2a3b844f9f6306ffc1df8012f559097
slurm sub: 20709891

```bash
Sucess
```

All together no controls

cycle 4 rev: e62efa40d11fbc47daeda40349372c6c90650869 
visualize ampliseq rev: 44da9169e2a3b844f9f6306ffc1df8012f559097
slurm sub: 20711714

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Already-up-to-date
Launching `https://github.com/lorentzben/visualize-ampliseq` [crazy_woese] DSL2 - revision: 44da9169e2 [control]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /scratch/bjl34716/ade/cycle-4/litter
metadata : /scratch/bjl34716/ade/cycle-4/litter/metadata.tsv
item of interest : Treatment
ordered item of interest : /home/bjl34716/ade/cycle-4/litter/order_item_of_interest.csv
outdir   : /work/sealab/bjl34716/ade/cycle-4/litter-no-control
rarefaction depth : 16500
controls:
profile : slurm,singularity

Process `RAREFACTIONPLOT` declares 3 input channels but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 98 or see '.nextflow.log' file for more details
```

cycle 4 rev: e62efa40d11fbc47daeda40349372c6c90650869
visualize ampliseq rev: 00e4f528028ab316e7f1822bdbcd512ad9efe44f
slurm sub: 20712086

```bash
Launching `https://github.com/lorentzben/visualize-ampliseq` [fervent_gilbert] DSL2 - revision: 00e4f52802 [control]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /scratch/bjl34716/ade/cycle-4/litter
metadata : /scratch/bjl34716/ade/cycle-4/litter/metadata.tsv
item of interest : Treatment
ordered item of interest : /home/bjl34716/ade/cycle-4/litter/order_item_of_interest.csv
outdir   : /work/sealab/bjl34716/ade/cycle-4/litter-no-control
rarefaction depth : 16500
controls:
profile : slurm,singularity

No such variable: qza_table

 -- Check script /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf at line: 98 or see .nextflow.log file for more details
```

cycle 4 rev: e62efa40d11fbc47daeda40349372c6c90650869
visualize ampliseq rev: 8927ca7a56fa556a374f87a6bceeb66a03076010
slurm sub: 20712265

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [voluminous_liskov] DSL2 - revision: 8927ca7a56 [control]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /scratch/bjl34716/ade/cycle-4/litter
metadata : /scratch/bjl34716/ade/cycle-4/litter/metadata.tsv
item of interest : Treatment
ordered item of interest : /home/bjl34716/ade/cycle-4/litter/order_item_of_interest.csv
outdir   : /work/sealab/bjl34716/ade/cycle-4/litter-no-control
rarefaction depth : 16500
controls:
profile : slurm,singularity

Process `GENERATERAREFACTIONCURVE` declares 6 input channels but 5 were specified

 -- Check script /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf at line: 111 or see .nextflow.log file for more details
[-        ] process > ORDERIOI -

```


cycle 4 rev: e62efa40d11fbc47daeda40349372c6c90650869
visualize ampliseq rev: 3046d9a95ea6cc3a3ad1a01c01df5832bf580ad9
slurm sub: 20712429

```bash
Execution cancelled -- Finishing pending tasks before exit
Error executing process > 'REPORT01BARPLOT (1)'

Caused by:
  Not a valid path value: 'NO_FILE'


Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line


[30/e8a1e0] Submitted process > ORDERIOI (1)
```


cycle 4 rev: e62efa40d11fbc47daeda40349372c6c90650869
visualize ampliseq rev: 99b5f0e66d1e315ba6f540e011136894908b2936
slurm sub: 20712705

```bash
Error executing process > 'RAREFACTIONPLOT (1)'

Caused by:
  Not a valid path value: 'NO_FILE'


Tip: you can try to figure out whats wrong by changing to the process work dir and showing the script file named .command.sh
```

cycle 4 rev: e62efa40d11fbc47daeda40349372c6c90650869
visualize ampliseq rev: ca5db365095b4e5f7136573a3fdf48e165634881
slurm sub: 20713524

```bash
Error executing process > 'RAREFACTIONPLOT (1)'

Caused by:
  Path value cannot be empty


Tip: you can try to figure out whats wrong by changing to the process work dir and showing the script file named `.command.sh`
```

cycle 4 rev: e62efa40d11fbc47daeda40349372c6c90650869
visualize ampliseq rev: a092c7d566a2ff169cf77e3b7cdd095d733eea14
slurm sub: 20713693

```bash
Error executing process > 'RAREFACTIONPLOT (1)'

Caused by:
  Not a valid path value: '.'


Tip: you can try to figure out whats wrong by changing to the process work dir and showing the script file named `.command.sh`
```

cycle 4 rev: e62efa40d11fbc47daeda40349372c6c90650869
visualize ampliseq rev: 95fc0de1307b8208201b117f73d303f197793627
slurm sub: 20714098

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
  Traceback (most recent call last):
    File ".command.sh", line 6, in <module>
      read_ord_ioi = pd.read_table("order_item_of_interest.csv",index_col=0,sep=',')
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 767, in read_table
      return read_csv(**locals())
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 688, in read_csv
      return _read(filepath_or_buffer, kwds)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 454, in _read
      parser = TextFileReader(fp_or_buf, **kwds)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 948, in __init__
      self._make_engine(self.engine)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 1180, in _make_engine
      self._engine = CParserWrapper(self.f, **self.options)
    File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 2010, in __init__
      self._reader = parsers.TextReader(src, **kwds)
    File "pandas/_libs/parsers.pyx", line 540, in pandas._libs.parsers.TextReader.__cinit__
  pandas.errors.EmptyDataError: No columns to parse from file

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/f9/e168dbb3046c5c2bb72f4152b87d16
```


cycle 4 rev: e4cda0d877e7f7a9a1c695be00a3f9d445830311
visualize ampliseq rev: 95fc0de1307b8208201b117f73d303f197793627
slurm sub: 20714420

```bash

Command error:
  
  
  processing file: 08_report.Rmd
  Quitting from lines 19-37 (08_report.Rmd) 
  Error in read.table(file = file, header = header, sep = sep, quote = quote,  : 
    no lines available in input
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.csv -> read.table
  In addition: Warning message:
  In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  Execution halted
  
  
  processing file: 08_report.Rmd
  Quitting from lines 19-37 (08_report.Rmd) 
  Error in read.table(file = file, header = header, sep = sep, quote = quote,  : 
    no lines available in input
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read.csv -> read.table
  In addition: Warning message:
  In readLines("item_of_interest.csv") :
    incomplete final line found on 'item_of_interest.csv'
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/7e/ee9e19a09d81f78c81e79517004c4c
```

#### Fix the order ioi method

#### Update Report 10 

#### Update Report 12

#### 6b NMDS Plots

### Todos for Tomorrow

- Class
  - Examine Comments on Word Doc
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix Downstream Uses of table with filtered
    - ORDIOI issue
    - Update 10
    - Update 12
  - Examine How SRS changes result vs rarefying
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

### Git Commits

#### Labnotebook

```bash
5f47a34 - Benjamin Lorentz, Tue Apr 4 12:17:35 2023 -0400 : added notes before lunch
c1ebf72 - Benjamin Lorentz, Tue Apr 4 11:45:26 2023 -0400 : progress so far
9f1f489 - Benjamin Lorentz, Tue Apr 4 09:22:06 2023 -0400 : page for tuesday
```

#### cycle 4

```bash
e4cda0d - Benjamin Lorentz, Tue Apr 4 17:03:44 2023 -0400 : change filename for ordered ioi
e62efa4 - Benjamin Lorentz, Tue Apr 4 15:04:37 2023 -0400 : update ade_vis_params
2259deb - Benjamin Lorentz, Tue Apr 4 12:15:24 2023 -0400 : update params and add order item of interest
```

#### visualize ampliseq

```bash
95fc0de - Benjamin Lorentz, Tue Apr 4 16:51:37 2023 -0400 : update main.nf
8f1fadc - Benjamin Lorentz, Tue Apr 4 16:45:00 2023 -0400 : update main.nf
a092c7d - Benjamin Lorentz, Tue Apr 4 16:37:24 2023 -0400 : update main.nf
ca5db36 - Benjamin Lorentz, Tue Apr 4 16:33:00 2023 -0400 : update main.nf
99b5f0e - Benjamin Lorentz, Tue Apr 4 16:28:28 2023 -0400 : update main.nf
3046d9a - Benjamin Lorentz, Tue Apr 4 16:18:11 2023 -0400 : update main.nf
8927ca7 - Benjamin Lorentz, Tue Apr 4 16:12:54 2023 -0400 : update main.nf
00e4f52 - Benjamin Lorentz, Tue Apr 4 16:06:09 2023 -0400 : update main.nf
44da916 - Benjamin Lorentz, Tue Apr 4 14:12:00 2023 -0400 : update main.nf
2d5a58f - Benjamin Lorentz, Tue Apr 4 12:10:49 2023 -0400 : update 05_report
cd6f020 - Benjamin Lorentz, Tue Apr 4 11:07:13 2023 -0400 : update main.nf
22c4d21 - Benjamin Lorentz, Tue Apr 4 10:54:05 2023 -0400 : update main.nf
6ee3853 - Benjamin Lorentz, Tue Apr 4 10:44:45 2023 -0400 : update main.nf
:...skipping...
95fc0de - Benjamin Lorentz, Tue Apr 4 16:51:37 2023 -0400 : update main.nf
8f1fadc - Benjamin Lorentz, Tue Apr 4 16:45:00 2023 -0400 : update main.nf
a092c7d - Benjamin Lorentz, Tue Apr 4 16:37:24 2023 -0400 : update main.nf
ca5db36 - Benjamin Lorentz, Tue Apr 4 16:33:00 2023 -0400 : update main.nf
99b5f0e - Benjamin Lorentz, Tue Apr 4 16:28:28 2023 -0400 : update main.nf
3046d9a - Benjamin Lorentz, Tue Apr 4 16:18:11 2023 -0400 : update main.nf
8927ca7 - Benjamin Lorentz, Tue Apr 4 16:12:54 2023 -0400 : update main.nf
00e4f52 - Benjamin Lorentz, Tue Apr 4 16:06:09 2023 -0400 : update main.nf
44da916 - Benjamin Lorentz, Tue Apr 4 14:12:00 2023 -0400 : update main.nf
2d5a58f - Benjamin Lorentz, Tue Apr 4 12:10:49 2023 -0400 : update 05_report        
cd6f020 - Benjamin Lorentz, Tue Apr 4 11:07:13 2023 -0400 : update main.nf
22c4d21 - Benjamin Lorentz, Tue Apr 4 10:54:05 2023 -0400 : update main.nf
6ee3853 - Benjamin Lorentz, Tue Apr 4 10:44:45 2023 -0400 : update main.nf
5c37ccc - Benjamin Lorentz, Tue Apr 4 10:34:54 2023 -0400 : update main.nf
ece17a8 - Benjamin Lorentz, Tue Apr 4 09:55:21 2023 -0400 : update 01 report        
c85baf8 - Benjamin Lorentz, Tue Apr 4 09:44:18 2023 -0400 : update 01_report_MbA.rmd
```
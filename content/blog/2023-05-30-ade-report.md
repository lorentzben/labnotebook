---
title: 'Ade Report'
date: 2023-05-30T13:06:00Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "Mock"
  - "Module"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - compare fastp and prinseq analyses
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
  - Run a proper analysis to send to Ade
    - Create Report
      - NC
      - Mock Quality
      - Why SRS?
  - Longitudinal Analysis By hand
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Ade

#### Generating an Analysis for Ade

cycle 4 rev:  3097ad09135b2099bd7a6f0a9ab065163f0e4946
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23046627

```bash
Waiting files transfer to complete (1 files)
Completed at: 26-May-2023 18:30:34
Duration    : 1h 15m 18s
CPU hours   : 3.9 (0.1% cached)
Succeeded   : 43
Cached      : 1
```

#### Save Contam Features For NC

check the val for VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:FILTERNEGATIVECONTROL (NC)

```R
setwd('/scratch/bjl34716/ade/cycle-4/work/5e/f4a06ad9c20b76d06dbf1a382e6abc')
```

cycle 4 rev: b4dba1fa6a5ce0bd61e9610e20b8e46d0c2d9ae7
visualize rev: dd7174957a59e72c403cb54b7f625fb279f14eb2
slurm job: 23093420

```bash
Command output:
  (empty)

Command error:
  ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
  ✔ ggplot2 3.3.6     ✔ purrr   0.3.4
  ✔ tibble  3.1.7     ✔ dplyr   1.0.9
  ✔ tidyr   1.2.0     ✔ stringr 1.4.0
  ✔ readr   2.1.2     ✔ forcats 0.5.1
  ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
  ✖ dplyr::filter() masks stats::filter()
  ✖ dplyr::lag()    masks stats::lag()
  Error in read.table("nc_name.txt") : no lines available in input
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/61/954b8c0d7ccab710f22bfcb140d55c

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line
```


cycle 4 rev: b4dba1fa6a5ce0bd61e9610e20b8e46d0c2d9ae7
visualize rev: 2eba6d646a82bcdc4362e2a1ac615528d41d262c
slurm job: 23093926

```bash
Completed at: 30-May-2023 12:15:49
Duration    : 1h 1m 11s
CPU hours   : 6.0 (3.6% cached)
Succeeded   : 35
Cached      : 9
```

Who was filtered out?


cycle 4 rev: b4dba1fa6a5ce0bd61e9610e20b8e46d0c2d9ae7
visualize rev: 32b7a5aae8549071fe32ff55fbe5ee25f324537e
slurm job: 23096050

```bash
Waiting files transfer to complete (1 files)
Completed at: 30-May-2023 15:51:31
Duration    : 50m 15s
CPU hours   : 3.0 (7% cached)
Succeeded   : 35
Cached      : 9
```

I am pretty happy with the reports I have generated for the "raw data" based on the fastp results it may be final.


#### Report for Dr. Ade

- update the TODO #TODO save these contams to disk so we can examine them in contam_script.r
- understand how good the mock community analysis is
- Describe the difference between SRS and Longitudinal analysis
Looks like I got most of this updated and uploaded holding off to emailing him till tomorrow

#### Fastp vs Prinseq analysis

FASTP

cycle 4 rev:  369a02f3135fdce9bd6b5c744f52a8758063f59c
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23044970

```bash
Completed at: 26-May-2023 14:22:38
Duration    : 42m 11s
CPU hours   : 2.3 (0.2% cached)
Succeeded   : 43
Cached      : 1
```

NEED TO EXAMINE

#### Ben's Other analysis

What steps did he take?

- 

What steps do I take?

-

#### Longitudinal Analysis

See if it makes a difference in this specific analysis. 

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - compare fastp and prinseq analyses
    - examine slurm 23044970
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
  - Longitudinal Analysis By hand
  - Email Dr. Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Git Commits

#### Lab Notebook

```bash
89089e7 - Benjamin Lorentz, Tue May 30 09:07:49 2023 -0400 : added page for Tuesday
```

#### Visualize Ampliseq

```bash
d8cfbe9 - Benjamin Lorentz, Tue May 30 16:08:08 2023 -0400 : remove row names from contam script
32b7a5a - Benjamin Lorentz, Tue May 30 14:28:06 2023 -0400 : update contam_script
bff5bcd - Benjamin Lorentz, Tue May 30 14:12:14 2023 -0400 : update modules.conf
2eba6d6 - Benjamin Lorentz, Tue May 30 10:45:11 2023 -0400 : update filternegativecontrol
dd71749 - Benjamin Lorentz, Tue May 30 10:17:59 2023 -0400 : update contam scripts
```

#### Cycle 4

```bash
2d7183c - Benjamin Lorentz, Tue May 30 16:54:12 2023 -0400 : add report and update markdown file
```
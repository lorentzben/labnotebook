---
title: 'Test SRS Downstreams'
date: 2023-05-02T14:10:06Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
description: "Description for the page"
---

### Todos for Today

- Class
  - if there are any paper edits
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - test 4 options
  - Taguchi optmization for richness?
  - Make these subworkflows as opposed to one long workflow?
  - Unit tests based on the example data
  - Positive Control Analysis
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
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

#### Testing Downstream Processes

Yes SRS Yes NC

cycle 4 rev: d569474337136d7f226a3fb21dbd238a76e94d34
visualize ampliseq rev: 9f99cb55a5261748f4561e22cec6260df23e2a83
slurm sub: 21920965

```bash
Completed at: 02-May-2023 11:10:25
Duration    : 13m 6s
CPU hours   : 1.2 (71.2% cached)
Succeeded   : 18
Cached      : 11
```

Yes SRS No NC

cycle 4 rev: 4108db0f3bcdd669c89354ff1b3a7dcab96aaeb0
visualize ampliseq rev: 9f99cb55a5261748f4561e22cec6260df23e2a83
slurm sub: 21921444

```bash
No such variable: table_qza

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 129 or see '.nextflow.log' file for more details
```

cycle 4 rev: 4108db0f3bcdd669c89354ff1b3a7dcab96aaeb0
visualize ampliseq rev: ac73067dac20844f06a47eb6dc980d8241a9ddb3
slurm sub: 21921534

```bash
No such variable: tax_qza

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 127 or see '.nextflow.log' file for more details
[ERROR] Terminal initialization failed; falling back to unsupported
java.lang.IllegalStateException: Shutdown in progress
        at java.base/java.lang.ApplicationShutdownHooks.add(ApplicationShutdownHooks.java:66)
        at java.base/java.lang.Runtime.addShutdownHook(Runtime.java:213)
        at jline.internal.ShutdownHooks.addHook(ShutdownHooks.java:79)
        at jline.internal.ShutdownHooks.add(ShutdownHooks.java:43)
        at jline.TerminalSupport.init(TerminalSupport.java:46)
        at jline.UnixTerminal.init(UnixTerminal.java:47)
        at jline.TerminalFactory.create(TerminalFactory.java:101)
```

cycle 4 rev: 4108db0f3bcdd669c89354ff1b3a7dcab96aaeb0
visualize ampliseq rev: fa741193c6b17889ab56a4a4cd0725b9cb573b43
slurm sub: 21921597

```bash
Loading required package: shinycssloaders
Loading required package: shinybusy
Warning message:
In readLines("/scratch/bjl34716/ade/cycle-4/work/3c/0dfd580b5de4d5843d20720332c91c/srs_min_curve_val.txt") :
  incomplete final line found on '/scratch/bjl34716/ade/cycle-4/work/3c/0dfd580b5de4d5843d20720332c91c/srs_min_curve_val.txt'
Error in assign(paste(names(data)[i], sep = ""), fixed_factor) :
  invalid first argument
Calls: SRS -> SRS -> assign
Execution halted`, size: 766 (max: 255)
```

cycle 4 rev: 4108db0f3bcdd669c89354ff1b3a7dcab96aaeb0
visualize ampliseq rev: ad6e481a9cf9ac1f12fae0975ec26418185e4043
slurm sub: 21922203

```bash
```



No SRS Yes NC

No SRS No NC

#### If we don't provide a raredepth:

Does the coremetric and SRS use the same depth? (so same table)
### Unit testing:

Here is the nf-core test data location

https://github.com/nf-core/test-datasets/tree/ampliseq
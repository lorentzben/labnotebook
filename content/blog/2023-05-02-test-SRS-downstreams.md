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

06 was pretty skewed, did we use the rarefied table? can we raise the rare above the NC samples?

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
Completed at: 02-May-2023 12:30:09
Duration    : 25m 8s
CPU hours   : 1.2 (38.8% cached)
Succeeded   : 18
Cached      : 9
```

No SRS Yes NC

cycle 4 rev: 7af860216bfafeebc817f3849107327a59969dc8
visualize ampliseq rev: ad6e481a9cf9ac1f12fae0975ec26418185e4043
slurm sub: 21923461

```bash
Execution cancelled -- Finishing pending tasks before exit
WARN: Input tuple does not match input set cardinality declared by process `TSVTOQZA` -- offending value: /scratch/bjl34716/ade/cycle-4/work/b6/23adcadcf127c97ada31a2a58ffe5e/filtered-table.biom
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/tsvtoqza.nf' at line: 5 or see '.nextflow.log' file for more details
```

cycle 4 rev: 7af860216bfafeebc817f3849107327a59969dc8
visualize ampliseq rev: 30b3dbc06729205c2ae8ac4ac7610eb717a17a05
slurm sub: 21923526

```bash
Completed at: 02-May-2023 14:19:15
Duration    : 9m 7s
CPU hours   : 1.1 (72.3% cached)
Succeeded   : 18
Cached      : 11
```

No SRS No NC

cycle 4 rev: 4bade93ae6e7fd34433396a55027668f621bb42c
visualize ampliseq rev: 30b3dbc06729205c2ae8ac4ac7610eb717a17a05
slurm sub: 21923772

```bash
Completed at: 02-May-2023 14:38:20
Duration    : 12m 8s
CPU hours   : 1.1 (70.9% cached)
Succeeded   : 17
Cached      : 10
```

#### If we don't provide a raredepth:

Does the coremetric and SRS use the same depth? (so same table)

cycle 4 rev: 922859ef770b376e9f140bb153b303decea68e50 
visualize ampliseq rev: 30b3dbc06729205c2ae8ac4ac7610eb717a17a05
slurm sub: 21924104

```bash
Completed at: 02-May-2023 15:03:54
Duration    : 13m 8s
CPU hours   : 1.1 (73.8% cached)
Succeeded   : 17
Cached      : 12
```

Raise raredepth to 49481:

cycle 4 rev: 4857690f36eb38fd4868aef9ccbae4d92886def4
visualize ampliseq rev: 30b3dbc06729205c2ae8ac4ac7610eb717a17a05
slurm sub: 21926371

```bash

  All values in the grouping vector are unique. This method cannot operate on a grouping vector with only unique values (e.g., there are no 'within' distances because each group of objects contains only a single object).

Debug info has been saved to /tmp/qiime2-q2cli-err-7td4pzec.log
Usage: qiime tools export [OPTIONS]

  Exporting extracts (and optionally transforms) data stored inside an
  Artifact or Visualization. Note that Visualizations cannot be transformed
  with --output-format

Options:
  --input-path ARTIFACT/VISUALIZATION
                        Path to file that should be exported        [required]
  --output-path PATH    Path to file or directory where data should be
                        exported to                                 [required]
  --output-format TEXT  Format which the data should be exported as. This
                        option cannot be used with Visualizations
  --help                Show this message and exit.

                    There was a problem with the command:
 (1/1) Invalid value for '--input-path': File 'unweighted-unifrac.qzv' does
  not exist.
cp: cannot stat 'unweighted-unifrac/raw_data.tsv': No such file or directory`, size: 2705 (max: 255)
```

The value is too high, can we just filter the samples based on Metadata?


Filter Mock Process

I found a module that will do what I want.

Not Completed, testing that the filtering and exporting functions work need to update downstream TSVs, using SRS and NC

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: edd2a7f413b2738ca7d225b4f74b00faaacff831
slurm sub: 21929181

```bash
Caused by:
  Not a valid path value type: groovyx.gpars.dataflow.DataflowBroadcast (DataflowBroadcast around DataflowStream[?])


Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`


[e4/d64f2e] Cached process > REFORMATANDQZATAX (1)
[34/603eb3] Cached process > REPORT14CITATIONS (1)
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: c2ffa128b14b4e58f6d0493a096a4a98d1646df6
slurm sub: 21929270

```bash
Error executing process > 'QIIME2_FILTERNC (null)'

Caused by:
  Not a valid path value type: groovyx.gpars.dataflow.DataflowBroadcast (DataflowBroadcast around DataflowStream[?])


Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`
```
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 11b6a2f9a3c568a62f0566cc1c440d4005ce9f6f
slurm sub: 21929312

```bash

Caused by:
  Not a valid path value type: groovyx.gpars.dataflow.DataflowBroadcast (DataflowBroadcast around DataflowStream[?])


Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`


[b6/23adca] Cached process > FILTERNEGATIVECONTROL (1)
```

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: e6e0ad0dd54c440d0b1cf915c67b0073f4edbd49
slurm sub: 21929436

```bash
Process `QIIME2_FILTERMOCK` declares 3 input channels but 1 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 94 or see '.nextflow.log' file for more details
[ERROR] Terminal initialization failed; falling back to unsupported
java.lang.IllegalStateException: Shutdown in progress
```

Filter Control Process


We might want to use [this process](https://github.com/nf-core/ampliseq/blob/master/modules/local/qiime2_export_absolute.nf) after the filtering? or what I've set up before


### Unit testing:

Here is the nf-core test data location

https://github.com/nf-core/test-datasets/tree/ampliseq

### Todos for Tomorrow

- Class
  - if there are any paper edits
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - Filter NC and Mock Samples
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

### Git Commits

#### Lab Notebook

```bash
577cddd - Benjamin Lorentz, Tue May 2 12:06:03 2023 -0400 : notes before lunch
97f72a3 - Benjamin Lorentz, Tue May 2 10:15:36 2023 -0400 : added page for tuesday
```

#### Visualize Ampliseq

```bash
e6e0ad0 - Benjamin Lorentz, Tue May 2 16:56:54 2023 -0400 : Modifying filter module
11b6a2f - Benjamin Lorentz, Tue May 2 16:48:45 2023 -0400 : update main.nf
c2ffa12 - Benjamin Lorentz, Tue May 2 16:44:00 2023 -0400 : update main.nf
edd2a7f - Benjamin Lorentz, Tue May 2 16:33:19 2023 -0400 : added export absolute and logic to filter mock and nc
b1d8431 - Benjamin Lorentz, Tue May 2 15:59:14 2023 -0400 : update main.nf
30b3dbc - Benjamin Lorentz, Tue May 2 14:10:00 2023 -0400 : update main.nf
ad6e481 - Benjamin Lorentz, Tue May 2 11:59:02 2023 -0400 : update main.nf
fa74119 - Benjamin Lorentz, Tue May 2 11:26:48 2023 -0400 : update main.nf
ac73067 - Benjamin Lorentz, Tue May 2 11:23:56 2023 -0400 : update main.nf
```

#### Cycle 4 

```bash
8a2cfca - Benjamin Lorentz, Tue May 2 16:35:43 2023 -0400 : update SRS NC paramfile
4857690 - Benjamin Lorentz, Tue May 2 15:35:58 2023 -0400 : update srs-nc
922859e - Benjamin Lorentz, Tue May 2 14:50:44 2023 -0400 : add srs-nc-no-rarefaction
4bade93 - Benjamin Lorentz, Tue May 2 14:26:21 2023 -0400 : update driver script
7af8602 - lorentzben, Tue May 2 14:04:40 2023 -0400 : Merge branch 'main' of github.com:lorentzben/cycle-4 into main
28907f5 - Benjamin Lorentz, Tue May 2 14:04:52 2023 -0400 : update driver script
bf0ca56 - lorentzben, Tue May 2 11:20:31 2023 -0400 : Merge branch 'main' of github.com:lorentzben/cycle-4 into main
4108db0 - Benjamin Lorentz, Tue May 2 11:19:04 2023 -0400 : update ade-cycle-4-nextflow-litter_srs-driver.sh
7a48c39 - Benjamin Lorentz, Tue May 2 10:55:46 2023 -0400 : added paramfiles for analysis
d569474 - lorentzben, Tue May 2 10:55:04 2023 -0400 : Merge branch 'main' of github.com:lorentzben/cycle-4 into main
7037b15 - Benjamin Lorentz, Tue May 2 10:44:22 2023 -0400 : add srs test dir
```
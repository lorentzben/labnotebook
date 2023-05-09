---
title: 'Check NC MOCK SRS'
date: 2023-05-09T14:01:31Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
  - "Module"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
    - continue down the script into modules
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

#### Check No NC No Mock No SRS

cycle 4 rev: 329ea90526c6f02ce499d55806efe8f7ac83f1ed
visualize ampliseq rev: 55ffde4bf3867d125ff335eb3196f1a851199b31
slurm sub: 22259601

```bash
DataflowStream[DataflowStream[?], groovyx.gpars.dataflow.operator.PoisonPill@3ec7c78b, ?]
DataflowStream[DataflowStream[?], groovyx.gpars.dataflow.operator.PoisonPill@3ec7c78b, ?]
WARN: Theres no process matching config selector: REPORT01BARPLOT

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2tMZos0RQ1Hokc
[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b5/09397e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔




Completed at: 09-May-2023 10:28:17
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 3
```

#### Negative Control Only

cycle 4 rev: a7d00b7cce211cef08077a6c0b16f79597c986ba
visualize ampliseq rev: 55ffde4bf3867d125ff335eb3196f1a851199b31
slurm sub: 22259938

```bash
no normalization with SRS
DataflowStream[?]
DataflowStream[?]
WARN: Theres no process matching config selector: REPORT01BARPLOT

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/Y7RRAUcVcWDXa
[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b5/09397e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[bf/1061a8] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b7/32b316] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[cd/b3106d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[de/eef3d6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[01/62e5e6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔




Completed at: 09-May-2023 10:35:29
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 8
```

Filtered table is empty...
Check the NC process

cycle 4 rev: a7d00b7cce211cef08077a6c0b16f79597c986ba
visualize ampliseq rev: b5ddfc39d74ae8f9ecbff2b5349e8b4f952b96fc
slurm sub: 22260028

```bash
no normalization with SRS
DataflowStream[?]
DataflowStream[?]
WARN: Theres no process matching config selector: REPORT01BARPLOT

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/3EVjnBzk50H9rd
[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b5/09397e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[bf/1061a8] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b7/32b316] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[cd/b3106d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[de/eef3d6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[01/62e5e6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔




Completed at: 09-May-2023 10:42:34
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 8
```

close but we want the NC samples removed...

cycle 4 rev: a7d00b7cce211cef08077a6c0b16f79597c986ba
visualize ampliseq rev: 27c17575edc93c06134b5c92c139fe556f45b02a
slurm sub: 22260195

```bash
no normalization with SRS
DataflowStream[?]
DataflowStream[?]
WARN: Theres no process matching config selector: REPORT01BARPLOT

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5Tzms7FVmP7R4e
[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b5/09397e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[bf/1061a8] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b7/32b316] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[cd/b3106d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[de/eef3d6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[01/62e5e6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔




Completed at: 09-May-2023 10:51:08
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 8
```

LGTM

#### NC and MOCK together

cycle 4 rev: 9c0a294dd0ab8ca16d4cc6abeaa24766adef5a5b
visualize ampliseq rev: bcf1060e27a2ae5c5f2393824b04f5dd38b9a693
slurm sub: 22260344

```bash
no normalization with SRS
DataflowStream[?]
DataflowStream[?]
WARN: Theres no process matching config selector: REPORT01BARPLOT

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/55WMagDmninUPD
[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b5/09397e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[bf/1061a8] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[b7/32b316] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[cd/b3106d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[de/eef3d6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[01/62e5e6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[da/824e15] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[f3/d29f91] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[51/aff40f] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔




Completed at: 09-May-2023 10:56:50
Duration    : 1m 6s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 11
```

I don't think that we need the biom/qza tables, but if we want them in the future we can add them back in.

#### Just Mock

cycle 4 rev: 8f74472f8622fae46e493dffb1b208edde9e914d
visualize ampliseq rev: 895276d1bd8af3056afd85ca5ca7a42299c301ca
slurm sub: 22260463

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4j15uBFjkwLyoP
[0d/4df878] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1
[b5/09397e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1
[11/756cba] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
[-        ] process > VISUALIZE_AMPLISEQ:VISUALIZ... -
no normalization with SRS
DataflowStream[?]
DataflowStream[?]
Execution cancelled -- Finishing pending tasks before exit
WARN: Theres no process matching config selector: REPORT01BARPLOT
Error executing process > 'VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_FILTERMOCK (null)'

Caused by:
  Not a valid path value type: groovyx.gpars.dataflow.stream.DataflowStreamReadAdapter (DataflowStream[?])


Tip: you can replicate the issue by changing to the process work dir and entering the command `bash .command.run`
```

cycle 4 rev: 8f74472f8622fae46e493dffb1b208edde9e914d
visualize ampliseq rev: 142eaede71d107bd29a53fc75ecd3128f0e8cf34
slurm sub: 22261160

```bash
```


\
-resume 

So the problem is that when you use ifEmpty() it wants a default value not another channel.

Can we do:
if !ch_filtered_tsv_table ? 


#### Compare Colsums, Rowsums, and colnames

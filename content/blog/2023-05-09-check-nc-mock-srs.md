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

cycle 4 rev: fb85eee2f47574ecd87e1f4005ef3f69a842eac6
visualize ampliseq rev: 81e508505ec34b37fff2a8a92cdcf25aeb3de8b5
slurm sub: 22267087

```bash
/scratch/bjl34716/ade/cycle-4/work/7e/968c26d3263bd069712eabff2d5e83/raw-feature-table.qza
/scratch/bjl34716/ade/cycle-4/work/9b/d5dd003c092b07f00c203d9e3e6222/raw_table.tsv
WARN: Theres no process matching config selector: REPORT01BARPLOT

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5qMekv0dWrQNdA
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔



Completed at: 09-May-2023 14:07:53
Duration    : 1m 3s
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


cycle 4 rev: cf1f1edf3ae64720e5939db3fd5e79b80190897e
visualize ampliseq rev: 81e508505ec34b37fff2a8a92cdcf25aeb3de8b5
slurm sub: 22267161

```bash
/scratch/bjl34716/ade/cycle-4/work/83/5449915c78a6d2a7e43c6757e15752/NC.qza
/scratch/bjl34716/ade/cycle-4/work/1a/f1dcbe2124d918ec3fb0c8e12f525f/raw_table.tsv
WARN: Theres no process matching config selector: REPORT01BARPLOT

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4t8RMHnxPZO4gv
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9e/16fcd2] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e0/5b29df] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[83/544991] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[d6/76503a] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[1a/f1dcbe] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔



Completed at: 09-May-2023 14:11:34
Duration    : 1m 5s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 8
```

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

cycle 4 rev: a1886376d9cb3e6abe6d809684a64e0a9ef0106c
visualize ampliseq rev: 81e508505ec34b37fff2a8a92cdcf25aeb3de8b5
slurm sub: 22267252

```bash
/scratch/bjl34716/ade/cycle-4/work/e0/98ef7d55ebe85fa2abaf940b4d43e5/MOCK.qza
/scratch/bjl34716/ade/cycle-4/work/52/bb22cf091619a71f184aa3a85e0057/raw_table.tsv
WARN: Theres no process matching config selector: REPORT01BARPLOT

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/daYtDy6WzaqAe
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9e/16fcd2] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e0/5b29df] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[83/544991] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[d6/76503a] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[1a/f1dcbe] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e0/98ef7d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[23/ee35f4] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[52/bb22cf] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔



Completed at: 09-May-2023 14:15:07
Duration    : 1m 4s
CPU hours   : (a few seconds)
Succeeded   : 0
Cached      : 11
```

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

cycle 4 rev: 1c2ab38d1613faf68020427bddbf5f99a6c7ab3f
visualize ampliseq rev: 81e508505ec34b37fff2a8a92cdcf25aeb3de8b5
slurm sub: 22267370

```bash
/scratch/bjl34716/ade/cycle-4/work/3b/928862a9f7a9440904ca0c7f6718b0/MOCK.qza
/scratch/bjl34716/ade/cycle-4/work/8a/b5559e90de59231996a233a4f64618/raw_table.tsv
Completed at: 09-May-2023 14:22:37
Duration    : 3m 3s
CPU hours   : (a few seconds)
Succeeded   : 3
Cached      : 3
```

#### Just SRS

cycle 4 rev: 3dae5e36012e4cd075fe3d2c80474f09fc7386cd
visualize ampliseq rev: 81e508505ec34b37fff2a8a92cdcf25aeb3de8b5
slurm sub: 22267453

```bash
/scratch/bjl34716/ade/cycle-4/work/9b/34751b2293b01372888ff2f580b7a3/normalized-table.tsv
/scratch/bjl34716/ade/cycle-4/work/5a/bd19b4ec529fb5f7bf6fc2b346bba6/feature-table.qza
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/3NNC7v4hvCSvpk
executor >  slurm (3)
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[63/2653a9] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[9b/34751b] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[5a/bd19b4] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
/scratch/bjl34716/ade/cycle-4/work/5a/bd19b4ec529fb5f7bf6fc2b346bba6/feature-table.qza
Completed at: 09-May-2023 14:33:22
Duration    : 7m 4s
CPU hours   : 0.2 (4% cached)
Succeeded   : 3
Cached      : 3
```

#### Negative Control and SRS

cycle 4 rev: cfe50642d1e0c7339c5304369dd184a77c93f30e
visualize ampliseq rev: 81e508505ec34b37fff2a8a92cdcf25aeb3de8b5
slurm sub: 22267625

```bash
/scratch/bjl34716/ade/cycle-4/work/7c/283e99896b76abb762288d1905409c/normalized-table.tsv

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/U4HRZQMLdkzSs
executor >  slurm (3)
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9e/16fcd2] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e0/5b29df] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[83/544991] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[d6/76503a] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[1a/f1dcbe] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[a2/00d910] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[7c/283e99] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[41/dde9d6] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
/scratch/bjl34716/ade/cycle-4/work/41/dde9d6e77be3233c37a3519c08de33/feature-table.qza

Completed at: 09-May-2023 14:43:38
Duration    : 7m 3s
CPU hours   : 0.2 (14.7% cached)
Succeeded   : 3
Cached      : 8
```

#### SRS and Mock

cycle 4 rev: 1eb029ce1e51801ef40ed5e12153dae2057bd692
visualize ampliseq rev: 81e508505ec34b37fff2a8a92cdcf25aeb3de8b5
slurm sub: 22268196

```bash
/scratch/bjl34716/ade/cycle-4/work/de/36da36ea4052ede7da4fa9aae5fa46/normalized-table.tsv

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/3MM2Q26EZa20P2
executor >  slurm (3)
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[3b/928862] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[29/e5fc8c] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[8a/b5559e] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[66/4e9019] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[de/36da36] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[43/a421d2] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
/scratch/bjl34716/ade/cycle-4/work/43/a421d2231338107c13388217d38b40/feature-table.qza

Completed at: 09-May-2023 14:56:01
Duration    : 7m 6s
CPU hours   : 0.2 (10.6% cached)
Succeeded   : 3
Cached      : 6
```

#### NC MOCK and SRS

cycle 4 rev: 08aad11963ccbc54fde2d78ed50551e5b68a18c9
visualize ampliseq rev: 81e508505ec34b37fff2a8a92cdcf25aeb3de8b5
slurm sub: 22269326

```bash
/scratch/bjl34716/ade/cycle-4/work/95/2d6ee00b4db84461e1fdaf56c80879/normalized-table.tsv

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/2I6KurmrXK1or8
executor >  slurm (3)
[1a/aba0ec] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9b/d5dd00] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[7e/968c26] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[9e/16fcd2] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e0/5b29df] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[83/544991] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[d6/76503a] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[1a/f1dcbe] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[e0/98ef7d] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[23/ee35f4] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[52/bb22cf] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1, cached: 1 ✔
[29/a57dd1] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[95/2d6ee0] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
[89/ac4af4] process > VISUALIZE_AMPLISEQ:VISUALIZ... [100%] 1 of 1 ✔
/scratch/bjl34716/ade/cycle-4/work/89/ac4af4704c20f87a4f281b7aad7987/feature-table.qza

Completed at: 09-May-2023 15:09:07
Duration    : 7m 6s
CPU hours   : 0.2 (19.9% cached)
Succeeded   : 3
Cached      : 11
```

#### Compare Colsums, Rowsums, and colnames

No NC No Mock No SRS

```bash
/scratch/bjl34716/ade/cycle-4/work/7e/968c26d3263bd069712eabff2d5e83/raw-feature-table.qza
/scratch/bjl34716/ade/cycle-4/work/9b/d5dd003c092b07f00c203d9e3e6222/raw_table.tsv

library(qiime2R)
library(tidyverse)
> raw_qza <- read_qza("/scratch/bjl34716/ade/cycle-4/work/7e/968c26d3263bd069712eabff2d5e83/raw-feature-table.qza")
> raw_qza <- raw_qza$data
> colSums(raw_qza)
LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109
  49310   66941   49141   49177   42147     111   61204   43832   64887   55267
  LT110   LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119
  45422   57547   65777   95753  101883   60087   16777   45906   52614   41924
  LT120    LT73    LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81
  53815       6   32467   22261   34065   30143   31022   23455   29338   19877
   LT82    LT83    LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91
  25110       4   27082   52045   48475   60500   46449   64058   36320   41303
   LT92    LT93    LT95    LT96    LT97    LT98    LT99 MOCK167 MOCK288 MOCK323
  35994   53447   53211    2915      25   55016   64752      59    2357   49481
 MOCK71   NC168   NC287   NC324    NC72
  10908   40416   39371     208     336
> sum(colSums(raw_qza))
[1] 2151998

> raw_tsv <- read.table('/scratch/bjl34716/ade/cycle-4/work/9b/d5dd003c092b07f00c203d9e3e6222/raw_table.tsv', sep='\t')
> colSums(raw_tsv)
  LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109
  49310   66941   49141   49177   42147     111   61204   43832   64887   55267
  LT110   LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119
  45422   57547   65777   95753  101883   60087   16777   45906   52614   41924
  LT120    LT73    LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81
  53815       6   32467   22261   34065   30143   31022   23455   29338   19877
   LT82    LT83    LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91
  25110       4   27082   52045   48475   60500   46449   64058   36320   41303
   LT92    LT93    LT95    LT96    LT97    LT98    LT99 MOCK167 MOCK288 MOCK323
  35994   53447   53211    2915      25   55016   64752      59    2357   49481
 MOCK71   NC168   NC287   NC324    NC72
  10908   40416   39371     208     336
  
> sum(colSums(raw_tsv))
[1] 2151998
```

NC only

```bash
/scratch/bjl34716/ade/cycle-4/work/83/5449915c78a6d2a7e43c6757e15752/NC.qza
/scratch/bjl34716/ade/cycle-4/work/1a/f1dcbe2124d918ec3fb0c8e12f525f/raw_table.tsv

nc_only_qza <- read_qza("/scratch/bjl34716/ade/cycle-4/work/83/5449915c78a6d2a7e43c6757e15752/NC.qza")
nc_only_qza <- nc_only_qza$data

nc_only_tsv <- read.table('/scratch/bjl34716/ade/cycle-4/work/1a/f1dcbe2124d918ec3fb0c8e12f525f/raw_table.tsv', sep='\t')

> colSums(nc_only_qza)
  LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109
  49310   66941   49141   49177   42147     111   61204   43832   64887   55267
  LT110   LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119
  45422   57547   65777   95753  101883   60087   16777   45906   52614   41924
  LT120    LT73    LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81
  53815       6   32467   22261   34065   30143   31022   23455   29338   19877
   LT82    LT83    LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91
  25110       4   27082   52045   48475   60500   46449   64058   36320   41303
   LT92    LT93    LT95    LT96    LT97    LT98    LT99 MOCK167 MOCK288 MOCK323
  35994   53447   53211    2915      25   55016   64752      59    2357   49481
 MOCK71
  10908
>
> colSums(nc_only_tsv)
  LT100   LT101   LT102   LT103   LT104   LT105   LT106   LT107   LT108   LT109
  49310   66941   49141   49177   42147     111   61204   43832   64887   55267
  LT110   LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119
  45422   57547   65777   95753  101883   60087   16777   45906   52614   41924
  LT120    LT73    LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81
  53815       6   32467   22261   34065   30143   31022   23455   29338   19877
   LT82    LT83    LT84    LT85    LT86    LT87    LT88    LT89    LT90    LT91
  25110       4   27082   52045   48475   60500   46449   64058   36320   41303
   LT92    LT93    LT95    LT96    LT97    LT98    LT99 MOCK167 MOCK288 MOCK323
  35994   53447   53211    2915      25   55016   64752      59    2357   49481
 MOCK71
  10908
  
> sum(colSums(nc_only_qza))
[1] 2071667
>
> sum(colSums(nc_only_tsv))
[1] 2071667
```

NC and Mock 

```bash
/scratch/bjl34716/ade/cycle-4/work/e0/98ef7d55ebe85fa2abaf940b4d43e5/MOCK.qza
/scratch/bjl34716/ade/cycle-4/work/52/bb22cf091619a71f184aa3a85e0057/raw_table.tsv

nc_mock_qza <- read_qza("/scratch/bjl34716/ade/cycle-4/work/e0/98ef7d55ebe85fa2abaf940b4d43e5/MOCK.qza")
nc_mock_qza <- nc_mock_qza$data

nc_mock_tsv <- read.table('/scratch/bjl34716/ade/cycle-4/work/52/bb22cf091619a71f184aa3a85e0057/raw_table.tsv', sep='\t')

> colSums(nc_mock_qza)
 LT100  LT101  LT102  LT103  LT104  LT105  LT106  LT107  LT108  LT109  LT110
 49310  66941  49141  49177  42147    111  61204  43832  64887  55267  45422
 LT111  LT112  LT113  LT114  LT115  LT116  LT117  LT118  LT119  LT120   LT73
 57547  65777  95753 101883  60087  16777  45906  52614  41924  53815      6
  LT74   LT75   LT76   LT77   LT78   LT79   LT80   LT81   LT82   LT83   LT84
 32467  22261  34065  30143  31022  23455  29338  19877  25110      4  27082
  LT85   LT86   LT87   LT88   LT89   LT90   LT91   LT92   LT93   LT95   LT96
 52045  48475  60500  46449  64058  36320  41303  35994  53447  53211   2915
  LT97   LT98   LT99
    25  55016  64752
>
> colSums(nc_mock_tsv)
 LT100  LT101  LT102  LT103  LT104  LT105  LT106  LT107  LT108  LT109  LT110
 49310  66941  49141  49177  42147    111  61204  43832  64887  55267  45422
 LT111  LT112  LT113  LT114  LT115  LT116  LT117  LT118  LT119  LT120   LT73
 57547  65777  95753 101883  60087  16777  45906  52614  41924  53815      6
  LT74   LT75   LT76   LT77   LT78   LT79   LT80   LT81   LT82   LT83   LT84
 32467  22261  34065  30143  31022  23455  29338  19877  25110      4  27082
  LT85   LT86   LT87   LT88   LT89   LT90   LT91   LT92   LT93   LT95   LT96
 52045  48475  60500  46449  64058  36320  41303  35994  53447  53211   2915
  LT97   LT98   LT99
    25  55016  64752
>
> sum(colSums(nc_mock_qza))
[1] 2008862
>
> sum(colSums(nc_mock_tsv))
[1] 2008862
```

Just Mock

```bash
/scratch/bjl34716/ade/cycle-4/work/3b/928862a9f7a9440904ca0c7f6718b0/MOCK.qza
/scratch/bjl34716/ade/cycle-4/work/8a/b5559e90de59231996a233a4f64618/raw_table.tsv

mock_qza <- read_qza("/scratch/bjl34716/ade/cycle-4/work/3b/928862a9f7a9440904ca0c7f6718b0/MOCK.qza")
mock_qza <- mock_qza$data

mock_tsv <- read.table('/scratch/bjl34716/ade/cycle-4/work/8a/b5559e90de59231996a233a4f64618/raw_table.tsv', sep='\t')

colSums(mock_qza)

colSums(mock_tsv)

sum(colSums(mock_qza))

sum(colSums(mock_tsv))

> colSums(mock_qza)
 LT100  LT101  LT102  LT103  LT104  LT105  LT106  LT107  LT108  LT109  LT110
 49310  66941  49141  49177  42147    111  61204  43832  64887  55267  45422
 LT111  LT112  LT113  LT114  LT115  LT116  LT117  LT118  LT119  LT120   LT73
 57547  65777  95753 101883  60087  16777  45906  52614  41924  53815      6
  LT74   LT75   LT76   LT77   LT78   LT79   LT80   LT81   LT82   LT83   LT84
 32467  22261  34065  30143  31022  23455  29338  19877  25110      4  27082
  LT85   LT86   LT87   LT88   LT89   LT90   LT91   LT92   LT93   LT95   LT96
 52045  48475  60500  46449  64058  36320  41303  35994  53447  53211   2915
  LT97   LT98   LT99  NC168  NC287  NC324   NC72
    25  55016  64752  40416  39371    208    336
>
> colSums(mock_tsv)
 LT100  LT101  LT102  LT103  LT104  LT105  LT106  LT107  LT108  LT109  LT110
 49310  66941  49141  49177  42147    111  61204  43832  64887  55267  45422
 LT111  LT112  LT113  LT114  LT115  LT116  LT117  LT118  LT119  LT120   LT73
 57547  65777  95753 101883  60087  16777  45906  52614  41924  53815      6
  LT74   LT75   LT76   LT77   LT78   LT79   LT80   LT81   LT82   LT83   LT84
 32467  22261  34065  30143  31022  23455  29338  19877  25110      4  27082
  LT85   LT86   LT87   LT88   LT89   LT90   LT91   LT92   LT93   LT95   LT96
 52045  48475  60500  46449  64058  36320  41303  35994  53447  53211   2915
  LT97   LT98   LT99  NC168  NC287  NC324   NC72
    25  55016  64752  40416  39371    208    336
>
> sum(colSums(mock_qza))
[1] 2089193
>
> sum(colSums(mock_tsv))
[1] 2089193
```

Just SRS

```bash
/scratch/bjl34716/ade/cycle-4/work/9b/34751b2293b01372888ff2f580b7a3/normalized-table.tsv
/scratch/bjl34716/ade/cycle-4/work/5a/bd19b4ec529fb5f7bf6fc2b346bba6/feature-table.qza

srs_qza <- read_qza("/scratch/bjl34716/ade/cycle-4/work/5a/bd19b4ec529fb5f7bf6fc2b346bba6/feature-table.qza")
srs_qza <- srs_qza$data

srs_tsv <- read.table('/scratch/bjl34716/ade/cycle-4/work/9b/34751b2293b01372888ff2f580b7a3/normalized-table.tsv')

> colSums(srs_qza)
  LT100   LT101   LT102   LT103   LT104   LT106   LT107   LT108   LT109   LT110
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
  LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119   LT120
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82    LT84
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT98    LT99 MOCK323   NC168   NC287
  16500   16500   16500   16500   16500
>
> colSums(srs_tsv)
  LT100   LT101   LT102   LT103   LT104   LT106   LT107   LT108   LT109   LT110
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
  LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119   LT120
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82    LT84
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT98    LT99 MOCK323   NC168   NC287
  16500   16500   16500   16500   16500
>
> sum(colSums(srs_qza))
[1] 742500
>
> sum(colSums(srs_tsv))
[1] 742500
```

NC and SRS

```bash
/scratch/bjl34716/ade/cycle-4/work/7c/283e99896b76abb762288d1905409c/normalized-table.tsv
/scratch/bjl34716/ade/cycle-4/work/41/dde9d6e77be3233c37a3519c08de33/feature-table.qza

nc_srs_qza <- read_qza("/scratch/bjl34716/ade/cycle-4/work/41/dde9d6e77be3233c37a3519c08de33/feature-table.qza")
nc_srs_qza <- nc_srs_qza$data

nc_srs_tsv <- read.table('/scratch/bjl34716/ade/cycle-4/work/7c/283e99896b76abb762288d1905409c/normalized-table.tsv')

> colSums(nc_srs_qza)
  LT100   LT101   LT102   LT103   LT104   LT106   LT107   LT108   LT109   LT110
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
  LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119   LT120
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82    LT84
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT98    LT99 MOCK323
  16500   16500   16500
>
> colSums(nc_srs_tsv)
  LT100   LT101   LT102   LT103   LT104   LT106   LT107   LT108   LT109   LT110
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
  LT111   LT112   LT113   LT114   LT115   LT116   LT117   LT118   LT119   LT120
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT74    LT75    LT76    LT77    LT78    LT79    LT80    LT81    LT82    LT84
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT85    LT86    LT87    LT88    LT89    LT90    LT91    LT92    LT93    LT95
  16500   16500   16500   16500   16500   16500   16500   16500   16500   16500
   LT98    LT99 MOCK323
  16500   16500   16500
>
> sum(colSums(nc_srs_qza))
[1] 709500
>
> sum(colSums(nc_srs_tsv))
[1] 709500
```

SRS and Mock

```bash
/scratch/bjl34716/ade/cycle-4/work/de/36da36ea4052ede7da4fa9aae5fa46/normalized-table.tsv
/scratch/bjl34716/ade/cycle-4/work/43/a421d2231338107c13388217d38b40/feature-table.qza

srs_mock_qza <- read_qza("/scratch/bjl34716/ade/cycle-4/work/43/a421d2231338107c13388217d38b40/feature-table.qza")
srs_mock_qza <- srs_mock_qza$data

srs_mock_tsv <- read.table('/scratch/bjl34716/ade/cycle-4/work/de/36da36ea4052ede7da4fa9aae5fa46/normalized-table.tsv')

> colSums(srs_mock_qza)
LT100 LT101 LT102 LT103 LT104 LT106 LT107 LT108 LT109 LT110 LT111 LT112 LT113
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
LT114 LT115 LT116 LT117 LT118 LT119 LT120  LT74  LT75  LT76  LT77  LT78  LT79
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT80  LT81  LT82  LT84  LT85  LT86  LT87  LT88  LT89  LT90  LT91  LT92  LT93
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT95  LT98  LT99 NC168 NC287
16500 16500 16500 16500 16500
>
> colSums(srs_mock_tsv)
LT100 LT101 LT102 LT103 LT104 LT106 LT107 LT108 LT109 LT110 LT111 LT112 LT113
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
LT114 LT115 LT116 LT117 LT118 LT119 LT120  LT74  LT75  LT76  LT77  LT78  LT79
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT80  LT81  LT82  LT84  LT85  LT86  LT87  LT88  LT89  LT90  LT91  LT92  LT93
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT95  LT98  LT99 NC168 NC287
16500 16500 16500 16500 16500
>
> sum(colSums(srs_mock_qza))
[1] 726000
>
> sum(colSums(srs_mock_tsv))
[1] 726000
```

NC MOCK SRS

```bash
/scratch/bjl34716/ade/cycle-4/work/95/2d6ee00b4db84461e1fdaf56c80879/normalized-table.tsv
/scratch/bjl34716/ade/cycle-4/work/89/ac4af4704c20f87a4f281b7aad7987/feature-table.qza

srs_nc_mock_qza <- read_qza("/scratch/bjl34716/ade/cycle-4/work/89/ac4af4704c20f87a4f281b7aad7987/feature-table.qza")
srs_nc_mock_qza <- srs_nc_mock_qza$data

srs_nc_mock_tsv <- read.table('/scratch/bjl34716/ade/cycle-4/work/95/2d6ee00b4db84461e1fdaf56c80879/normalized-table.tsv')

> colSums(srs_nc_mock_qza)
LT100 LT101 LT102 LT103 LT104 LT106 LT107 LT108 LT109 LT110 LT111 LT112 LT113
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
LT114 LT115 LT116 LT117 LT118 LT119 LT120  LT74  LT75  LT76  LT77  LT78  LT79
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT80  LT81  LT82  LT84  LT85  LT86  LT87  LT88  LT89  LT90  LT91  LT92  LT93
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT95  LT98  LT99
16500 16500 16500
>
> colSums(srs_nc_mock_tsv)
LT100 LT101 LT102 LT103 LT104 LT106 LT107 LT108 LT109 LT110 LT111 LT112 LT113
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
LT114 LT115 LT116 LT117 LT118 LT119 LT120  LT74  LT75  LT76  LT77  LT78  LT79
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT80  LT81  LT82  LT84  LT85  LT86  LT87  LT88  LT89  LT90  LT91  LT92  LT93
16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500 16500
 LT95  LT98  LT99
16500 16500 16500
>
> sum(colSums(srs_nc_mock_qza))
[1] 693000
>
> sum(colSums(srs_nc_mock_tsv))
[1] 693000
```

#### Reformat and QZA tax


cycle 4 rev: 08aad11963ccbc54fde2d78ed50551e5b68a18c9
visualize ampliseq rev: 9a17c864ff639560c979e9e77a69e7f5c744f58a
slurm sub: 22276493

```bash
Completed at: 09-May-2023 17:04:05
Duration    : 1m 5s
CPU hours   : 0.2 (96.8% cached)
Succeeded   : 1
Cached      : 14
```

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish Modularization
    - GENERATEBIOMFORGRAPHLAN
    - COREMETRICPYTHON
    - QIIME2_EXPORT_ABSOLUTE_CORE(COREMETRICPYTHON.out.rare_table)
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

#### Labnotebook

```bash
23e6447 - Benjamin Lorentz, Tue May 9 16:22:18 2023 -0400 : update notes on final tables for the 8 different options
832ee68 - Benjamin Lorentz, Tue May 9 11:59:15 2023 -0400 : notes before lunch
3ad0c39 - Benjamin Lorentz, Tue May 9 10:03:31 2023 -0400 : added tuesdays page
```

#### Visualize Ampliseq

```bash
9a17c86 - Benjamin Lorentz, Tue May 9 17:03:23 2023 -0400 : update reformat and qza tax
dcdf1e5 - Benjamin Lorentz, Tue May 9 17:00:35 2023 -0400 : add reformat and qza tax
81e5085 - Benjamin Lorentz, Tue May 9 14:02:42 2023 -0400 : update visualize-ampliseq
df63231 - Benjamin Lorentz, Tue May 9 11:47:18 2023 -0400 : visualize ampliseq
5790d38 - Benjamin Lorentz, Tue May 9 11:41:25 2023 -0400 : try this
9602b32 - Benjamin Lorentz, Tue May 9 11:38:51 2023 -0400 : update visualize ampliseq
bb93726 - Benjamin Lorentz, Tue May 9 11:31:19 2023 -0400 : try this
0f194f1 - Benjamin Lorentz, Tue May 9 11:28:16 2023 -0400 : update visualize ampliseq
142eaed - Benjamin Lorentz, Tue May 9 11:26:27 2023 -0400 : update visualize-ampliseq
069d972 - Benjamin Lorentz, Tue May 9 11:17:13 2023 -0400 : update visualize-amplseq
93bd0ec - Benjamin Lorentz, Tue May 9 11:13:29 2023 -0400 : update visualize-ampliseq
9dde9f3 - Benjamin Lorentz, Tue May 9 11:10:57 2023 -0400 : update visualize-ampliseq
6d1d51d - Benjamin Lorentz, Tue May 9 11:08:11 2023 -0400 : update visualize-ampliseq
:...skipping...
9a17c86 - Benjamin Lorentz, Tue May 9 17:03:23 2023 -0400 : update reformat and qza tax
dcdf1e5 - Benjamin Lorentz, Tue May 9 17:00:35 2023 -0400 : add reformat and qza tax
81e5085 - Benjamin Lorentz, Tue May 9 14:02:42 2023 -0400 : update visualize-ampliseq
df63231 - Benjamin Lorentz, Tue May 9 11:47:18 2023 -0400 : visualize ampliseq
5790d38 - Benjamin Lorentz, Tue May 9 11:41:25 2023 -0400 : try this
9602b32 - Benjamin Lorentz, Tue May 9 11:38:51 2023 -0400 : update visualize ampliseq
bb93726 - Benjamin Lorentz, Tue May 9 11:31:19 2023 -0400 : try this
0f194f1 - Benjamin Lorentz, Tue May 9 11:28:16 2023 -0400 : update visualize ampliseq
142eaed - Benjamin Lorentz, Tue May 9 11:26:27 2023 -0400 : update visualize-ampliseq
069d972 - Benjamin Lorentz, Tue May 9 11:17:13 2023 -0400 : update visualize-amplseq
93bd0ec - Benjamin Lorentz, Tue May 9 11:13:29 2023 -0400 : update visualize-ampliseq
9dde9f3 - Benjamin Lorentz, Tue May 9 11:10:57 2023 -0400 : update visualize-ampliseq
6d1d51d - Benjamin Lorentz, Tue May 9 11:08:11 2023 -0400 : update visualize-ampliseq
6ac204e - Benjamin Lorentz, Tue May 9 11:05:09 2023 -0400 : update visualize-ampliseq
895276d - Benjamin Lorentz, Tue May 9 11:00:18 2023 -0400 : update modules.conf
bcf1060 - Benjamin Lorentz, Tue May 9 10:56:02 2023 -0400 : update modules.conf
27c1757 - Benjamin Lorentz, Tue May 9 10:50:21 2023 -0400 : update modules.conf
451f782 - Benjamin Lorentz, Tue May 9 10:47:02 2023 -0400 : update modules.conf
b5ddfc3 - Benjamin Lorentz, Tue May 9 10:41:26 2023 -0400 : update modules.conf
```

#### Cycle 4

```bash
08aad11 - Benjamin Lorentz, Tue May 9 15:02:19 2023 -0400 : update driver script
1eb029c - Benjamin Lorentz, Tue May 9 14:49:14 2023 -0400 : update driver script
cfe5064 - Benjamin Lorentz, Tue May 9 14:36:44 2023 -0400 : update driver script
3dae5e3 - Benjamin Lorentz, Tue May 9 14:26:21 2023 -0400 : update driver script
1c2ab38 - Benjamin Lorentz, Tue May 9 14:20:00 2023 -0400 : update driver scipt
a188637 - Benjamin Lorentz, Tue May 9 14:14:36 2023 -0400 : update driver script
cf1f1ed - Benjamin Lorentz, Tue May 9 14:10:04 2023 -0400 : update driver script
fb85eee - Benjamin Lorentz, Tue May 9 14:04:37 2023 -0400 : update driver script
899c796 - Benjamin Lorentz, Tue May 9 11:43:12 2023 -0400 : move back to mock and nc
51cf64b - Benjamin Lorentz, Tue May 9 11:32:41 2023 -0400 : remove resume
8f74472 - Benjamin Lorentz, Tue May 9 11:01:07 2023 -0400 : update driverscript
9c0a294 - Benjamin Lorentz, Tue May 9 10:54:29 2023 -0400 : update driver script
:...skipping...
08aad11 - Benjamin Lorentz, Tue May 9 15:02:19 2023 -0400 : update driver script
1eb029c - Benjamin Lorentz, Tue May 9 14:49:14 2023 -0400 : update driver script
cfe5064 - Benjamin Lorentz, Tue May 9 14:36:44 2023 -0400 : update driver script
3dae5e3 - Benjamin Lorentz, Tue May 9 14:26:21 2023 -0400 : update driver script
1c2ab38 - Benjamin Lorentz, Tue May 9 14:20:00 2023 -0400 : update driver scipt
a188637 - Benjamin Lorentz, Tue May 9 14:14:36 2023 -0400 : update driver script
cf1f1ed - Benjamin Lorentz, Tue May 9 14:10:04 2023 -0400 : update driver script
fb85eee - Benjamin Lorentz, Tue May 9 14:04:37 2023 -0400 : update driver script
899c796 - Benjamin Lorentz, Tue May 9 11:43:12 2023 -0400 : move back to mock and nc
51cf64b - Benjamin Lorentz, Tue May 9 11:32:41 2023 -0400 : remove resume
8f74472 - Benjamin Lorentz, Tue May 9 11:01:07 2023 -0400 : update driverscript
9c0a294 - Benjamin Lorentz, Tue May 9 10:54:29 2023 -0400 : update driver script
a7d00b7 - Benjamin Lorentz, Tue May 9 10:31:39 2023 -0400 : update driver script
329ea90 - Benjamin Lorentz, Tue May 9 10:22:52 2023 -0400 : update ade-cycle-4-nextflow_litter_srs-driver.sh
```
---
title: 'Finish Updating Visualize Ampliseq'
date: 2023-04-06T13:56:00Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Tomorrow

- Class
  - Examine Comments on Word Doc
  - Homework 4
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix report 06b
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
  
### Ade

#### Adding Control back in

Mock and NC are also included, so possibly the issue is that the old unfiltered table is being used?

Work dir: /scratch/bjl34716/ade/cycle-4/work/df/1aa771f65e92c53c4a622755cc332e

I now passed in the core metric table which will correctly rarefy the table based on user submitted params or nf-core/ampliseq (lowest richness sample). This really only applies to PCA and the NMDS plots 

cycle 4 rev: 0ce747f9535ec9d602f2dd2e29e22647af98bd4c
visualize ampliseq rev: 726eacb912d56ae9e8fc4c789a130fb44dfe70be
slurm sub: 20774502

```bash
Completed at: 06-Apr-2023 10:48:19
Duration    : 2m 7s
CPU hours   : 1.2 (97.1% cached)
Succeeded   : 2
Cached      : 27
```

#### Check Normality for 05 and 12

I want to run the normality test and then either automatically or manually produce both parametric and non-parametric results.

cycle 4 rev: e35d6670e818a70ba4e398a48e3713c91b861169
visualize ampliseq rev: 8c912a528a26f8785250a360ab68bd9fc1026cce
slurm sub: 20780581

```bash
 Workflow execution completed unsuccessfully

/scratch/bjl34716/ade/cycle-4/litter-normality/metadata.tsv
```


cycle 4 rev:  7071fe188d375c9b070bbb0728eebb72289aca70
visualize ampliseq rev: 8c912a528a26f8785250a360ab68bd9fc1026cce
slurm sub: 20781690

```bash
  Attaching package: 'rstatix'

  The following object is masked from 'package:stats':

      filter

  Quitting from lines 72-137 (05_report.Rmd)
  Error in asserttat_group_columns_exists(data) :
    data should contain group1 and group2 columns
  Calls: <Anonymous> ... stat_pvalue_manual -> asserttat_group_columns_exists
  In addition: There were 16 warnings (use warnings() to see them)
  Execution halted

```

#### Check metadata reading

This is one example I encountered, it subset 1 sample it shouldn't have 

```r
I don't think this is needed if error examine
metadata <- metadata[2:length(metadata[,1]),]
```

cycle 4 rev:  7071fe188d375c9b070bbb0728eebb72289aca70
visualize ampliseq rev: 699d0cd3e125bbb70b995ef7aad245319fe10aca
slurm sub: 20783096

```bash
Completed at: 06-Apr-2023 14:02:19
Duration    : 38m 6s
CPU hours   : 1.3 (51.9% cached)
Succeeded   : 5
Cached      : 24
```

cycle 4 rev:  7071fe188d375c9b070bbb0728eebb72289aca70
visualize ampliseq rev: 0d83c20b3ae2c236c734cf337e00ec8f2e6d6e41
slurm sub: 20786171

```bash
Completed at: 06-Apr-2023 15:54:05
Duration    : 1m 6s
CPU hours   : 1.3 (99.5% cached)
Succeeded   : 1
Cached      : 28
```

cycle 4 rev:  7071fe188d375c9b070bbb0728eebb72289aca70
visualize ampliseq rev: 3f4f735f7cb4da5dce591336072f88720773d006
slurm sub: 20786606

```bash
Completed at: 06-Apr-2023 16:16:53
Duration    : 1m 5s
CPU hours   : 1.3 (99.4% cached)
Succeeded   : 1
Cached      : 28
```

It looks good to me!


#### Implement FIGARO and Compare results



#### Use Mock Communities to Validate results


#### SRS Normalization

### Class

#### Homework 4 

#### Notes from Paper




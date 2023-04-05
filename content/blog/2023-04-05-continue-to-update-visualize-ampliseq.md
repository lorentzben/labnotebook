---
title: 'Continue to Update Visualize Ampliseq'
date: 2023-04-05T14:21:17Z
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
  - Homework 4
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

### Ade

#### Fix the order ioi method

Currently the method will read in the ordered IOI if provided, but it fails to write it out to file, so I want to go by hand and see what the issue is, and then update the code.

cycle 4 rev: e4cda0d877e7f7a9a1c695be00a3f9d445830311
visualize ampliseq rev: ac114e300c20aa9f02b36c14d21ad1888d3ff090
slurm sub: 20735135

```bash
Completed at: 05-Apr-2023 11:53:54
Duration    : 27m 8s
CPU hours   : 1.2 (36.6% cached)
Succeeded   : 17
Cached      : 9
```

#### Update Report 10 

cycle 4 rev: e4cda0d877e7f7a9a1c695be00a3f9d445830311
visualize ampliseq rev: ea5ff295ae8eeb074ef114e89f7894e570a797a1
slurm sub: 20739422 

```bash
Completed at: 05-Apr-2023 14:02:02
Duration    : 2m 9s
CPU hours   : 1.2 (98% cached)
Succeeded   : 1
Cached      : 25
```

#### Update Report 12

cycle 4 rev: e4cda0d877e7f7a9a1c695be00a3f9d445830311
visualize ampliseq rev: 5978dfe21309eab212788b1799667ba784cb74e4
slurm sub: 20739841

```bash
Completed at: 05-Apr-2023 14:24:55
Duration    : 9m 6s
CPU hours   : 1.2 (87.7% cached)
Succeeded   : 1
Cached      : 25
```

#### 6b NMDS Plots

cycle 4 rev: e4cda0d877e7f7a9a1c695be00a3f9d445830311
visualize ampliseq rev: 2bbb935d54ad13d341fd412c710f9dd70511dcf9
slurm sub: 20740808

```bash
Completed at: 05-Apr-2023 14:56:46
Duration    : 2m 9s
CPU hours   : 1.2 (98.5% cached)
Succeeded   : 1
Cached      : 26
```

Minor updates

cycle 4 rev: e4cda0d877e7f7a9a1c695be00a3f9d445830311
visualize ampliseq rev: 1bddccd018df63ab461008bb6d2850bf6e2e4f7f
slurm sub: 20741225

```bash
Completed at: 05-Apr-2023 15:11:16
Duration    : 2m 7s
CPU hours   : 1.2 (98.7% cached)
Succeeded   : 1
Cached      : 26
```

Updated the rest of the metrics

cycle 4 rev: e4cda0d877e7f7a9a1c695be00a3f9d445830311
visualize ampliseq rev: 0795364fafd27cccb8a698e4a1f222cd016ad474
slurm sub: 20742783

```bash
Completed at: 05-Apr-2023 15:58:17
Duration    : 2m 7s
CPU hours   : 1.2 (97.8% cached)
Succeeded   : 1
Cached      : 26
```

#### Adding Control back in

cycle 4 rev: 0ce747f9535ec9d602f2dd2e29e22647af98bd4c
visualize ampliseq rev: 0795364fafd27cccb8a698e4a1f222cd016ad474
slurm sub: 20743947

```bash
Completed at: 05-Apr-2023 16:51:42
Duration    : 11m 7s
CPU hours   : 1.2 (72.4% cached)
Succeeded   : 11
Cached      : 18
```

Sucess the NMDS look a little wonky still I'd be curious to do [an ordination](https://joey711.github.io/phyloseq/plot_ordination-examples.html#mds_(%E2%80%9Cpcoa%E2%80%9D)_on_unifrac_distances) on the taxa to see if someone is pushing them one way or the other. 

Mock and NC are also included, so possibly the issue is that the old unfiltered table is being used?

Work dir: /scratch/bjl34716/ade/cycle-4/work/df/1aa771f65e92c53c4a622755cc332e

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
  
### Git Commits

#### Lab Notebook

```bash
c05b071 - Benjamin Lorentz, Wed Apr 5 11:57:39 2023 -0400 : updates before lunch
e3418e6 - Benjamin Lorentz, Wed Apr 5 10:23:42 2023 -0400 : added page for wednesday
e12d8a8 - Benjamin Lorentz, Tue Apr 4 17:42:10 2023 -0400 : final notes for tuesday
```

#### Cycle 4

```bash
0ce747f - Benjamin Lorentz, Wed Apr 5 16:36:23 2023 -0400 : update params
```

#### Visualize Ampliseq

```bash
0795364 - Benjamin Lorentz, Wed Apr 5 15:51:51 2023 -0400 : update 06b_report.rmd
1bddccd - Benjamin Lorentz, Wed Apr 5 15:04:43 2023 -0400 : update 06b_report
2bbb935 - Benjamin Lorentz, Wed Apr 5 14:50:41 2023 -0400 : update main.nf add stub 06 report
5978dfe - Benjamin Lorentz, Wed Apr 5 14:04:24 2023 -0400 : update 12 report
ea5ff29 - Benjamin Lorentz, Wed Apr 5 13:56:31 2023 -0400 : update 10_report.rmd
ac114e3 - Benjamin Lorentz, Wed Apr 5 11:22:57 2023 -0400 : update main.nf
```

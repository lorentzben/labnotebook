---
title: 'Alphadiv Figaro'
date: 2023-04-14T15:40:41Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
  - "normalize"
  - "figaro"
  - "SRS"
description: "Description for the page"
---

### Todos for Today

- Class
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Is my pairise permanova the same as the pairwise one
  - Beta diversity measurements
  - Cluster to 97% similarity?
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

#### Check Alpha diversity tests

cycle 4 rev: 973b51163e2e4375a0bf2f233e3a9cd72e0402b4
visualize ampliseq res: 26f48e393a1068f142aabe32fee765ce5effcaf9 
slurm sub: 20973212

```bash

[5a/0ec1ae] process > REPORT05ALPHABOXPLOT (1)       [100%] 1 of 1 ✔

Completed at: 13-Apr-2023 17:14:03
Duration    : 1m 6s
CPU hours   : 1.3 (99.4% cached)
Succeeded   : 1
Cached      : 28

```

It's still kinda messy i want to see if we make it a df first then a kable?

cycle 4 rev: 973b51163e2e4375a0bf2f233e3a9cd72e0402b4
visualize ampliseq res: 93f9ba37ae59f9c9cad1e613355c47be59453d8d
slurm sub: 20999572

```bash
[41/8ade2f] process > REPORT05ALPHABOXPLOT (1)       [100%] 1 of 1 ✔

Completed at: 14-Apr-2023 12:08:55
Duration    : 1m 4s
CPU hours   : 1.3 (99.4% cached)
Succeeded   : 1
Cached      : 28
```

cycle 4 rev: 973b51163e2e4375a0bf2f233e3a9cd72e0402b4
visualize ampliseq res: ea5f207e38a7c83e64f3a9cfefb755265b3a3ce0
slurm sub: 21000820



cycle 4 rev: 973b51163e2e4375a0bf2f233e3a9cd72e0402b4
visualize ampliseq res: aa95a63bdf23842ff8c24ed7a914b361bf916ae0
slurm sub: 21004001

```bash
[c3/1b53e5] process > REPORT05ALPHABOXPLOT (1)       [100%] 1 of 1 ✔

Completed at: 14-Apr-2023 13:48:45
Duration    : 1m 4s
CPU hours   : 1.3 (99.4% cached)
Succeeded   : 1
Cached      : 28
```

This looks good to me!

#### PERMANOVA post-hoc

Does my method follow the same procedure as the R package I found online?

I think it looks the same so we'll keep it. 

#### Beta diversity measurments

Are there any other tests I should consider?

8.1.2 PCoA for ASV-level data with Aitchison distance

Now the same using Aitchison distance. This metric corresponds to Euclidean distances between CLR transformed sample abundance vectors. [source](https://microbiome.github.io/course_2021_radboud/beta-diversity.html)

PERMANOVA analysis [source](https://microbiome.github.io/OMA/beta-diversity.html)

Seems like Ordinations and then permanova are the measurements that make sense.

#### OTUs at 97% 

Provide the option to Cluster taxa into 97% otus
ampliseq does not allow this, we could look into it, but Right now let's just keep it at ASVs

### Merge Figaro Back to Main

Update the Readme for visualize ampliseq

Done

#### SRS vs Rarefy

Take this up next week

#### Positive Control Sample


### Todos for Tomorrow

- Class
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
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

#### Lab notebook

```bash
b5202c5 - Benjamin Lorentz, Fri Apr 14 15:42:25 2023 -0400 : notes from figaro, alpha div and new notes
cfba5f6 - Benjamin Lorentz, Fri Apr 14 12:07:09 2023 -0400 : added notes before lunch
7337748 - Benjamin Lorentz, Fri Apr 14 11:42:16 2023 -0400 : added page for friday
e9ac44b - Benjamin Lorentz, Thu Apr 13 17:05:49 2023 -0400 : final notes for thurs
```

#### Visualize Ampliseq

```bash
aa95a63 - Benjamin Lorentz, Fri Apr 14 13:38:24 2023 -0400 : update 05
ea5f207 - Benjamin Lorentz, Fri Apr 14 12:25:37 2023 -0400 : update 05
93f9ba3 - Benjamin Lorentz, Fri Apr 14 11:57:27 2023 -0400 : update 05
26f48e3 - Benjamin Lorentz, Thu Apr 13 17:01:46 2023 -0400 : update 05
```

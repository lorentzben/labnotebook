---
title: 'Zhang Relative Abundance'
date: 2023-01-25T15:37:37Z
draft: false
meta_img: "images/image.png"
tags:
  - "metagenome assembled genome"
  - "MAGs"
  - "zhang"
  - "relative abundance"
  - nextflow
description: "Description for the page"
---

### Todos for Tomorrow

- gg-catalog
  - Zhang
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Summarize info for meeting with Aggrey

### gg-catalog

#### Zhang

from the Huang Paper


Taxonomic assignments of protein sequences were made on the basis of DIAMOND (v0.8.28.90 diamond blastp --evalue 10 --max-target-seqs 250) alignment against the NCBI-NR database by CARMA3 (carma --classify-blast --type p --database p) [76, 77]. A number of 64,332 genes (0.71%) classified as eukaryota but not fungi were excluded from the non-redundant gene set, and the final chicken gut gene catalog includes 9,037,241 genes.

To calculate of relative gene abundance, the clean reads from each sample were aligned against the gene catalog by BWA-MEM with the criteria of alignment length ≥ 50 bp and identity > 95%. Sequenced-based abundance profiling was performed as previously described [81]. Phylum, genus, species, KO, and OG relative abundances were calculated by summing the abundance of the respective genes belonging to each category per sample, based on the taxonomic assignments, KO and OG annotations, respectively. The relative gene abundance profile was also summarized into KEGG and eggNOG functional profiles for the functional analysis. The gene relative abundance profiles and sequences of integrated gene catalog (IGC) of human gut microbiome [16], and the reference gene catalog of the pig gut metagenome [17], were downloaded and analyzed by the same KEGG and eggNOG functional annotation pipeline in our study.


Input: clean reads

What are clean reads?
  To ensure assembly quality, the raw HiFi sequencing reads were filtered, requiring read lengths over 2 kb and average   read accuracy over 99%. In addition, the remaining reads were mapped to the host chicken genome and feed genomes       (maize and soybean) by Minimap2 (RRID:SCR_018550) v2-2.20 [24] with parameter “-x map-hifi” to remove contaminant      sequences, eliminating approximately 2%, 0.5%, 0.5%, 0.1%, and 0.1% of the reads for the duodenum, jejunum, ileum,     cecum, and colorectum samples, respectively. 
  

| Tissue | Percent Loss |
| --- | --- |
| Duodenum | 2% | 
| Jejunum | 0.5 |
| Ileum | 0.5% |
| Cecum | 0.1% |
| Colorectum | 0.1% |

Test run:

gg-catalog rev: 13a3aa8d8ae7892b8678eb700d1cd3d9c717bb66
gg-catalog-nf rev: d98f4a531f17b1905a4ecfec1508a82a3ee04990
slurm sub: 17883898

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
Project config file is malformed -- Cause: Compile failed for sources FixedSetSources[name='/groovy/script/ScriptEC354DC4DA40B$/groovy/script/ScriptEC354DC4DA40BF3CA2978BD707DC42F2/_nf_config_45174931: 23: Unexpected character: '\'' @ line 23, column 53.   orentzb/microbiome_analyst:1.1'
                                 ^

1 error
```
gg-catalog rev: 13a3aa8d8ae7892b8678eb700d1cd3d9c717bb66
gg-catalog-nf rev: a9ac6237aa894be7d44250f06a52b03395349636
slurm sub: 17884094

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5K1JY4eWtSuEyB
[-        ] process > TEST -

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5K1JY4eWtSuEyB
[-        ] process > TEST -
No such file: /reads
```

gg-catalog rev: fbba41f68cb3b2314bf688bbecc29441c95704dd
gg-catalog-nf rev: a9ac6237aa894be7d44250f06a52b03395349636
slurm sub: 17884413


```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/3qKGL6VkSvBEn0
[-        ] process > TEST -
No such file: /reads
```

gg-catalog rev: fbba41f68cb3b2314bf688bbecc29441c95704dd
gg-catalog-nf rev: a9ac6237aa894be7d44250f06a52b03395349636
slurm sub: 17885245

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4CPaSFgFNS7aa4
executor >  slurm (1)
[f1/fe054e] process > TEST (1) [  0%] 0 of 1 ✔

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4CPaSFgFNS7aa4
executor >  slurm (1)
[f1/fe054e] process > TEST (1) [100%] 1 of 1 ✔
Completed at: 25-Jan-2023 15:03:01
Duration    : 1m 2s
CPU hours   : (a few seconds)
Succeeded   : 1
```

Success :)

#### collect data

gg-catalog rev: 65129682fde2019a1c5b2fa0cd01d6d2a52f6a6a 
gg-catalog-nf rev: a9ac6237aa894be7d44250f06a52b03395349636
slurm sub: 17890397

```bash
```

### Git Commits

#### Lab Notebook

```bash
dc5fc98 - Benjamin Lorentz, Wed Jan 25 15:08:36 2023 -0500 : added updates for nextflow gg-catalog
5faa8bf - Benjamin Lorentz, Wed Jan 25 10:38:57 2023 -0500 : added page for wednesday
```

#### gg-catalog

```bash
6512968 - Benjamin Lorentz, Wed Jan 25 16:07:21 2023 -0500 : add code/00_collect_data.sh
fbba41f - Benjamin Lorentz, Wed Jan 25 14:54:16 2023 -0500 : update test_params.yaml
13a3aa8 - Benjamin Lorentz, Wed Jan 25 14:46:07 2023 -0500 : added 00_zhang_nextflow and params
```

#### gg-catalog-nf

```bash
a9ac623 - Benjamin Lorentz, Wed Jan 25 14:49:22 2023 -0500 : update nextflow.config
d98f4a5 - Benjamin Lorentz, Wed Jan 25 14:22:43 2023 -0500 : update main.nf
3cb78c8 - Benjamin Lorentz, Wed Jan 25 14:14:07 2023 -0500 : add main.nf and others
74c587b - Ben Lorentz, Wed Jan 25 13:51:12 2023 -0500 : Initial commit
```



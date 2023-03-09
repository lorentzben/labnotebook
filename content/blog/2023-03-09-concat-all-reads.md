---
title: 'Concat All Reads'
date: 2023-03-09T13:48:33Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - yes, but Need to confirm with cat samples
    - make cat metadata and mapping
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### gg-catalog-nf

#### slurm job 19758400

Looks like the reads were sucessfully concatenated, now we need to rebuild the metadata and mapping files. 

gg-catalog-nf rev: fcf64d97ac9f17bb6ac1181fb311920e6dd77f0f
gg-catalog rev: 2827deb07ef8321df88f81e49e1e560387ffaa70
slurm sub: 19775463

```bash
```

#### Relative Abundance calc

From the Zhang paper and 01-25-2023:

To calculate of relative gene abundance, the clean reads from each sample were aligned against the gene catalog by BWA-MEM with the criteria of alignment length ≥ 50 bp and identity > 95%. Sequenced-based abundance profiling was performed as previously described [81].

From supps of Qin JJ 2012:

Quantification of metagenome content
Computation of relative gene abundance. The high quality reads from each sample were aligned against the gene catalogue by SOAP2 using the criterion of “identity > 90%”. In our sequence-based profiling analysis, only two types of alignments could be accepted: i). an entire of a paired-end read can be mapped onto a gene with the correct insert-size; ii). one end of the paired-end read can be mapped onto the end of a gene, only if the other end of read was mapped outside the genic region. In both cases, the mapped read was counted as one copy. Then, for any sample 𝑆, we calculated the abundance as follows:

Step 1: Calculation of the copy number of each gene

$ b_i = \frac{x_i}{L_i} $

Step 2: Calculation of the relative abundance of gene i 

$ a_i = \frac{b_i}{\Sigma_j b_j} = \frac{\frac{x_i}{L_i}}{\Sigma_j\frac{x_j}{L_j}} $

$a_i$ : The relative abundance of gene 𝑖 in sample 𝑆.
$L_i$ : The length of gene 𝑖.
$x_i$ : The times which gene 𝑖 can be detected in sample 𝑆 (the number of mapped reads).
$b_i$ : The copy number of gene 𝑖 in the sequenced data from sample 𝑆.


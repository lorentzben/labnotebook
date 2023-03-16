---
title: 'Examine Keggs'
date: 2023-03-16T13:45:29Z
draft: false
meta_img: "images/image.png"
tags:
  - "huang2018"
  - "Kegg"
  - "peptidase"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Reply to Ade
- gg-catalog
  - compare abundances of genes of interest (gene and kegg tables)
  - Generate a gene network 
    - how do you do this?
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7

### gg-catalog

#### subset the genes before merging

When trying to merge the selected KOs with the abundance table, we kept erroring out due to memory. We can make an intermediate table by taking the keggs of interest that are present in the kegg genes and then merge the subsetted table.

Why do the number of gene ids and the number of kegg genes not line up?
If our numbers line up with their kegg numbers then it is not an issue but if they do not then we have an error. 

These are the differences between the Kegg Abundance table and the Kegg info table, 1 makes sense as unknown but the other ones are curious.

```bash
 1 K02750  0.0000759     6.43e-5 2.70e-5 1.36e-5 1.11e-5 1.26e-5 4.97e-5 1.86e-5
 2 K02753  0.0000344     4.99e-5 2.02e-6 3.94e-5 1.02e-5 7.79e-6 1.86e-6 0    
 3 K02788  0.000000532   6.66e-7 0       1.03e-6 3.34e-7 3.54e-7 7.08e-8 1.11e-6
 4 K02810  0.000395      7.01e-4 2.25e-4 2.69e-4 1.92e-4 2.06e-4 2.59e-4 1.25e-4
 5 K02819  0.000240      3.40e-4 1.64e-4 1.55e-4 2.15e-4 1.59e-4 2.12e-4 8.04e-5
 6 K05344  0.0000226     1.38e-6 1.29e-5 2.11e-5 8.65e-6 7.29e-6 1.82e-5 3.41e-6
 7 K06022  0             0       0       5.08e-8 0       0       0       7.42e-7
 8 K10672  0.0000652     4.68e-5 6.00e-5 7.26e-5 6.67e-5 9.98e-5 4.15e-5 1.23e-5
 9 K10826  0.0000144     5.44e-6 8.44e-6 1.32e-5 2.15e-5 1.00e-5 1.60e-5 3.96e-6
10 K11192  0.0000246     3.38e-7 1.91e-6 2.94e-7 0       1.93e-7 1.83e-6 4.32e-7
11 K11199  0.00000519    3.37e-7 1.84e-6 2.92e-6 3.77e-6 7.38e-8 2.52e-5 0    
12 K11200  0.00000519    3.37e-7 1.84e-6 2.92e-6 3.77e-6 7.38e-8 2.52e-5 0    
13 K20108  0.0000281     4.44e-6 3.11e-5 3.14e-5 1.39e-5 1.91e-5 3.37e-5 3.70e-5
14 K20118  0.000202      3.71e-4 1.50e-4 1.69e-4 1.94e-4 1.51e-4 2.31e-4 7.97e-5
15 Unknown 0.410         4.10e-1 3.85e-1 4.10e-1 4.17e-1 4.17e-1 4.12e-1 4.71e-1
```

``` r
> sum(keggs_of_interest$KO %in% missing_kegg$"#KEGG")
0 
```

None of the keggs I'm interesting in are abundant but not accounted for.

genes of interest: 277
Kegg_gene subsetted by genes of interest: 192
their_kegg_abundance intersect genes of interest: 192

number of genes identified to be of interest and present in the kegg table: 83293
number of genes identified from selected and present in kegg table: 83293

I have noticed we can't really link the gene ids to the keggs easily. I think we'll go with their table.

```r
> sum(gene_abundance$"#" %in% genes_of_interest)
[1] 7124
> sum(genes_of_interest %in% gene_abundance$"#")
[1] 7124
> sum(selected$"#gene_id" %in% gene_abundance$"#")
[1] 7124
``` 

not equal to the 83293 we expected.






---
title: 'Diagnosing Parser Errors'
date: 2023-02-13T15:26:51Z
draft: false
meta_img: "images/image.png"
tags:
  - "jackwood blast"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - compare the list passed into the calc_batch_size and what comes out of the create_batches function
  - validate the strain table again
  - rm strain table param
- gg-catalog
  - Zhang
    - follow up on slurm process 18670379 (2/9/23)
    - create a minimap process (either concat or separate)
      - read about what a meta map is and if we can implement it
    - check for read loss (does it match the paper?)
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Jackwood Blast Parser

#### compare the list passed into the calc_batch_size and what comes out of the create_batches

Since the import and get first reads worked great, lets update the calc batch size and create batches to be 2 and then 5 to check for logical issues.

git revision

```bash
$ python3 blast_parser.py -b david/david_10.out -o david/david_db_2_13.csv -n david/david_10_batch_2_res.csv

```

There is an issue where the length of the blast dict is smaller than the length of the accession list so we need to try the case of 5 so it passes 7 out actually not 5.

### gg-catalog-nf


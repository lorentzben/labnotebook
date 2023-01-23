---
title: 'Third Tax Table Examine'
date: 2023-01-23T14:08:21Z
draft: false
meta_img: "images/image.png"
tags:
  - "metagenome assembled genome"
  - "MAGs"
  - "huang"
  - ""
description: "Description for the page"
---

### Todos for Today

- gg-catalog
  - Huang
    - separate out tissue types
    - redo the diversity calcs to see if they are the same
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Summarize info for meeting with Aggrey
- Respond to Dr. Kelly's student (done)

### gg-catalog


### Ben jackwood

150,000 seqs, Blast shows mostly spike proteins in virus but when running python parser, results are only coming from local database, not querying NCBI. 
We talked through a more generalized script and ran one command by hand without a database to try to re-create the issue. 

We noticed that the output file was empty even though every accession was examined (~ 25 min worth). I ran the code by hand and checked the verbose intermediaries and noticed that the api field was provided but if no key then the query reurns an empty list, we updated this to allow no key to be needed.


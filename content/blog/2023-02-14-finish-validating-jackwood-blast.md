---
title: 'Finish Validating Jackwood Blast'
date: 2023-02-14T13:23:31Z
draft: false
meta_img: "images/image.png"
tags:
  - "jackwood blast"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - fix the joining of the percent id and query tables and writing them out
  - fix the tag for 1.2 so that it has the xml parser in it. (no strain data)
  - validate the strain table again
  - rm strain table param
  - clean up code that is no longer needed
    - tag version 2.0 
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

#### fix the percent query and percent identity

I think we want to make a function that takes a dict of list of tuples and turns it into a dataframe and then we can join the dataframes based on taxa AND strain.

I built a function called dict_list_tuples_to_dataframe which will take the dict and return a dataframe and then you can join the tables based on the sci name and strain, then you can join this to counts. 

I am validating this result with the large (S1_CGM_result.out) file and no db > david/s1_2_14_22.csv

The database is missing 21 accessions... but the result files are correct.



#### check code with DB

take the S1 CGM result.out and the database david/david_db_2_14.csv I was able to fix the issue sometimes an accession is missed but on the next run it will get added. The results file remained stable. 

#### remove unnessecary code

I removed the old parse xml as well as some pickel code. 

#### Update tag v 1.0 

I updated tag 1.0 to revision: d64e87d83e1526465e9a98cbf44eb056b8545bab which was the version that fixed the api key issue. 

I updated Ben Jackwood to these updates and I think we are in a good holding point until we get a chance to meet up with Brian. 

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
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

### Git Commits

#### Lab Notebook

```bash
2d922cd - Benjamin Lorentz, Tue Feb 14 08:26:36 2023 -0500 : added page for tuesday
9d20503 - Benjamin Lorentz, Mon Feb 13 16:55:05 2023 -0500 : end of notes for monday
```

#### jackwood blast parser

```bash
91c0725 - Benjamin Lorentz, Tue Feb 14 16:40:46 2023 -0500 : update blast_parser.py
50116e0 - Benjamin Lorentz, Tue Feb 14 15:52:20 2023 -0500 : update blast_parser.py
db74f2e - Benjamin Lorentz, Tue Feb 14 15:32:28 2023 -0500 : update blast_parser.py
e44792f - Benjamin Lorentz, Mon Feb 13 16:50:51 2023 -0500 : update blast_parser.py
```

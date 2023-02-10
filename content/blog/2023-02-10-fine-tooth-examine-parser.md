---
title: 'Fine Tooth Examine Parser'
date: 2023-02-10T15:30:01Z
draft: false
meta_img: "images/image.png"
tags:
  - "jackwood blast"
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - validate the strain table
  - rm strain table param
  - find out where the ~ 100 missing records might be
- gg-catalog
  - Zhang
    - follow up on slurm process 18670379
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
  
### Jackwood Blast

#### Mini Dataset

I made a small resultfile with 10 records:

```bash
# BLASTN 2.12.0+
# Query: f0d51999-8e78-4820-9680-5e4e314709ff runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=4638 ch=186 start_time=2023-01-19T16:16:29Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
f0d51999-8e78-4820-9680-5e4e314709ff,MN615433,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MT270493,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MG191072,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MG191070,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MG191067,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MG191064,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MG191030,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MG191020,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MH648687,viruses,1.26e-125,462,79,93.438
f0d51999-8e78-4820-9680-5e4e314709ff,MK887047,viruses,1.26e-125,462,79,93.438
# BLASTN 2.12.0+
# Query: b7914362-4318-4e70-bcec-aa9f984620bb runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=4663 ch=185 start_time=2023-01-19T16:16:32Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
b7914362-4318-4e70-bcec-aa9f984620bb,GU301925,viruses,0.0,968,90,89.923
b7914362-4318-4e70-bcec-aa9f984620bb,GU437865,viruses,0.0,968,90,89.923
b7914362-4318-4e70-bcec-aa9f984620bb,GU437857,viruses,0.0,968,90,89.923
b7914362-4318-4e70-bcec-aa9f984620bb,MN599049,viruses,0.0,957,90,89.668
b7914362-4318-4e70-bcec-aa9f984620bb,KM660631,viruses,0.0,957,90,89.668
b7914362-4318-4e70-bcec-aa9f984620bb,KM660632,viruses,0.0,957,90,89.668
b7914362-4318-4e70-bcec-aa9f984620bb,KM434260,viruses,0.0,957,90,89.668
b7914362-4318-4e70-bcec-aa9f984620bb,GU437858,viruses,0.0,957,90,89.668
b7914362-4318-4e70-bcec-aa9f984620bb,KM434263,viruses,0.0,952,90,89.541
b7914362-4318-4e70-bcec-aa9f984620bb,KM434262,viruses,0.0,952,90,89.541
# BLASTN 2.12.0+
# Query: b0983c24-c539-4b18-b1ad-3f3761a4fc8c runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=3966 ch=184 start_time=2023-01-19T16:16:33Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,GU393340,viruses,2.72e-45,195,57,93.284
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MN615433,viruses,3.52e-44,191,57,92.593
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MN548287,viruses,3.52e-44,191,57,92.593
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MT270494,viruses,3.52e-44,191,57,92.593
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MT270493,viruses,3.52e-44,191,57,92.593
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MG191072,viruses,3.52e-44,191,57,92.593
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MG191070,viruses,3.52e-44,191,57,92.593
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MG191067,viruses,3.52e-44,191,57,92.593
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MG191064,viruses,3.52e-44,191,57,92.593
b0983c24-c539-4b18-b1ad-3f3761a4fc8c,MG191030,viruses,3.52e-44,191,57,92.593
# BLASTN 2.12.0+
# Query: 7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165 runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=3960 ch=184 start_time=2023-01-19T16:16:32Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,MN696794,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,MG191016,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,MG272488,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,KF696629,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,KF411040,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,KC506155,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,KC197210,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,JQ964064,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,JQ739334,viruses,2.14e-41,182,61,89.404
7cb9ff0a-8fb3-4d8f-b622-7416b4c0b165,JQ739329,viruses,2.14e-41,182,61,89.404
# BLASTN 2.12.0+
# Query: dcad48f3-c5bf-4666-96a8-e7f607035ff8 runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=4655 ch=183 start_time=2023-01-19T16:16:30Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
dcad48f3-c5bf-4666-96a8-e7f607035ff8,GU301925,viruses,0.0,854,90,87.742
dcad48f3-c5bf-4666-96a8-e7f607035ff8,GU437865,viruses,0.0,854,90,87.742
dcad48f3-c5bf-4666-96a8-e7f607035ff8,GU437857,viruses,0.0,854,90,87.742
dcad48f3-c5bf-4666-96a8-e7f607035ff8,MN599049,viruses,0.0,848,90,87.613
dcad48f3-c5bf-4666-96a8-e7f607035ff8,GU437858,viruses,0.0,848,90,87.613
dcad48f3-c5bf-4666-96a8-e7f607035ff8,GU437867,viruses,0.0,846,90,87.516
dcad48f3-c5bf-4666-96a8-e7f607035ff8,GU437868,viruses,0.0,845,89,87.581
dcad48f3-c5bf-4666-96a8-e7f607035ff8,GU437866,viruses,0.0,845,89,87.662
dcad48f3-c5bf-4666-96a8-e7f607035ff8,GU437863,viruses,0.0,845,88,87.827
dcad48f3-c5bf-4666-96a8-e7f607035ff8,KM660631,viruses,0.0,843,90,87.484
# BLASTN 2.12.0+
# Query: 904698bf-8827-4794-a95a-5444081fcbc2 runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=4748 ch=182 start_time=2023-01-19T16:16:34Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
904698bf-8827-4794-a95a-5444081fcbc2,MN696794,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,MG191016,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,MG272488,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,KR265092,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,KJ999795,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,KF696629,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,KF411040,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,KC506155,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,KC197210,viruses,2.08e-31,148,59,86.806
904698bf-8827-4794-a95a-5444081fcbc2,JQ964064,viruses,2.08e-31,148,59,86.806
# BLASTN 2.12.0+
# Query: fbd3813c-8041-4c7f-a179-eea748a4a2a6 runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=4744 ch=182 start_time=2023-01-19T16:16:32Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
fbd3813c-8041-4c7f-a179-eea748a4a2a6,KU727201,viruses,7.73e-56,230,64,93.631
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MN615433,viruses,3.59e-54,224,64,92.994
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MN548287,viruses,3.59e-54,224,64,92.994
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MT270493,viruses,3.59e-54,224,64,92.994
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MG191072,viruses,3.59e-54,224,64,92.994
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MG191070,viruses,3.59e-54,224,64,92.994
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MG191067,viruses,3.59e-54,224,64,92.994
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MG191064,viruses,3.59e-54,224,64,92.994
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MG191030,viruses,3.59e-54,224,64,92.994
fbd3813c-8041-4c7f-a179-eea748a4a2a6,MG191020,viruses,3.59e-54,224,64,92.994
# BLASTN 2.12.0+
# Query: e5a29223-4de4-47cb-b544-db0a402eb1d4 runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=4740 ch=182 start_time=2023-01-19T16:16:31Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
e5a29223-4de4-47cb-b544-db0a402eb1d4,MN599049,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU301925,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU437865,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU437859,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU437870,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU437868,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU437867,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU437866,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU437863,viruses,2.42e-30,145,59,88.618
e5a29223-4de4-47cb-b544-db0a402eb1d4,GU437862,viruses,2.42e-30,145,59,88.618
# BLASTN 2.12.0+
# Query: b269f407-d0db-44f1-a887-62fd9e058bba runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=4732 ch=182 start_time=2023-01-19T16:16:29Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
b269f407-d0db-44f1-a887-62fd9e058bba,MN615433,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MN548287,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MT270493,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MG191072,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MG191070,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MG191067,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MG191064,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MG191030,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MG191020,viruses,1.86e-62,252,68,91.534
b269f407-d0db-44f1-a887-62fd9e058bba,MH648687,viruses,1.86e-62,252,68,91.534
# BLASTN 2.12.0+
# Query: 3087e25e-69fa-428b-b362-6007c99aa47a runid=251d75a119092feee8eaa2178d427a7b3687ddb7 read=4695 ch=176 start_time=2023-01-19T16:16:34Z flow_cell_id=FAS87028 protocol_group_id=S1_CGM_01192023 sample_id=S1_CGM
# Database: nt
# Fields: query acc., subject acc., subject blast names, evalue, bit score, % query coverage per uniq subject, % identity
# 10 hits found
3087e25e-69fa-428b-b362-6007c99aa47a,MN548287,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,MK937833,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,MK937831,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,MK937829,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,MK071267,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,MG913343,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,MG763935,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,KY626045,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,KY588135,viruses,5.49e-165,593,81,92.523
3087e25e-69fa-428b-b362-6007c99aa47a,KT736031,viruses,5.49e-165,593,81,92.523
# BLAST processed 10 queries
```

I am going to first try to send these through twice:
using code revision: 39d84745c21ca880727a010626c321803605c3c3

1. without database

```bash
$ (jackwood_blast) bjl34716@DESKTOP-0NR359U:/mnt/f/jordan/jackwood_blast_parser$ python3 blast_parser.py -v -b david/david_10.out -o david_10_database.csv -n david_10_no_database.csv

record count: 17
accession_count: 7
```

we got three empty files, and the record count is incorrect... 

2. with database 

#### get first records

There was an issue with this parsing. I went through and fixed it and added the code to parse out all of the records as well. I am validating that it correctly creates the accession dicts for the records. 

Right now the all records one is repeating one batch too many so I think there might be a duplicate possibly.

It was a logical error so I fixed it!

The current version does not work but is saved under git revision: b7c41a7ea00f37ca3394c9fd9297864eefb1aea8

Wait, the larger file did not validate correctly, it was because queries with 0 hits exist:
This comment is updated in git ref: 6687be7025384d98a92cea27177b8ff866a0e606

#### batch size and number of batches

Just add in a check to see if the length of accession list is shorter than the divider,
if yes just use the lenght of the accession list. 

Updated ref: 6cfc5a118bb8488148cbc262f2f503febafe2708


1. without DB for big file:

```bash
(jackwood_blast) bjl34716@DESKTOP-0NR359U:/mnt/f/jordan/jackwood_blast_parser$ python3 blast_parser.py -b david/S1_CGM_result.out -o david/david_database_new_2_10.csv -n david/big_no_database.csv 
record count:  152957
accession_count: 887

Length of accessions in database: 799
Number of records in result file: 152870 which is 87 less than the 152957 from above
```


2. with DB for big file.

```bash
(jackwood_blast) bjl34716@DESKTOP-0NR359U:/mnt/f/jordan/jackwood_blast_parser$ python3 blast_parser.py -b david/S1_CGM_result.out -d david/david_database_new_2_10.csv -o david/david_db_2_2_10.csv -n david/big_database.csv        
record count:  152957
accession_count: 887


Length of accessions in database: 800
Number of records in result file: 152870 which is 87 less than the 152957 from above
```

My guess is that the last record is being messed up in the function below:

```python
def create_batches(accesion_list, batch_size, divider):
    batch_list = []
    # subsets long list by the provided divider and returns a list
    for i in range(0, divider):
        first_index = i*batch_size
        second_index = first_index + batch_size
        batch_list.append(accesion_list[first_index:second_index])
    gc.collect()
    return batch_list
```

Follow up on this monday


### gg-catalog-nf

#### Pass in the Concat Fastq as opposed to .mmi

Also for monday

### Todos for Next Week

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

### Git Commits

#### Lab notebook

```bash
d858e08 - Benjamin Lorentz, Fri Feb 10 10:32:23 2023 -0500 : added page for friday
```

#### Jackwood Blast Parser

```bash
6cfc5a1 - Benjamin Lorentz, Fri Feb 10 16:25:25 2023 -0500 : update blast_parser.py
6687be7 - Benjamin Lorentz, Fri Feb 10 16:20:28 2023 -0500 : update blast_parser.py
b7c41a7 - Benjamin Lorentz, Fri Feb 10 15:23:40 2023 -0500 : update blast_parser.py
```

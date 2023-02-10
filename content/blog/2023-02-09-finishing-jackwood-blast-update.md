---
title: 'Finishing Jackwood Blast Update'
date: 2023-02-09T13:20:08Z
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
  - meet with Ben to talk about two points above 2/9/23
  - validate the strain table
  - add strain table param
  - strain more info table?
- gg-catalog
  - Zhang
    - follow up on slurm process 18653067
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

I Tagged yesterday's version as 1.5 since it is an intermediary and in case I really mess up some of the code.

#### Output Format:

Species Strain Count
XXX Unknown 93

How do we get here?

we make a dict of tuples for the species and check then update.

TODO 527: adding results to the final dict 

TODO line 364 see line 527, remove the list funkyness if not needed.

Checking if the result table doesn't need to have the fix name step

```python3

  function update_list_of_strain_tuples (strain, count, strain_count_list list(tuples(strain:count))):
    updated_list_of_tuples = []
    for item in strain_count_list:
      curr_strain = item[0]
      if strain == curr_strain:
        curr_strain[1] = curr_strain[1] + count
        updated_list_of_tuples.append(curr_strain)
      else:
        updated_list_of_tuples.append(curr_strain)
        
    
    return updated_list_of_tuples
    
# TODO where do the strain and count come from?
if current_species in final species:
  final_species[current_species] = update_list_of_strain_tuples(strain, count, final_species.get(current_species))
else:
  final_species[current_species] = [tuple(strain, current_species[strain])]
```

TODO line 164 nest the strain check

TODO 245 same as 164

See if we only need to use the updated on a list of tuples that exists which would be starting with line 164

It currently does what I want it to do but I do need to refine the code a little more

I need to update the second if else tree for the querying

To Validate:
  1. delete half the db check if it still works
  2. ensure count of result = 153844
    a. it does not the value I got was 51230
  3. Check the number of strains coming out matches the accessions going in
  4. where do the 100ish results go?


  

#### Meet with Ben Jackwood

From Ben: 

"I managed to update the code with gitpull. I have run some sequences through the pipeline with the updated database. It seemed to generate new accession numbers as well as pull from the database. However, I am getting generic IBV still. I guess if the sequence doesn't match anything in the IBV list it goes to NCBI for generic?"

I have an updated database right now that links strain to sci name to accession, the current step is re-working the data structures so that the result table has:

Species Strain Count
XXX Unknown 93

Expected GA 13 on RT-PCR Conn 

He mentioned that Brian might be interested in setting up a patent for the process the code performs so that there would be a commission/royalty when the Vets use the code for diagnostics.

I want to find a way to make this happen while also reserving the right for anyone else to utilize the code
#### Validate the Strain Table


### gg-catalog-nf

I want it to rebuild the index and re-run 

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 480361d1c9e2f273bbfbe290d489a985f1a28940
slurm sub: 18670379

```bash
Command error:
  [WARNING][1;31m Indexing parameters (-k, -w or -H) overridden by parameters used in the prebuilt index.[0m
  [WARNING][1;31m For a multi-part index, no @SQ lines will be outputted. Please use --split-prefix.[0m
  [M::main::63.751*0.23] loaded/built the index for 507 target sequence(s)
  [M::mm_mapopt_update::67.003*0.27] mid_occ = 500
  [M::mm_idx_stat] kmer size: 15; skip: 10; is_hpc: 0; #seq: 507
  [M::mm_idx_stat::69.171*0.29] distinct minimizers: 113152470 (39.56% are singletons); average occurrences: 6.599; average spacing: 5.372; total length: 4011685380
  [E::sam_parse1] no SQ lines present in the header
  [W::sam_read1_sam] Parse error at line 1758
  samtools sort: truncated file. Aborting
  [main_samview] fail to read the header from "-".

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/7d/00357575ad21eaf2c570d99e676a00
```

If this doesn't work then we should submit the concat reference fasta as opposed to the mmi. 

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
  
### Git Commits

#### Lab Notebook

```bash
871806d - Benjamin Lorentz, Thu Feb 9 16:48:45 2023 -0500 : notes from development
4fe10b4 - Benjamin Lorentz, Thu Feb 9 10:01:05 2023 -0500 : notes before meeting with ben jackwood
78d195e - Benjamin Lorentz, Thu Feb 9 09:05:53 2023 -0500 : added cheatsheet
8e9ddef - Benjamin Lorentz, Thu Feb 9 08:22:20 2023 -0500 : added page for thursday
c1e2ebc - Benjamin Lorentz, Wed Feb 8 17:22:03 2023 -0500 : notes for the end of wednesday
```

#### Jackwood Blast Parser

```bash
39d8474 - Benjamin Lorentz, Thu Feb 9 16:47:59 2023 -0500 : remove prints
4461303 - Benjamin Lorentz, Thu Feb 9 16:45:23 2023 -0500 : update blast_parser.py
a56302f - Benjamin Lorentz, Thu Feb 9 12:20:51 2023 -0500 : update main.nf
9dc35dd - Benjamin Lorentz, Wed Feb 8 17:17:47 2023 -0500 : update blast_parser.py
```
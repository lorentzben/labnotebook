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
#### Validate the Strain Table


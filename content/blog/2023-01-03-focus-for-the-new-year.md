---
title: 'Focus for the New Year'
date: 2023-01-03T14:34:05Z
draft: false
meta_img: "images/image.png"
tags:
  - "visualize-ampliseq"
  - "rarefaction"
description: "Description for the page"
---

from 2022-12-23

```md

So the python code can take in values and paths no problem, the next step is to add in the steps 
to actually run the process and save the file to disk

We can possibly wrap the qiime call in python code to use the warnings package to ignore the warnings [seen here](https://www.tutorialexample.com/beginner-guide-to-disable-or-ignore-python-warnings-python-tutorial/)

TODO:
  check downstream diversity files.
  04
  05
  06
  07
  09
  10
  12
  
```

### Todos for Next Year:

- Visualize Ampliseq
  - Check if user submitted cutoff?
  - pass cutoff (user or otherwise) into the core-metric
  - ensure all diversity files downstream are from the newly generated core-metric
    - search for results/diversity and change to emit etc.
- Generate a Mock community M&M or other and validate pipelines
- Open Up Space on the Lacie drive
- review gene 8940 Term Paper

### Gene 8940 Term Paper

Most big issues were not capitalizing Wald test, and there were some grammatical issues that Dr. Bergman Highlighted but he seemed pleased overall with the results from this paper. 

### What Will I Achieve This Month?

I want to determine the main actors is the gut segments of a chicken. I will achieve this by reviewing papers cited in other reviews as well as try to generate mock microbial communities to see if that is a feasible method to summarize the big players. I think that also examining the functional capacity of the microbes is also very important.

### What does Sucess Look Like?

- Being able to summarize the major players in the gut 
- Being able to summarize the major functions of the gut

### Visualize Ampliseq

```bash
update main.nf

    NOT QUITE FUNCTIONAL YET

    - imported the minmax script into the process
    - downloaded a dir to test by hand
    - have script flow control implemented
    - need to translate bash to api calls
```

While working inside the docker image by hand I was able to generate the results object which is below:

```python

Results (name = value)
----------------------------------------------------------------------------------------------------------------------
rarefied_table                     = <artifact: FeatureTable[Frequency] uuid: a4d9a96d-413e-4891-b899-d41154485bf6>
faith_pd_vector                    = <artifact: SampleData[AlphaDiversity] uuid: 3ed19678-b4f0-43d3-a2b4-428e713f2ea0>
observed_features_vector           = <artifact: SampleData[AlphaDiversity] uuid: 7e50512b-31b0-4fbb-b2af-1865d517bcb3>
shannon_vector                     = <artifact: SampleData[AlphaDiversity] uuid: cbcebd14-965a-448e-bb68-5d5c91a37737>
evenness_vector                    = <artifact: SampleData[AlphaDiversity] uuid: 2d03a77e-ad8c-4d98-8e5f-cbd3a60030b9>
unweighted_unifrac_distance_matrix = <artifact: DistanceMatrix uuid: 6032a1ba-f89c-4479-91c4-31736ec3cf4c>
weighted_unifrac_distance_matrix   = <artifact: DistanceMatrix uuid: 78eb4a10-1a88-4de3-aeb7-6eab6f129401>
jaccard_distance_matrix            = <artifact: DistanceMatrix uuid: 5cf34e96-0abb-4d18-b248-f5d30734ecc1>
bray_curtis_distance_matrix        = <artifact: DistanceMatrix uuid: 52bb0355-cf70-4b80-be3e-6e832df08ef7>
unweighted_unifrac_pcoa_results    = <artifact: PCoAResults uuid: 167301b5-6aae-4a68-b486-10d883c17da3>
weighted_unifrac_pcoa_results      = <artifact: PCoAResults uuid: 97833460-a946-40ba-9a2b-e27822e205d2>
jaccard_pcoa_results               = <artifact: PCoAResults uuid: 33119fe1-768a-401d-9168-61b6ca547502>
bray_curtis_pcoa_results           = <artifact: PCoAResults uuid: a7e1c94a-73aa-46bb-94ca-11d4239b375d>
unweighted_unifrac_emperor         = <visualization: Visualization uuid: 411951c9-2b0a-47eb-8500-af8cfdfa884a>
weighted_unifrac_emperor           = <visualization: Visualization uuid: a77e58c6-c064-4c93-8d25-d0e2ad68564d>
jaccard_emperor                    = <visualization: Visualization uuid: f14ca731-ca2c-4a85-860b-d290461476c1>
bray_curtis_emperor                = <visualization: Visualization uuid: 3721ce57-c4ce-4134-b4c8-c7ace4f8048e>
```
we are able to select each object as core[0] etc. 

```python
 Artifact.save(core[0],'./rarefied_table_6000')
'./rarefied_table_6000.qza'
```

Next step is to evaluate these processes and to use the correctly rarefied files

TODO:
  check downstream diversity files.
  04
  05
  06
  07
  09
  10
  12
  
### Todos for tomorrow:

- Visualize Ampliseq
  - ensure all diversity files downstream are from the newly generated core-metric
    - search for results/diversity and change to emit etc.
- Generate a Mock community M&M or other and validate pipelines
- Open Up Space on the Lacie drive

### Git Commits

#### Lab Notebook

```bash
f717578 - Benjamin Lorentz, Tue Jan 3 11:45:41 2023 -0500 : updates to visualize ampliseq
6de7afb - Benjamin Lorentz, Tue Jan 3 09:37:30 2023 -0500 : added page for first day back
```

#### Visualize Ampliseq

```bash
5491747 - Benjamin Lorentz, Tue Jan 3 16:03:17 2023 -0500 : update main.nf
cee7003 - Benjamin Lorentz, Tue Jan 3 16:00:20 2023 -0500 : update main.nf
f521876 - Benjamin Lorentz, Tue Jan 3 11:43:52 2023 -0500 : update main.nf
```

---
title: Mock Community Construction
author: Ben Lorentz
date: '2022-12-15'
slug: mock-community-construction
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Visualize Ampliseq 
  - determine the proper richness
    - microbiome helper sop
    - mock community analysis
- Host microbiome interaction
  - finish Borda-Molina
- install Z

### Visualize Ampliseq

#### Rarefaction depth suggestions

Microbiome Helper

    4.3 Exclude low-depth samples
  
    Often certain samples will have quite low depth after these filtering steps, which can be excluded from downstream analyses since they will largely add noise. There is no single cut-off that works best for all datasets, but researchers often use minimum cut-offs within the range of 1000 to 4000 reads. You can also use a cut-off much lower than this if you want to retain all samples except those that failed entirely (e.g. depth < 50 reads). Ideally you would choose this cut-off after visualizing rarefaction curves to determine at what read depth the richness of your samples plateaus and choose a cut-off as close to this plateau as possible while retaining sufficient sample size for your analyses.
    
    [source](https://github.com/LangilleLab/microbiome_helper/wiki/Amplicon-SOP-v2-(qiime2-2022.2)#43-exclude-low-depth-samples)

Qiime2
     
    This isn't QIIME per-say but they did sign [their name](https://www.youtube.com/watch?v=g5BdGP4V5YA&ab_channel=QIIME2) onto it, so I still want to include it.
    

Mothur

    Pete Schloss has a [good video](https://www.youtube.com/watch?v=c7H8jLjTxSE&ab_channel=RiffomonasProject) on this logic. I may want to copy him. 
    Schloss suggests go for breath not for depth if you have to make that choice. Deeper is better for rarer taxa but being able to compare treatments might prevale.
    
    We should implement Schloss' ideas. 


possible option is to "--skip-rarefaction" and then in the begining of visualize ampliseq, to run the logic to rarefy the table, perform diversity analysis and then visualize.

### Generating unfiltered table from Villegas data

Do we need to run cut adapt?

Make mapping and metadata files that match the whole sample dataset

I made a [github issue under ampliseq-benchmark](https://github.com/lorentzben/ampliseq-benchmarking/issues/1) to track the progress of this section.

visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462
ampliseq benchmark rev: e4ca701e2ef305937ac3bba5791db0976ccf74da
slurm: 15908186

```bash
Incompatible parameters: `--FW_primer` and `--RV_primer` are required for cutting the QIIME2 reference database to the amplimplicon sequences. Please specify primers or do not use `--qiime_ref_taxonomy`.
```

I changed to the primer clipped sequences

visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462
ampliseq benchmark rev: bda360b6a75b5fc9670c81d1d6ac47a14a5c873b
slurm:  15908838

```bash
Incompatible parameters: `--FW_primer` and `--RV_primer` are required for cutting the QIIME2 reference database to the amplimplicon sequences. Please specify primers or do not use `--qiime_ref_taxonomy`.
```

I misunderstood what the error message was saying. I want to go back and try to run the raw samples through trim adapt and see if it will go

visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462
ampliseq benchmark rev: e53b3fe7cbaf952f5fd0a425fedc8d50c1a318cd
slurm: 15908841

```bash
WARN: No DADA2 cutoffs were specified (`--trunclenf` & `--trunclenr`), therefore reads will be truncated where median quality drops below 25 (defined by `--trunc_qmin`) but at least a fraction of 0.75 (defined by `--trunc_rmin`) of the reads will be retained.
The chosen cutoffs do not account for required overlap for merging, therefore DADA2 might have poor merging efficiency or even fail.

Incompatible parameters: `--FW_primer` and `--RV_primer` are required for primer trimming. If primer trimming is not needed, use `--skip_cutadapt`.
```

will revert back to primer clipped manifest and add skip trim

visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462
ampliseq benchmark rev: b5d930f458c994fafa64e32c446cd9ff5ce529b6 
slurm: 15908843

```bash

```

TODO tasks:

- run this analysis through ampliseq
- run the schloss analysis by hand
- compare automated value to hand picked
- automate the schloss analysis as the first process of visualize ampliseq and create a report
- run all diversity analysis required for visualize ampliseq before reports

#### Generate mock community

Can we use a mock microbial community tool to identify common species in the gut?


### Host Microbiome Interaction 


### Todos for Tomorrow:

- Visualize Ampliseq
  - create a not-filtered/rarefied dataset
  - run pat scholosses analysis on the non-rarefied data
    - compare my numbers to ampliseqs
  - do we need to run cutadapt?
- Host Microbiome Commuity
  - finish 

### Git Commits

#### Lab Notebook

```bash


```

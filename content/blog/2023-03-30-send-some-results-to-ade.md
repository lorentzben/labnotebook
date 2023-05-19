---
title: 'Send Some Results to Ade'
date: 2023-03-30T12:28:02Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
description: "Description for the page"

---

### Todos for Today

- Class
  - read over Ellie's sections
  - what can I write? 
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Ade

#### Dig up old revisions and run with rarefact so that I can send something while I continue to work

cycle 4 rev: 12bd4f8e59405ce6fcce725f28510eee946b82b9
visualize-amplseq rev: df62a69b9f614cd51ec08cd3fde4899e01d40668
slurm sub: 20072884

```bash
Completed at: 23-Mar-2023 14:06:33
Duration    : 2m 5s
CPU hours   : 1.6 (97.9% cached)
Succeeded   : 4
Cached      : 22
```

The previous visualize ampliseq rev was  6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77


cycle 4 rev: 078b239b1945f8f7c61fb602bb3b06654927209b
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20450743

```bash
Error executing process > 'NFCORE_AMPLISEQ:AMPLISEQ:MULTIQC'

Caused by:
  /work/sealab/bjl34716/ade/cycle-4/litter/multiqc: Disk quota exceeded



WARN: Failed to render execution report -- see the log file for details
WARN: Failed to render execution report -- see the log file for details
WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value:
````

cycle 4 rev: 078b239b1945f8f7c61fb602bb3b06654927209b
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20452442

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
lorentzben/visualize-ampliseq contains uncommitted changes -- cannot pull from repository
(END)
```

cycle 4 rev: 078b239b1945f8f7c61fb602bb3b06654927209b
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20452496

```bash
Completed at: 30-Mar-2023 12:10:01
Duration    : 49m 6s
CPU hours   : 1.5 (15.2% cached)
Succeeded   : 19
Cached      : 7
```

The mock and NC samples were skewing the ordination plots, so I want a run without those two to possibly be able to send to Dr. Ade here is the setup:

cycle 4 rev: 6ef9f97086eea2153fe588763ec95eb526fb4d10
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20456178

```bash
!! Only displaying parameters that differ from the pipeline defaults !!
------------------------------------------------------
If you use nf-core/ampliseq for your analysis please cite:

* The pipeline publication
  https://doi.org/10.3389/fmicb.2020.550420

* The pipeline
  https://doi.org/10.5281/zenodo.1493841

* The nf-core framework
  https://doi.org/10.1038/s41587-020-0439-x

* Software dependencies
  https://github.com/nf-core/ampliseq/blob/master/CITATIONS.md
------------------------------------------------------
No such file: /home/bjl34716/ade/cycle-4/litter/cycle_4_litter_metadata_rm_mock_nc.tsv

 -- Check script '/home/bjl34716/.nextflow/assets/nf-core/ampliseq/./workflows/ampliseq.nf' at line: 15 or see '.nextflow.log' file for more details
cp: cannot stat ‘/home/bjl34716/ade/cycle-4/litter-rm-mock-nc/cycle_4_litter_metadata_rm_mock_nc.tsv’: No such file or directory
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
lorentzben/visualize-ampliseq contains uncommitted changes -- cannot pull from repository
```
 
 
cycle 4 rev: 93bb5dccf8e76cbaa04cceee6851755393ab08f3
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20456195

```bash
/scratch/bjl34716/ade/cycle-4/litter-rm-mock-nc/metadata.tsv not found
```

cycle 4 rev: b8c6d97e0b6b49a3a95d272c64e18e35eeb297ff
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20457339

```bash
Sucess
```

We should update the params to match most of what Ben did:

"Raw sequence reads obtained from the Illumina Miseq were processed in R using the DADA2 package (version 1.14) (Callahan et al., 2016). Only reads with a maximum number of expected errors lower than or equal to 2 were retained. In addition, reads were truncated where the phred quality score dropped below 30. Chimeras were identified and removed using the consensus method and the remaining reads were annotated to the SILVA database release 138 with a minimum bootstrap threshold of 50 (Quast et al., 2013). Additionally, full-length 16S rRNA gene sequences generated on the Pacbio Sequel II were processed in the SMRT Link software package version 8.0. The circular consensus reads (ccs) were determined with a minimum predicted accuracy of 0.99 and the minimum number of passes set to 3. After demultiplexing, the ccs were further processed with DADA2 (version 1.14) to obtain high quality amplicons with single-nucleotide resolution as previously described (Callahan et al., 2019). Same as the Illumina reads, the full-length 16S rRNA gene sequences were annotated to the SILVA database 138. Hereafter, the annotated Pacbio reads were used to create a custom formatted database that was utilized as a reference for the Illumina reads that were generated from the same samples. Iterating the species taxonomy assignment of the Illumina reads to the custom database and adding this information to the taxonomy table improved species classification rate by 35%. Amplicon sequence variants (ASVs) with less than 5 sequences in total were removed from the dataset before decontamination. Contaminant sequences were identified from extracted negative controls with the R package decontam and the probability threshold set to 0.5. After contaminant removal, samples with less than 1,000 sequences were removed. The average sequence depth per sample was 23,088.38, ranging from 1,769 to 93,023 sequences." [source](https://www.frontiersin.org/articles/10.3389/fphys.2023.1083192/full)

I followed everything (minus the decontamination):

cycle 4 rev: bb9b63b9d0f1dbc4829c6223e795c7b6b48ecaef 
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm sub: 20459781 

```bash
Completed at: 30-Mar-2023 20:12:21
Duration    : 26m 7s
CPU hours   : 0.8 (1.1% cached)
Succeeded   : 25
Cached      : 1
```

It's still a little bit messy... we'll see what we can do.


#### Clean Up Work Dir

13847 directories, 87758 files

I am pulling all previous analyses out of the work dir and moving to the lacie drive.




#### Update downstream table qzas

### Update The rarefaction report Rmd file to use the QIIME Tables

### Class

#### Read Ellies writing

I read over her notes and a lot make sense, but I have a couple notes I've added and I want to reconnect and see how we're doing. 

#### What Can I do?

I can help with the methods and results/discussion and maybe the conclusion.

### Todos for Tomorrow

- Class
  - Meet and discuss
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Git Commit

#### Lab notebook

```bash
b1b1532 - Benjamin Lorentz, Thu Mar 30 11:41:42 2023 -0400 : updates for before lunch
8526d6b - Benjamin Lorentz, Thu Mar 30 08:32:37 2023 -0400 : added page for Thursday
5c6cdb2 - Benjamin Lorentz, Wed Mar 29 17:12:35 2023 -0400 : final notes for wednesday
```

#### Cycle 4

```bash
93bb5dc - Benjamin Lorentz, Thu Mar 30 13:59:35 2023 -0400 : update metadata filenames
6ef9f97 - Benjamin Lorentz, Thu Mar 30 13:55:32 2023 -0400 : add new metadata, mapping and yaml files
078b239 - Benjamin Lorentz, Thu Mar 30 09:32:29 2023 -0400 : add ade-cycle-4...sh script and update params
```

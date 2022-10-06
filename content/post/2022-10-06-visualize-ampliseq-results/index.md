---
title: Visualize Ampliseq Results
author: ''
date: '2022-10-06'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Tasks for today:

   - See what the report for ALDEx2 looks like
   - Continue working on the pipeline to generate visualizations after ampliseq

So far I have a [cloned nf-core pipeline](https://github.com/lorentzben/ampliseqvis/commit/69d6bf34c3fe649ac54dddd723149481062633ba). I'm not sure that I love the format that they have everything (hence removing a bunch of files), but I think that it is mostly set up to turn their processes (fastqc and multiqc) into report generation like I did for automate 16nf. See below. 

```bash
process Report01 {
    publishDir "${params.outdir}/reports", mode: 'move'

    container "docker://lorentzb/r_01:2.0"

    input:
    file "01_report.Rmd" from ch_01_report_file
    file "item_of_interest.csv" from ch_ioi_r01_csv
    file "order_item_of_interest.csv" from ch_oioi_r01_csv
    file "core-metric-results/*" from ch_rare_table_r01 
    file "rooted-tree.qza" from ch_rooted_tree_r01  
    file "taxonomy.qza" from ch_taxonomy_r01  
    file "metadata.tsv" from ch_metadata_r01

    output:
    path "01_report_*" into ch_01_reports
    path "Figures/*" into ch_01_figures

    label 'process_medium'
    script:
    '''
    #! /usr/bin/env bash

    #Input: item_of_interest.csv order_item_of_interest.csv qiime/* metadata.tsv
    #Output: ../Figures/* 01_report_$dt.html 01_report_$dt.pdf

    echo "I am Here:"
    pwd
    ls
    
    dt=$(date '+%d-%m-%Y_%H.%M.%S');

    Rscript -e "rmarkdown::render('01_report.Rmd', output_file='$PWD/01_report_$dt.html', output_format='html_document', clean=TRUE, knit_root_dir='$PWD')"

    Rscript -e "rmarkdown::render('01_report.Rmd', output_file='$PWD/01_report_$dt.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='$PWD')"
    '''
}
```

It seems like the nf-core template is in DSL1 and part of the development idea was to learn DSL2 so I may spend 1 chunk trying to see if they have a DSL2 template. If not then DSL1 is good for me.

Found and watched [this tutorial](https://nf-co.re/developers/developer_tutorials) for DSL2 pipeline structure. 


### Introduction to Bioinformatics workflows with Nextflow and nf-core


I am going to see about following [this tutorial](https://carpentries-incubator.github.io/workflows-nextflow/01-getting-started-with-nextflow/index.html) to see if it can help me build a DSL2 pipeline from scratch. 

From this tutorial there is a really neat way to do paired reads:

```groovy
$ read_pair_ch = Channel.fromFilePairs('data/yeast/reads/*_{1,2}.fq.gz')
$ read_pair_ch.view()

[etoh60_3, [data/yeast/reads/etoh60_3_1.fq.gz, data/yeast/reads/etoh60_3_2.fq.gz]]
[temp33_1, [data/yeast/reads/temp33_1_1.fq.gz, data/yeast/reads/temp33_1_2.fq.gz]]
[ref1, [data/yeast/reads/ref1_1.fq.gz, data/yeast/reads/ref1_2.fq.gz]]
[ref2, [data/yeast/reads/ref2_1.fq.gz, data/yeast/reads/ref2_2.fq.gz]]
```

You can also pull reads from [SRA](https://carpentries-incubator.github.io/workflows-nextflow/04-channels/index.html#the-fromsra-channel-factory)

We had to build the conda env from rnaseq_pipeline and under a different name nf-training which is not perfect, but it worked well enough to run scripts from the local root dir. 

I can see the power of DSL2 and that's a little frustrating but I think the structure of building up chunk at a time makes more sense than the way I learned DSL1. 

If you pass multiple values through, you must change val input to each input.

I see the appeal of the modularity of DSL2 now. For example, I could add in the processes for the lefse report generation, but not call them in the workflow until the lefse result files are generated. This has great implications.

**TODO**

Include a test profile

A test profile is a configuration profile that specifies a short running test data set to check the functionality of the whole pipeline. It can also demonstrate to users of your workflow the kinds of inputs and outputs to expect. Another benefit is the possibility of automated testing of your workflow, ensuring the workflow keeps working as you add new functionality.

```bash
profiles {
    test {
        params {
           reads = 'https://github.com/my_repo/test/test_reads.fastq.gz'
           reference = 'https://github.com/my_repo/test/test_reference.fasta.gz'
        }
    }
}
```

I've completed the tutorial! I have a bunch of really great ideas now to implement. I think I will rebase the ampliviseq since the template is a little too intense.

I've set up a skeleton nextflow script and dev branch that I think I can run locally as well as on the server. I will attempt to do my development locally to see how that workflow goes. Maybe it's worth trying to use conda in the future but for now I will keep my docker images to avoid large slowdowns with bioconda etc. We are in a good spot for a heavy development Friday if we desire. 

## Tasks for tomorrow

- add at least 1 report chunk to the nextflow pipeline
- read over the homework to see how large it is. 

### ALDEx2 Analysis

Job: 14502765 failed due to OOM error @ 64gbs

I updated the slurm script to request 128gbs and resubmitted.
Job: 14560917
Commit: [65028601d11f820f266cc5cd3a13c846fc1225f4](https://github.com/lorentzben/picrust2_shailes/commit/65028601d11f820f266cc5cd3a13c846fc1225f4)


### Code Commits

#### Lab Notebook

```bash
6c2c036 - Benjamin Lorentz, Thu Oct 6 12:05:28 2022 -0400 : added note about shailes rendering
7aa9726 - Benjamin Lorentz, Thu Oct 6 11:53:44 2022 -0400 : add one more note about val and what to start after lunch:
bc331cf - Benjamin Lorentz, Thu Oct 6 11:46:16 2022 -0400 : Updates for today before lunch
cf48db5 - Benjamin Lorentz, Thu Oct 6 08:43:56 2022 -0400 : make tasks for today bullet points as opposed to indented
aa38ad6 - Benjamin Lorentz, Thu Oct 6 08:41:07 2022 -0400 : Added Thursday 10/6 Post
```

#### Picrust2_shailes

```bash
6502860 - Benjamin Lorentz, Thu Oct 6 11:58:22 2022 -0400 : add email and greater memory
```

#### visualize-ampliseq

```bash
06f7f3a - Benjamin Lorentz, Thu Oct 6 17:09:22 2022 -0400 : had to quote out my string
716cb96 - Benjamin Lorentz, Thu Oct 6 17:08:31 2022 -0400 : change analysis to input
ffee63a - Benjamin Lorentz, Thu Oct 6 17:06:25 2022 -0400 : change to python
e55da76 - Benjamin Lorentz, Thu Oct 6 17:02:28 2022 -0400 : Skeleton Commit
9ccedef - Benjamin Lorentz, Thu Oct 6 16:37:28 2022 -0400 : update readme
9b54027 - Ben Lorentz, Thu Oct 6 16:35:02 2022 -0400 : Initial commit
```





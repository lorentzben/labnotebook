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

We will pick up on processes part 2. 

---
title: Continue diagnosing chunk 10, and Makefile to render rmarkdown docs
author: Ben Lorentz
date: '2022-12-09'
slug: continue-diagnosing-chunk-10-and-makefile-to-render-rmarkdown-docs
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Visualize Ampliseq 
  - try to use a makefile for 3,4 
  - check diverity for boxplot visualization
  - modify uncompress diversity
  - add a new process for boxplot
- Host microbiome interaction
  - new paper
  
### Visualize Ampliseq

#### Use A Makefile to render rmarkdowns for 3,4 

working in dir /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/70/0256cb365cccd694fcd412be7f3f9b



```make
#########################################################
## Makefile to execute systemPipeR and generate Report ##
#########################################################
## Usage:
## (1) Change value assigned to 'MAIN" to base name of your *.Rmd (or *.Rnw) source file 
## (2) To run workflow, execute from command-line 
##		$ make # or make all
## (3) To clean up directory, execute from command-line 
## 		$ make clean

## Define suffixes used for file interconversions
# .SUFFIXES: .tex .pdf .Rnw .R
.SUFFIXES: .Rmd .html .md .R

MAIN = 04_report

#######################################
## Build PDF report with knitr/Latex ##
#######################################
# all: $(MAIN).pdf 
all: $(MAIN).html 

# .Rnw.pdf:
# 	R CMD Sweave --engine=knitr::knitr --pdf $<
.Rmd.html:
	Rscript -e "rmarkdown::render('$<')"

########################################
## Build PDF report with Sweave/Latex ##
########################################
# all: $(MAIN).tex $(MAIN).R $(MAIN).pdf 
# 
# .Rnw.R:
# 	R CMD Stangle $<
# 
# .Rnw.tex:
# 	R CMD Sweave $<
# 
# .tex.pdf:
# 	pdflatex $<
# 	bibtex $*
# 	pdflatex $<
# 	pdflatex $<
 
########################
## Clean-up directory ##
########################
clean:
	rm -fv $(MAIN).aux $(MAIN).log $(MAIN).bbl $(MAIN).blg $(MAIN).out $(MAIN).toc $(MAIN).tex
	rm -fv $(MAIN)-*.pdf $(MAIN)-*.png $(MAIN)-*.jpg
	rm -fv *~ 
```

update process 4 with stageInMode = 'copy'

visualize ampliseq rev: 5985fac1a0e10cf1af9cf1979fd3329d86dd176a
benchmark ampliseq rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15760137

```bash
Command exit status:
  1

Command output:
  (empty)

Command wrapper:
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/0f/dc4359c5dbc4625480d5914a323d22/results’
  cp: cannot stat ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/87/0672cdb4d9a3c2150e04a3fb4a6f3c/ordered_item_of_interest.csv’: No such file or directory
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/87/92900d82a6b894fd92e16daad2f840/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/9f/fc77bf8e908c8708a100c2866ae6ea/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/6f/2540bb2f84f3ab0728b3ebc23a83d8/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/03/c057b0edd7e58f14071679e72dcb9b/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/7e/7497a6270a5125f952c56868f07f36/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/38/417fc192e3bf5bf08f9fc99f05ae06/results’
  cp: cannot stat ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/e7/d26ecfd9ae465db10443408fc39395/ordered_item_of_interest.csv’: No such file or directory
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/30/b217050e07f604ddd73970950bcc07/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/67/8ea683f5d397b1acac8ab443157371/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/67/1f29db776983ed2fdab816cd994efc/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/25/a13e0399ad1764ea5ae01532e853df/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/02/953916e5254d3ecb3007c532890c9f/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/62/b3cc53392044044f7a127849718e7c/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/98/6c8957e70b4512d4fee0fbd088b085/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/39/2e56850fdev/ampliseq-benchmark/medium_richness/work/54/6e6958c07512676469f73319477244/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/2a/8ff1f23326395f43c641725f177702/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/42/a14793b2e289594a69454733a4592f/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/ec/eaa6736542975250010eee350e7386/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/b6/becce651e0b784e86b79dcc3acc241/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/09/5b6e032d385f1b142806f4a30008bb/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/4a/417e3258b5eacbbc9210ae659ed858/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/51/8eef34ff94af5a1e066d06746f3c16/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/ac/b7ac8d675b93c6f1819c120f79d851/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/2c/14f510061214548aca85de3ca10f10/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/73/8042b2796a0ca56688b9d3cd408916/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/83/3acd1b3e1e2d4efcc117a2708677dc/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/01/996e00bc2accf660ab951b00f92cf2/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/0f/dc4359c5dbc4625480d5914a323d22/results’
  cp: cannot stat ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/87/0672cdb4d9a3c2150e04a3fb4a6f3c/ordered_item_of_interest.csv’: No such file or directory
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/87/92900d82a6b894fd92e16daad2f840/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/9f/fc77bf8e908c8708a100c2866ae6ea/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/6f/2540bb2f84f3ab0728b3ebc23a83d8/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/03/c057b0edd7e58f14071679e72dcb9b/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/7e/7497a6270a5125f952c56868f07f36/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/38/417fc192e3bf5bf08f9fc99f05ae06/results’
  cp: cannot stat ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/e7/d26ecfd9ae465db10443408fc39395/ordered_item_of_interest.csv’: No such file or directory
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/30/b217050e07f604ddd73970950bcc07/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/67/8ea683f5d397b1acac8ab443157371/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/67/1f29db776983ed2fdab816cd994efc/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/25/a13e0399ad1764ea5ae01532e853df/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/02/953916e5254d3ecb3007c532890c9f/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/62/b3cc53392044044f7a127849718e7c/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/98/6c8957e70b4512d4fee0fbd088b085/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/39/2e56850fe71254bc8a8a33e8cb6f72/results’
  cp: cannot stat ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/19/fa7753e071f1e61877a194eccbdf95/ordered_item_of_interest.csv’: No such file or directory
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/2d/7b2a4fc8d4e2789254d6f28ce1c8a9/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/27/e6db11d21b2069137d11fb0b883134/results’
  cp: cannot copy cyclic symbolic link ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness/work/bf/bce3fdeaf2e89d05c1b0a4d4418a59/results’

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/81/b69ba9837aee6e61d8549384f7a952
```

lets try hard link

visualize ampliseq rev: c452a90f5e99cad92c85a35825df1fecd2720be1
benchmark ampliseq rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15760495

```bash
Command exit status:
  1

Command output:
  (empty)

Command wrapper:
  ln: ‘/scratch/bjl34716/nf_dev/ampliseq-benchmark/medium_richness’: hard link not allowed for directory

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/d2/74315d5e9d3e88134ac93e09646b63
```

going to try to copy with the L flag

cp -L base_v001.txt /targetdir

visualize ampliseq rev: c04586a17afda88c78936221a639f365eee5aa8b
benchmark ampliseq rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15762292

```bash
Command exit status:
  2

Command output:
  (empty)

Command error:
  .command.sh: line 5: syntax error near unexpected token `2'
  .command.sh: line 5: `Rscript -e "rmarkdown::render('03_report.Rmd', output_file='$PWD/03_report_$dt.html', output_format='html_document', clean=TRUE, knit_root_dir='$PWD')" > 03_html.txt > 2>&1'

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/86/b1078f6d5d6c89ac806f541c65cbb8
```

we need to examine /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/ff/14c202c39ef633b0d9ac88d3990c38 to see if the rmd file was copied or not. 



04 is in: /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/2c/a90dcddd277e4100a2db473228bcaa

visualize ampliseq rev: df7e5ac7392aeaeacdd554c5e5b0525b5636c859
benchmark ampliseq rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15765552

```bash
/scratch/bjl34716/nf_dev/ampliseq-benchmark/work/96/21967ede31b5897a0925f2c0f94a27/.command.sh: line 5: PWD: command not found
cp: cannot create regular file '/04_report_test.Rmd': Read-only file system
Error in abs_path(input) : The file '04_report_test.Rmd' does not exist.
Calls: <Anonymous> -> setwd -> dirname -> abs_path
In addition: Warning message:
In normalizePath(path, winslash = winslash, mustWork = mustWork) :
  path[1]="04_report_test.Rmd": No such file or directory
Execution halted
Error in abs_path(input) : The file '04_report_test.Rmd' does not exist.
Calls: <Anonymous> -> setwd -> dirname -> abs_path
In addition: Warning message:
In normalizePath(path, winslash = winslash, mustWork = mustWork) :
  path[1]="04_report_test.Rmd": No such file or directory
Execution halted
```

report 4 /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/96/21967ede31b5897a0925f2c0f94a27

visualize ampliseq rev: 0abcc264b22904b42b09a7403317124fa3a82248
benchmark ampliseq rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub:15765587

```bash

#!/usr/bin/env bash

dt=$(date '+%d-%m-%Y_%H.%M.%S');

cp -L 04_report.Rmd $PWD/04_report_test.Rmd

Rscript -e "rmarkdown::render('04_report_test.Rmd', output_file='04_report_$dt.html', output_format='html_document', output_dir='$PWD', clean=TRUE, knit_root_dir='$PWD')"

Rscript -e "rmarkdown::render('04_report_test.Rmd', output_file='04_report_$dt.pdf', output_format='pdf_document', output_dir='$PWD', clean=TRUE, knit_root_dir='$PWD')"

Status

Exit: 0 (COMPLETED) Attempts: 1 

Work directory

/scratch/bjl34716/nf_dev/ampliseq-benchmark/work/b1/2b7facdf8036e96a7bf0148b8bf923
```

Success without makefile!!


#### Whats wrong with 8 and 10

visualize ampliseq rev: 
benchmark ampliseq rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15762898

```bash
GENERATEUNIFRAC

Command exit status:
  1

Command output:
  Saved Visualization to: weighted-unifrac.qzv
  Exported weighted-unifrac.qzv as Visualization to directory weighted-unifrac
  Saved Visualization to: unweighted-unifrac.qzv
  Exported unweighted-unifrac.qzv as Visualization to directory unweighted-unifrac

Command error:
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  cp: cannot stat 'weighted-unifrac/*/*/metadata.tsv': No such file or directory
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  cp: cannot stat 'unweighted-unifrac/*/*/metadata.tsv': No such file or directory

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/bd/2c46f80777378f09c322f72519b0d7

```

This is the path to be updated unweighted-unifrac/raw_data.tsv

visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462
benchmark ampliseq rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15765674

```bash
```

### Todos for Next Week:

- Visualize Ampliseq 
  - check if slurm 15765674 suceeded
- Host microbiome interaction
  - new paper

### Git commits

#### Lab notebook

```bash
4f2b2f6 - Benjamin Lorentz, Fri Dec 9 09:11:20 2022 -0500 : add page for friday
```

#### Visualize Ampliseq

```bash
61eab99 - Benjamin Lorentz, Fri Dec 9 16:49:25 2022 -0500 : update main.nf
218e38f - Benjamin Lorentz, Fri Dec 9 16:46:07 2022 -0500 : update main.nf
0abcc26 - Benjamin Lorentz, Fri Dec 9 16:40:09 2022 -0500 : update main.nf
df7e5ac - Benjamin Lorentz, Fri Dec 9 16:34:14 2022 -0500 : update main.nf
7136c07 - Benjamin Lorentz, Fri Dec 9 15:43:47 2022 -0500 : update main.nf
c04586a - Benjamin Lorentz, Fri Dec 9 14:58:10 2022 -0500 : update main.nf
c452a90 - Benjamin Lorentz, Fri Dec 9 13:17:52 2022 -0500 : update main.nf
5985fac - Benjamin Lorentz, Fri Dec 9 12:56:28 2022 -0500 : update main.nf
```

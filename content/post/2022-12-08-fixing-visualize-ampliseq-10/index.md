---
title: Fixing Visualize Ampliseq 10
author: Ben Lorentz
date: '2022-12-08'
slug: fixing-visualize-ampliseq-10
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Tomorrow:

- Rebuild rocker/verse:4.2.0 to include boxboat/fixuid
- Visualize Ampliseq 
  - check diverity for boxplot visualization
  - modify uncompress diverity
  - add a new process for boxplot
- Host microbiome interaction
  - new paper
  
### Rstudio docker image

```dockerfile
FROM rocker/verse:4.2.0

# creates user "docker" with UID 1000, home directory /home/docker, and shell /bin/sh
# creates group "docker" with GID 1000

RUN addgroup --gid 1000 docker && \
    adduser --uid 1000 --ingroup docker --home /home/docker --shell /bin/sh --disabled-password --gecos "" docker

# Install fixuid in the container, ensure that root owns the file, make it execuatble, and enable the setuid bit. 
# Create the file /etc/fixuid/config.yml with two lines, user: <user> and group: <group> using the user and group from step 1.
  
RUN USER=docker && \
    GROUP=docker && \
    curl -SsL https://github.com/boxboat/fixuid/releases/download/v0.5.1/fixuid-0.5.1-linux-amd64.tar.gz | tar -C /usr/local/bin -xzf - && \
    chown root:root /usr/local/bin/fixuid && \
    chmod 4755 /usr/local/bin/fixuid && \
    mkdir -p /etc/fixuid && \
    printf "user: $USER\ngroup: $GROUP\n" > /etc/fixuid/config.yml
    
# Set the default user/group to user:group and set the entrypoint to fixuid

USER docker:docker
ENTRYPOINT ["fixuid"]

# docker run --rm -it -u 1000:1000 <image name> sh
```

This dockerfile did not work for my use case but I was able to find the [params I needed](https://rocker-project.org/images/versioned/rstudio.html)

##### 4.1.4 USERID and GROUPID

The UID and GID of the default non-root user can be changed as follows:

```bash
docker run --rm -ti -e USERID=1001 -e GROUPID=1001 -p 8787:8787 rocker/rstudio
```

### Visualize Ampliseq

#### Fix process 10 

I updated main to use qiime to generate the diversity pairwise comparisons for unifrac

visualize ampliseq rev: c1ee5fd503bba30df9705b911ca5fc853a23fa8a
ampliseq benchmark rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15723902

```bash
[-        ] process > ORDERIOI -
Process `UNCOMPRESSDIVMATS` declares 3 input channels but 2 were specified

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 67 or see '.nextflow.log' fi

```

Whoops I mixed up which process is which, so I decided to just flip flop since the order isn't important. 

visualize ampliseq rev: 1c476e4e8aa7304e45b455c2040329623c86f4c2
ampliseq benchmark rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15725716

```bash

No such variable: path

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/main.nf' at line: 765 or see '.nextflow.log' f$
[-        ] process > ORDERIOI                       -
```
needed to give a pathname for uncompress div mat

visualize ampliseq rev: 3212921f62abdedf29520556b64e0abaaccc6a79
ampliseq benchmark rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15725970

```bash

# Process 8 


#!/usr/bin/env bash

dt=$(date '+%d-%m-%Y_%H.%M.%S');

Rscript -e "rmarkdown::render('08_report.Rmd', output_file='$PWD/08_report_$dt.html', output_format='html_document', clean=TRUE, knit_root_dir='$PWD')"

Rscript -e "rmarkdown::render('08_report.Rmd', output_file='$PWD/08_report_$dt.pdf', output_format='pdf_document', clean=TRUE, knit_root_dir='$PWD')"

Status

Exit: - (FAILED) Attempts: 1 (action: FINISH)

Work directory

/scratch/bjl34716/nf_dev/ampliseq-benchmark/work/f2/91f49cb3b4a424e00c639f3f7f05f4

# Process Uncompress Div Mats

Status

Exit: 1 (FAILED) Attempts: 1 (action: FINISH)

Work directory

/scratch/bjl34716/nf_dev/ampliseq-benchmark/work/cb/16609964a71651375f9c8adb89903c

# Process Generate Unifrac

Status

Exit: 1 (FAILED) Attempts: 1 (action: FINISH)

Work directory

/scratch/bjl34716/nf_dev/ampliseq-benchmark/work/de/7cf7d03d7d9092dc0972bd810b124f

 (1/1?) no such option: --metadata-column  Did you mean --m-metadata-column?
  Usage: qiime tools export [OPTIONS]

```

Updated the script 

visualize ampliseq rev: 970afc4f91a62486e42e187aa8497369a3c40fbd
ampliseq benchmark rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15730442

```bash

# uncompress div mat

Caused by:
  Process `UNCOMPRESSDIVMATS (1)` terminated with an error exit status (1)

Command executed:

  #!/usr/bin/env bash
  
  dt=$(date '+%d-%m-%Y_%H.%M.%S');
  
  R --no-save < uncompress_diversity.r

Command exit status:
  1

Command output:
  (empty)

Command error:
  .command.sh: line 5: uncompress_diversity.r: No such file or directory

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/cf/8fc28ae5806dde70a535f903f3fe64
  
```

made some changes to main.nf

visualize ampliseq rev: 0f734c369a849f31a71c797acde2146cf3cb7c46
ampliseq benchmark rev: 15c33da5f6243330fc5a4deda9ebe1fd63e1af80
slurm sub: 15735807

```bash
Command exit status:
  2

Command output:
  (empty)

Command error:
  .command.sh: line 5: syntax error near unexpected token `2'
  .command.sh: line 5: `Rscript -e "rmarkdown::render('04_report.Rmd', output_file='04_report_$dt.html', output_format='html_document', output_dir='$PWD', clean=TRUE, knit_root_dir='$PWD')" > 04_html.txt > 2>&1'

Work dir:
  /scratch/bjl34716/nf_dev/ampliseq-benchmark/work/70/0256cb365cccd694fcd412be7f3f9b
```

#### Logfiles generated by rmarkdown::render

This could be fixed by a makefile possibly since you can run cleanup at the end?

Render Rmd script

An R Markdown script can be evaluated and rendered with the following render command or by pressing the knit button in RStudio. The output_format argument defines the format of the output (e.g. html_document or pdf_document). The setting output_format="all" will generate all supported output formats. Alternatively, one can specify several output formats in the metadata section.

rmarkdown::render("sample.Rmd", clean=TRUE, output_format="BiocStyle::html_document")

R

The following shows two options how to run the rendering from the command-line. To render to PDF format, use the argument setting: output_format="pdf_document".

$ Rscript -e "rmarkdown::render('sample.Rmd', output_format='BiocStyle::html_document', clean=TRUE)"

Sh

Alternatively, one can use a Makefile to evaluate and render an R Markdown script. A sample Makefile for rendering the above sample.Rmd can be downloaded here. To apply it to a custom Rmd file, one needs open the Makefile in a text editor and change the value assigned to MAIN (line 13) to the base name of the corresponding .Rmd file (e.g. assign systemPipeRNAseq if the file name is systemPipeRNAseq.Rmd). To execute the Makefile, run the following command from the command-line.

$ make -B

[source](https://girke.bioinformatics.ucr.edu/GEN242/tutorials/rmarkdown/rmarkdown/)

### Git Commits

#### Lab Notebook

```bash
6e7330e - Benjamin Lorentz, Thu Dec 8 12:18:35 2022 -0500 : in the process of fixing process 10 in visualize ampliseq
4c33ab1 - Benjamin Lorentz, Thu Dec 8 10:24:48 2022 -0500 : notes about rstudio docker
0e2acd1 - Benjamin Lorentz, Thu Dec 8 09:46:01 2022 -0500 : added page for thursday
ac4cca0 - Benjamin Lorentz, Wed Dec 7 17:05:58 2022 -0500 : notes for wednesday
```

#### Visualize Ampliseq

```bash
0f734c3 - Benjamin Lorentz, Thu Dec 8 16:27:25 2022 -0500 : update main.nf
667c11f - Benjamin Lorentz, Thu Dec 8 16:22:52 2022 -0500 : update main.nf
636dfce - Benjamin Lorentz, Thu Dec 8 16:20:29 2022 -0500 : update main.nf
9227aa8 - Benjamin Lorentz, Thu Dec 8 16:19:02 2022 -0500 : updated main.nf
970afc4 - Benjamin Lorentz, Thu Dec 8 14:48:03 2022 -0500 : Modify main.nf
3212921 - Benjamin Lorentz, Thu Dec 8 12:16:22 2022 -0500 : Update main.nf
1c476e4 - Benjamin Lorentz, Thu Dec 8 12:10:11 2022 -0500 : Update main.nf
c1ee5fd - Benjamin Lorentz, Thu Dec 8 12:02:16 2022 -0500 : update main.nf and 10_report.Rmd
1867d88 - Benjamin Lorentz, Thu Dec 8 11:55:24 2022 -0500 : update main.nf
c5f3ab1 - Benjamin Lorentz, Wed Dec 7 17:02:42 2022 -0500 : Updated 10_report.md
```

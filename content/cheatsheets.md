---
title: Helpful Codes
description: A place to save helpful commands and to organize by domain
date: '2022-10-05'
menu: main
slug: 'cheatsheets'
---

This would be a good command to run at the end of the day especially to pipe to 
file.

```bash
git log --pretty=format:"%h - %an, %ar : %s"

git log --since=2.weeks

git log --since=1.days --pretty=format:"%h - %an, %ad : %s"
```

### Blogdown specific code

To create a new file:

```r
blogdown::new_post("TITLE",author = "Ben Lorentz",ext = '.Rmd')
```

To render docks before pushing to github:
```r
blogdown::check_site()
blogdown::build_site(build_rmd = TRUE)
blogdown::build_site(build_rmd = 'newfile')
or
blogdown::serve_site()
or
render("content/post/2022-11-02-project-check-in-and-examining-ampliseq-results/index.Rmd")
```

### Docker

start a rstudio session in docker Updated 12.14.22 to allow write access to unix systems.

```bash
docker run -it -v $PWD:/mnt -e ROOT='true' -e PASSWORD='pass' -p 8888:8787 -e USERID=1000 -e GROUPID=1000 rocker/verse:4.2.0
```

Make a dockerfile based on a renv.lockfile

```bash
$ docker run -it -v $PWD:/mnt lorentzb/dockerfiler
```

```r
$ R
> library(dockerfiler)
> my_dock <- dock_from_renv("renv.lock","focal",FROM=rocker/verse)

```

This command will print out the contents of the directory and sort the filesize which can be good to figure out what files need to be removed. 

```bash

$ du -hs * | sort -h

du -hc | sort -h

```

This tag is helpful when you want to link to a paragraph in Obsidian from another text

```bash
<a id="^c1a3b2"></a>
```

### Git tags

```bash

$ git tag ____

$ git push origin tagname

$ git tag -d tagname
```

### Filter out contaminated reads from raw reads

```bash
minimap2 -a REF R1 R2 | samtools sort | samtools view -f 4 | samtools fastq -s 'R0' -1 'R1' -2 'R2'
```

### Nextflow 

Issue where you expect multiple process runs but you only get one back (especially in the case that one of your channels is a reference). By default channels are a channel of values, so in the case of a reference you have to specify .first() or .last() 

ex: 

```nextflow

MINIMAP2_ALIGN(ch_filtered ,contam_path_ch, true, false, true)

MINIMAP2_ALIGN(ch_filtered ,contam_path_ch.first(), true, false, true)
```

where ch_filtered is a channel of reads
contam_path_ch is a tuple of the metadata and a path for the location of the reference database

### Slurm Interactive session

```bash
$ srun --pty  --cpus-per-task=8 --job-name=interact --ntasks=1 --nodes=1 --partition=inter_p --time=12:00:00 --mem=16GB /bin/bash -l
```

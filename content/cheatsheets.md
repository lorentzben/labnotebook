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
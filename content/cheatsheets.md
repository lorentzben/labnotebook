---
title: Helpful Codes
description: A place to save helpful commands and to organize by domain
date: '2022-10-05'
menu: main
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
or
blogdown::serve_site()
```

### Docker

start a rstudio session in docker 

```bash
docker run -p 8888:8787 -it -v $PWD:/mnt -e ROOT='true' -e PASSWORD='pass' rocker/verse:4.2.0
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
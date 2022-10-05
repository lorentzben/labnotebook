---
title: Helpful Codes
author: Ben Lorentz
date: '2022-10-05'
slug: helpful-codes
categories: []
tags:
  - Cheatsheet
---

This would be a good command to run at the end of the day especially to pipe to 
file.

```bash
git log --pretty=format:"%h - %an, %ar : %s"
```

### Blogdown specific code

To create a new file:

```r
blogdown::new_post("TITLE",author = "Ben Lorentz",ext = '.Rmd')
```

To render docks before pushing to github:
```r
blogdown::check_site()
blogdown::build_site()
or
blogdown::serve_site()
```
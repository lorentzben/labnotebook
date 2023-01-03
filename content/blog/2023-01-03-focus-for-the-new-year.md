---
title: 'Focus for the New Year'
date: 2023-01-03T14:34:05Z
draft: false
meta_img: "images/image.png"
tags:
  - "one tag"
  - "another tag"
description: "Description for the page"
---

from 2022-12-23

```md

So the python code can take in values and paths no problem, the next step is to add in the steps 
to actually run the process and save the file to disk

We can possibly wrap the qiime call in python code to use the warnings package to ignore the warnings [seen here](https://www.tutorialexample.com/beginner-guide-to-disable-or-ignore-python-warnings-python-tutorial/)

TODO:
  check downstream diversity files.
  04
  05
  06
  07
  09
  10
  12
  
```

### Todos for Next Year:

- Visualize Ampliseq
  - Check if user submitted cutoff?
  - pass cutoff (user or otherwise) into the core-metric
  - ensure all diversity files downstream are from the newly generated core-metric
    - search for results/diversity and change to emit etc.
- Generate a Mock community M&M or other and validate pipelines
- Open Up Space on the Lacie drive
- review gene 8940 Term Paper

### Gene 8940 Term Paper

Most big issues were not capitalizing Wald test, and there were some grammatical issues that Dr. Bergman Highlighted but he seemed pleased overall with the results from this paper. 

### What Will I Achieve This Month?

I want to determine the main actors is the gut segments of a chicken. I will achieve this by reviewing papers cited in other reviews as well as try to generate mock microbial communities to see if that is a feasible method to summarize the big players. I think that also examining the functional capacity of the microbes is also very important.

### What does Sucess Look Like?

- Being able to summarize the major players in the gut 
- Being able to summarize the major functions of the gut

### Visualize Ampliseq

```bash
update main.nf

    NOT QUITE FUNCTIONAL YET

    - imported the minmax script into the process
    - downloaded a dir to test by hand
    - have script flow control implemented
    - need to translate bash to api calls
```

Current progress.


---
title: 'Downstream Correct Rarefact'
date: 2023-01-06T14:14:42Z
draft: false
meta_img: "images/image.png"
tags: ['visualize-ampliseq', 'downstream']
description: "Description for the page"
---

### Todos for today:

- Visualize Ampliseq
  - update all downstream diveristies
- Generate a Mock community M&M or other and validate pipelines
- Examine some papers collected

### Annotate Jackwood Blast Parser

I started making a ppt to explain the commented main function. I think that this is the material most important to understand since it's the high level functionality. I still need to write on the slides or in the notes more of the conceptual ideas but it is a good start. (also think about how we can explain this in "stages"). 

The next step after commenting the powerpoint will be to comment the lower-level code inside each of the functions so that I can walk through those with Ben Jackwood. I would say we are a good 40% complete so far. 

### Visualize Ampliseq

The downstream processes still need to be examined and updated. 

### Todos for Next Week:

- Visualize Ampliseq
  - !!! update all downstream diversities !!!
- Jackwood Parser
  - Comment the powerpoint
  - Comment the lower level functions
- Generate a Mock community M&M or other and validate pipelines
- Examine some papers collected

### Question for next week:

Can we use a mock community to describe the common taxa in the different chicken gut segments AND can we use that community to benchmark the pipeline we have developed?

### Git Commits

#### Lab Notebook

```bash
0eac6f8 - Benjamin Lorentz, Fri Jan 6 14:28:18 2023 -0500 : added note about blast parser
3fb0009 - Benjamin Lorentz, Fri Jan 6 09:33:24 2023 -0500 : must include tag.html
4bf6bd0 - Benjamin Lorentz, Fri Jan 6 09:31:48 2023 -0500 : single as opposed to double
065a41b - Benjamin Lorentz, Fri Jan 6 09:29:40 2023 -0500 : make tags a list as opposed to hyphens
2d76e15 - Benjamin Lorentz, Fri Jan 6 09:26:36 2023 -0500 : added a tag html and rendered todays page
dbdfd04 - Benjamin Lorentz, Fri Jan 6 09:23:56 2023 -0500 : added a tag definition
8ce8b0c - Benjamin Lorentz, Fri Jan 6 09:16:01 2023 -0500 : added page for friday
```

#### Jackwood Blast Parser

```bash
4d4f09c - Benjamin Lorentz, Fri Jan 6 11:42:43 2023 -0500 : added comments to main()
```
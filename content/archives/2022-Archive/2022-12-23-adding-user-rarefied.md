---
title: '2022 12 23 Adding User Rarefied'
date: 2022-12-23T14:19:30Z
draft: false
meta_img: "images/image.png"
tags:
  - "one tag"
  - "another tag"
description: "Description for the page"
---

### Visualize Ampliseq

#### Rarefaction

Slurm run 15947603 completed sucessfully. 

The next step is to implement the param rarefaction cutoff in the visualize ampliseq nextflow. The best way IMO is to set the default to 0, if that is detected use the min max py from ampliseq and pass those files downstream. If not 0 then run with the user provided.


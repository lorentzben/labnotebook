---
title: Rebuilding Report 01 with Microbiome Analyst
author: 'Ben Lorentz'
date: '2022-10-10'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Todo's from Friday:

- Rebase Report-01 based on microbiome analyst
  - store a copy of the current stacked bar with tax.clean function in it
  - Figure out how to install and pick a version to pin
  - Build a docker image
  - determine general appropriate stacked bar
  - implement
- Work on Homework 3 for class (Genome Assembly)
- Check in on ALDEx2 Analysis
- Check in on Classifiers and their generation.


### Installing Microbiome Analyst

Note when looking into NF-Core stuff they suggest the heriachy to be Bioconda -> someone else's docker image -> (last resort) making your own docker image. And if I remember correctly Microbiome analyst is 1. still under development 2. only available through GitHub. This also means we need to pick a version/commit that we want to be pinned to. 

We keep running into an issue with installing just the dependencies for Microbiome analyst. Since they are using the bleeding edge packages and I was previously using 4.2.0 I think the MASS package baked into rocker/verse:4.2.0 was a little too old. I am downloading rocker/verse:4.2.1 to see if we can install on that one. 

This seems like the correct approach to use 4.2.1 we just need to install Tax4Fun through github I think. From the github "nick-youngblut/Tax4Fun by ensuring the following dependencies are also installed - rhdf5; qiimer; joey711/biom."

Eventually they will migrate to tax4fun2. 

### Homework 3

I have sucessfully assembed long reads with canu and short reads with SPADES. Quast and Mummer are running right now. 

Todos for tomorrow:

- reply to Shailes to set up a time to meet
- Watch lectures for #14 for class
- Check in on the classifier (though it outran 96hrs so it may take longer)
- Continue trying to build the microbiome analyst image 
  - install github version of tax4fun


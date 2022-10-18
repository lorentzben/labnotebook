---
title: Implement Report Chunk 4
author: Ben Lorentz
date: '2022-10-18'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for today:

- Evaluate Report 03
- Start Report 04
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Update repo for Homework for this week
- Check in on classifier still running

- update WSL2 packages locally

```bash
apt list --upgradable
 
```

### Report 04

The former report 04 
obs shannon simpson  chao1 ace faith_pd 

When copying over reports to someplace I can see them 03 and 04 show 0kb...

here is a run to look into

```bash
[b5/a19225] process > ORDERIOI (1)                         [100%] 1 of 1 ✔
[6f/56aa40] process > REPORT01BARPLOT (1)                  [100%] 1 of 1 ✔
[cb/1204f6] process > REFORMATANDQZATAX (1)                [100%] 1 of 1 ✔
[e2/092e0a] process > GENERATEBIOMFORGRAPHLAN (1)          [100%] 1 of 1 ✔
[e1/1557c3] process > RUNGRAPHLAN (1)                      [100%] 1 of 1 ✔
[dd/fb4cf7] process > REPORT02GRAPHLANPHYLOGENETICTREE (1) [  0%] 0 of 1
[2f/1be993] process > REPORT03HEATMAP (1)                  [  0%] 0 of 1
[e5/497905] process > REPORT04ALPHATABLE (1)               [100%] 1 of 1
```

I had a mistype for mode it was mSode, the issue is still heatmaps isn't being copied over. I first want to see if the report copies over. 

Report 01 also did not include images correctly so I'm thinking of trying to knit them in now that we don't have to deal with the mounting issue, and also do this with report 02:

```bash
knitr::include_graphics("temp.png")
```

update WSL2 packages locally

```bash
apt list --upgradable
 
```
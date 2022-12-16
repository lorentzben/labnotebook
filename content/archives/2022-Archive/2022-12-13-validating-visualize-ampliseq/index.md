---
title: Validating Visualize Ampliseq
author: Ben Lorentz
date: '2022-12-13'
slug: validating-visualize-ampliseq
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Visualize Ampliseq 
  - check if slurm 15765674 suceeded
- Host microbiome interaction
  - new paper
  
### Visualize Ampliseq

#### Getting low effeciency results

slurm: 15813195
ampliseq benchmark rev: a594451cee11613389990ccac4e1fa9a4a7f05af 
visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462

```bash
Completed at: 13-Dec-2022 09:59:47
Duration    : 12m 7s
CPU hours   : 0.7 (0.2% cached)
Succeeded   : 22
Cached      : 1
```

sweet!

#### Getting high effeciency results

slurm: 15814945
ampliseq benchmark rev: c78db6cf268323951b70d84047ca28a24b08d8e3
visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462

```bash
Specified params file does not exists: /home/bjl34716/nf_dev/ampliseq-benchmarking/high_rich/high_rich_viz_params.yaml
```

slurm: 15823145
ampliseq benchmark rev: c9c6a1b89b5958d231379ad1ef488032a87547e3
visualize ampliseq rev: 61eab99387e188483e8827c03b07e7a3fd872462

```bash
sucess
```

### Todos for Tomorrow:

- Visualize Ampliseq 
  - examine the 3 results to see what richness should be selected for this set
    - AND record why!!
- Host microbiome interaction
  - finish Borda-Molina

### Git Commits

#### Lab Notebook

```bash
f6e0bfe - Benjamin Lorentz, Tue Dec 13 10:45:19 2022 -0500 : add notes for tuesday
```

#### Ampliseq Benchmark

```bash
c9c6a1b - Benjamin Lorentz, Tue Dec 13 16:20:52 2022 -0500 : added high_rich_vis_params.yaml
c78db6c - Benjamin Lorentz, Tue Dec 13 10:42:58 2022 -0500 : update high_rich_params; slurm-sub-high
a594451 - Benjamin Lorentz, Tue Dec 13 09:36:59 2022 -0500 : update slurm-sub-low.sh
```


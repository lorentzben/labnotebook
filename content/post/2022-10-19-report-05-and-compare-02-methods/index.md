---
title: Report 05 and Compare 02 Methods
author: Ben Lorentz
date: '2022-10-19'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Todos for today:
- Watch lecture for Thursday
- Check in on slurm run slurm-14913334.out
- Start Report 05
- Update repo for Homework for this week
  - do homework 4
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Check in on classifier still running
- update WSL2 packages locally


### Compare automate 16 nf Report chunk 02 to Visualize Ampliseq 

Outdir for Automate 16 nf 
/work/sealab/bjl34716/nf_dev/clean_dir
workdir
/scratch/bjl34716/nf_dev/clean_dir/work/55/6f41f34adf874be2fe7731c8c3a997

So locally the report will render but when put on the server it shows the same rmarkdown render 99 error.

Visualize Ampliseq Workdir
71/5b0e30
/scratch/bjl34716/ampliseq-vis/work/7d/68792308e16946653bd5048832f0eb

I am trying to list out the files in the directory to see if that explains anything.

This is what visualize ampliseq looks like:
```bash
.:
total 16K
lrwxrwxrwx 1 bjl34716 sealab   92 Oct 19 10:37 02_report.Rmd -> /home/bjl34716/.nextflow/assets/lorentzben/visualize-am
lrwxrwxrwx 1 bjl34716 sealab   81 Oct 19 10:37 item_of_interest.csv -> /scratch/bjl34716/ampliseq-vis/work/tmp/04/2e26e
drwxr-xr-x 2 bjl34716 sealab 4.0K Oct 19 10:37 phylo_trees

./phylo_trees:
total 12K
lrwxrwxrwx 1 bjl34716 sealab 100 Oct 19 10:37 NC_image_graph.png -> /scratch/bjl34716/ampliseq-vis/work/bb/44d411473bf7
lrwxrwxrwx 1 bjl34716 sealab 100 Oct 19 10:37 OC_image_graph.png -> /scratch/bjl34716/ampliseq-vis/work/bb/44d411473bf7
lrwxrwxrwx 1 bjl34716 sealab 100 Oct 19 10:37 UC_image_graph.png -> /scratch/bjl34716/ampliseq-vis/work/bb/44d411473bf7
/scratch/bjl34716/ampliseq-vis/work/7d/68792308e16946653bd5048832f0eb
```

This is what automate 16 looks like:
```bash
.:
total 40K
lrwxrwxrwx 1 bjl34716 sealab   88 Oct 18 22:41 02_report.Rmd -> /home/bjl34716/.nextflow/assets/lorentzben/automate_16_nf/report_gen_files/02_report.Rmd
drwxr-xr-x 2 bjl34716 sealab 4.0K Oct 18 22:41 Figures
lrwxrwxrwx 1 bjl34716 sealab   85 Oct 18 22:41 item_of_interest.csv -> /scratch/bjl34716/nf_dev/clean_dir/work/tmp/6c/94f05a11032f4da8910944012cd769/input.2
lrwxrwxrwx 1 bjl34716 sealab   86 Oct 18 22:41 metadata.tsv -> /scratch/bjl34716/nf_dev/clean_dir/work/5d/0f069a7c144bc77662fff5a47f6097/metadata.tsv
lrwxrwxrwx 1 bjl34716 sealab  100 Oct 18 22:41 order_item_of_interest.csv -> /scratch/bjl34716/nf_dev/clean_dir/work/55/8f4f3745a2dd56437a15b226efdb2c/order_item_of_interest.csv
drwxr-xr-x 2 bjl34716 sealab 4.0K Oct 19 10:23 phylo_trees
drwxr-xr-x 2 bjl34716 sealab 4.0K Oct 18 22:41 phylo_trees3

./Figures:
total 0

./phylo_trees:
total 12K
lrwxrwxrwx 1 bjl34716 sealab 104 Oct 18 22:41 14_image_graph.png -> /scratch/bjl34716/nf_dev/clean_dir/work/f1/a08dbf5b067413eb66ca827aa33570/phylo_trees/14_image_graph.png
lrwxrwxrwx 1 bjl34716 sealab 104 Oct 18 22:41 28_image_graph.png -> /scratch/bjl34716/nf_dev/clean_dir/work/f1/a08dbf5b067413eb66ca827aa33570/phylo_trees/28_image_graph.png
lrwxrwxrwx 1 bjl34716 sealab 103 Oct 18 22:41 7_image_graph.png -> /scratch/bjl34716/nf_dev/clean_dir/work/f1/a08dbf5b067413eb66ca827aa33570/phylo_trees/7_image_graph.png
```

This is the error I keep receiving when I try to run the pipeline locally:

``bash
 Error in include_graphics(tree_filenames) :
    Cannot find the file(s): "../../../../../my_utils/work/39/a46d3ba33948cfd64267d4f9221ab2/phylo_trees/NC_image_graph.png"; "../../../../../my_utils/work/39/a46d3ba33948cfd64267d4f9221ab2/phylo_trees/OC_image_graph.png"; "../../../../../my_utils/work/39/a46d3ba33948cfd64267d4f9221ab2/phylo_trees/UC_image_graph.png"
  Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> include_graphics
```

My solution is to assign the local profile a dummy file that will render and point the user to the images in the directory and then when using the slurm submission select the script that will render files into the report correctly. 

To be validated, Huzzah!! It appears that my code ran without a hitch :).

I need to figure out how to set the nextflow singularity cache correctly as well it keeps deleting the cache between runs.

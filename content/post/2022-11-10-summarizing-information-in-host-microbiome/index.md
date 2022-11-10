---
title: Summarizing Information in Host Microbiome
author: Ben Lorentz
date: '2022-11-10'
slug: summarizing-information-in-host-microbiome
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segement
    - they may have done some of this heavy lifting for us.
- site for microbiome
  - ingest Zou
- continue reading jones
- Visualize Ampliseq
  - add example params and slurm for ampliseq into ampliseq-vis repos
- Run Visualize Ampliseq
  - on low med high richness samples
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Try to run DESeq2’s GLM/LRT on shaile’s design

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

Today I want to finish ingesting the documents and then summarize each page's information. I know we will be working on my term paper later today during class time. I should also at least download Shailes' data to see what it looks like. Finally we should look at the results from visualize ampliseq 2. 

### Host Microbiome Interaction

I added some summaries in 

Ceca:

Ceca are the transition point between the small and large intestine. Fermentation of carbohydrates is an important process in the ceca with one of the major byproducts being short chain fatty acids (SCFAs). Genes related to glycosyl hydrolase are commonly present. [source](https://lorentz-host-microbe-interaction.netlify.app/segments/ceca/)

Small Intestine:

The most protein degradation and digestion happens in the small intestine, especially the duodenum and jejunum. Some of the active enzymes that cleve protien are trypsin, chymotrypsin, carboxypeptidase and proelastase. These split off ammino acids are absorbed in the small intestine.  In the duodeunm the environment changes from acidic to alkaline with the addition of bile and excretions from the pancrease. Most of the absorption occurs in the jejunum due to its large size. When passing into the Ileum water and minerals are primarily absorbed, less digestive and AA absorption is observed in the ileum. [source](https://lorentz-host-microbe-interaction.netlify.app/segments/small-intestine-duodneumjejunumileum/)

### Term paper progress

I have a directory of Kallisto results that is separated by tissue type. My next step is to generate a report for each tissue to compare which genes are differentially expressed.

I am going to make 5 different rscripts (one for each tissue) and then a driver slurm script.

I have made the script and pushed them to the server, the inital run is:

revision: 91ec53c5cf43122837c97c854c67647141601fa6
slurm job: 32433

The logfile produced is: 

```bash
# log.32433

running sleuth on ceca results

R version 3.6.1 (2019-07-05) -- "Action of the Toes"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-conda_cos6-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> #!/usr/bin/env Rscript
> # Written by Casey Bergman https://github.com/cbergman
> suppressMessages({
+  library("sleuth")
+ })
> 
> #TODO update paths to correct dirs 
> 
> #set input and output dirs
> datapath <- "/home/bjl34716/gene8940-term-paper/data/kallisto/ceca"  # you need to modify this line to match the path made by your BASH script
> resultdir <- "/work/gene8940/bjl34716/term_paper/results"   # you need to modify this line to match the path made by your BASH script
> setwd(resultdir)
> 
> #TODO update this metadata section to be true to the current analysis
> #create a sample-to-condition metadata object
> sample <- c("SRR8265548", "SRR8265550","SRR8265621","SRR8265623","SRR8265625","SRR8265627","SRR8265629","SRR8265549","SRR8265591","SRR8265622","SRR8265624" ,"SRR8265626","SRR8265628","SRR8265630") #create vector of sample IDs
> kallisto_dirs <- file.path(datapath, sample) #create vector of paths to kallisto output directories
> condition <- c(rep("high",7),rep("low",7)) #create vector of treatments in same order as sample IDs
> samples_to_conditions <- data.frame(sample,condition) #create dataframe associating treatments to sample IDs
> samples_to_conditions <- dplyr::mutate(samples_to_conditions, path = kallisto_dirs) #add kallisto output paths to dataframe
> 
> # check that directories and metadata object are OK
> # print(kallisto_dirs)
> # print(samples_to_conditions)
> 
> # read data into sleuth_object, import bootstrap summaries and TPMs, and perform normalization/filtering steps
> sleuth_object <- sleuth_prep(samples_to_conditions, extra_bootstrap_summary = TRUE, read_bootstrap_tpm=TRUE)
reading in kallisto results
dropping unused factor levels
..............
normalizing est_counts
11118 targets passed the filter
normalizing tpm
merging in metadata
summarizing bootstraps
..............
> 
> # estimate parameters for the full linear model that includes the conditions as factors
> sleuth_object <- sleuth_fit(sleuth_object, ~condition, 'full')
fitting measurement error models
shrinkage estimation
computing variance of betas
> 
> # estimate parameters for the reduced linear model that assumes equal transcript abundances in both conditions
> sleuth_object <- sleuth_fit(sleuth_object, ~1, 'reduced')
fitting measurement error models
shrinkage estimation
computing variance of betas
> 
> # perform likelihood ratio test to identify transcripts whose fit is significantly better under full model relative to reduced model
> sleuth_object <- sleuth_lrt(sleuth_object, 'reduced', 'full')
> 
> # check that sleuth object is OK
> models(sleuth_object)
[  full  ]
formula:  ~condition 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
 	conditionlow
[  reduced  ]
formula:  ~1 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
> 
> #summarize the sleuth results for DE genes with q-values < 0.05
> sleuth_table <- sleuth_results(sleuth_object, 'reduced:full', 'lrt', show_all = FALSE)
> sleuth_significant <- dplyr::filter(sleuth_table, qval <= 0.05)
> 
> #print the summary table for DE genes with q-values < 0.05
> write.csv(x = sleuth_significant, file = "high_vs_low_ceca_sleuth_q_0.05.csv", row.names = FALSE)
> 
> #visualize results for the 10 most significant DE genes
> #TODO determine if more genes should be visualized 
> pdf(file="Sleuth_Ceca_Results.pdf")
> for(i in sleuth_significant$target_id[1:10]) {
+   p1 <- plot_bootstrap(sleuth_object, i, units = "tpm", color_by = "condition")
+   print(p1)
+   print("significant genes identified: ")
+   print(lenght(sleuth_significant$target_id))
+ }
Error in get_bootstrap_summary(obj, target_id, units) : 
  couldn't find target_id 'NA'
Calls: plot_bootstrap -> get_bootstrap_summary
Execution halted
running sleuth on duodenum results

R version 3.6.1 (2019-07-05) -- "Action of the Toes"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-conda_cos6-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> #!/usr/bin/env Rscript
> # Written by Casey Bergman https://github.com/cbergman
> suppressMessages({
+  library("sleuth")
+ })
> 
> #TODO update paths to correct dirs 
> 
> #set input and output dirs
> datapath <- "/home/bjl34716/gene8940-term-paper/data/kallisto/duodenum"  # you need to modify this line to match the path made by your BASH script
> resultdir <- "/work/gene8940/bjl34716/term_paper/results"   # you need to modify this line to match the path made by your BASH script
> setwd(resultdir)
> 
> #TODO update this metadata section to be true to the current analysis
> #create a sample-to-condition metadata object
> sample <- c("SRR8265558", "SRR8265560", "SRR8265562", "SRR8265633", "SRR8265635", "SRR8265637", "SRR8265639", "SRR8265557","SRR8265559", "SRR8265561", "SRR8265634", "SRR8265636", "SRR8265638", "SRR8265640") #create vector of sample IDs
> kallisto_dirs <- file.path(datapath, sample) #create vector of paths to kallisto output directories
> condition <- c(rep('high',7),rep('low',7)) #create vector of treatments in same order as sample IDs
> samples_to_conditions <- data.frame(sample,condition) #create dataframe associating treatments to sample IDs
> samples_to_conditions <- dplyr::mutate(samples_to_conditions, path = kallisto_dirs) #add kallisto output paths to dataframe
> 
> # check that directories and metadata object are OK
> # print(kallisto_dirs)
> # print(samples_to_conditions)
> 
> # read data into sleuth_object, import bootstrap summaries and TPMs, and perform normalization/filtering steps
> sleuth_object <- sleuth_prep(samples_to_conditions, extra_bootstrap_summary = TRUE, read_bootstrap_tpm=TRUE)
reading in kallisto results
dropping unused factor levels
..............
normalizing est_counts
10582 targets passed the filter
normalizing tpm
merging in metadata
summarizing bootstraps
..............
> 
> # estimate parameters for the full linear model that includes the conditions as factors
> sleuth_object <- sleuth_fit(sleuth_object, ~condition, 'full')
fitting measurement error models
shrinkage estimation
computing variance of betas
> 
> # estimate parameters for the reduced linear model that assumes equal transcript abundances in both conditions
> sleuth_object <- sleuth_fit(sleuth_object, ~1, 'reduced')
fitting measurement error models
shrinkage estimation
computing variance of betas
> 
> # perform likelihood ratio test to identify transcripts whose fit is significantly better under full model relative to reduced model
> sleuth_object <- sleuth_lrt(sleuth_object, 'reduced', 'full')
> 
> # check that sleuth object is OK
> models(sleuth_object)
[  full  ]
formula:  ~condition 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
 	conditionlow
[  reduced  ]
formula:  ~1 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
> 
> #summarize the sleuth results for DE genes with q-values < 0.05
> sleuth_table <- sleuth_results(sleuth_object, 'reduced:full', 'lrt', show_all = FALSE)
> sleuth_significant <- dplyr::filter(sleuth_table, qval <= 0.05)
> 
> #print the summary table for DE genes with q-values < 0.05
> write.csv(x = sleuth_significant, file = "high_vs_low_duodenum_sleuth_q_0.05.csv", row.names = FALSE)
> 
> #visualize results for the 10 most significant DE genes
> #TODO determine if more genes should be visualized 
> pdf(file="Sleuth_duodenum_Results.pdf")
> for(i in sleuth_significant$target_id[1:10]) {
+   p1 <- plot_bootstrap(sleuth_object, i, units = "tpm", color_by = "condition")
+   print(p1)
+   print("significant genes identified: ")
+   print(lenght(sleuth_significant$target_id))
+ }
Error in get_bootstrap_summary(obj, target_id, units) : 
  couldn't find target_id 'NA'
Calls: plot_bootstrap -> get_bootstrap_summary
Execution halted
running sleuth on ileum results

R version 3.6.1 (2019-07-05) -- "Action of the Toes"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-conda_cos6-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> #!/usr/bin/env Rscript
> # Written by Casey Bergman https://github.com/cbergman
> suppressMessages({
+  library("sleuth")
+ })
> 
> #TODO update paths to correct dirs 
> 
> #set input and output dirs
> datapath <- "/home/bjl34716/gene8940-term-paper/data/kallisto/ileum"  # you need to modify this line to match the path made by your BASH script
> resultdir <- "/work/gene8940/bjl34716/term_paper/results"   # you need to modify this line to match the path made by your BASH script
> setwd(resultdir)
> 
> #TODO update this metadata section to be true to the current analysis
> #create a sample-to-condition metadata object
> sample <- c("SRR8265592", "SRR8265594", "SRR8265596", "SRR8265598", "SRR8265600", "SRR8265654", "SRR8265659", "SRR8265593", "SRR8265595", "SRR8265597", "SRR8265599", "SRR8265653", "SRR8265660") #create vector of sample IDs
> kallisto_dirs <- file.path(datapath, sample) #create vector of paths to kallisto output directories
> condition <- c(rep('high',7),rep('low',6)) #create vector of treatments in same order as sample IDs
> samples_to_conditions <- data.frame(sample,condition) #create dataframe associating treatments to sample IDs
> samples_to_conditions <- dplyr::mutate(samples_to_conditions, path = kallisto_dirs) #add kallisto output paths to dataframe
> 
> # check that directories and metadata object are OK
> # print(kallisto_dirs)
> # print(samples_to_conditions)
> 
> # read data into sleuth_object, import bootstrap summaries and TPMs, and perform normalization/filtering steps
> sleuth_object <- sleuth_prep(samples_to_conditions, extra_bootstrap_summary = TRUE, read_bootstrap_tpm=TRUE)
reading in kallisto results
dropping unused factor levels
.............
normalizing est_counts
10492 targets passed the filter
normalizing tpm
merging in metadata
summarizing bootstraps
.............
> 
> # estimate parameters for the full linear model that includes the conditions as factors
> sleuth_object <- sleuth_fit(sleuth_object, ~condition, 'full')
fitting measurement error models
shrinkage estimation
2 NA values were found during variance shrinkage estimation due to mean observation values outside of the range used for the LOESS fit.
The LOESS fit will be repeated using exact computation of the fitted surface to extrapolate the missing values.
These are the target ids with NA values: ENSGALT00000043743.1, ENSGALT00000029093.1
computing variance of betas
> 
> # estimate parameters for the reduced linear model that assumes equal transcript abundances in both conditions
> sleuth_object <- sleuth_fit(sleuth_object, ~1, 'reduced')
fitting measurement error models
shrinkage estimation
2 NA values were found during variance shrinkage estimation due to mean observation values outside of the range used for the LOESS fit.
The LOESS fit will be repeated using exact computation of the fitted surface to extrapolate the missing values.
These are the target ids with NA values: ENSGALT00000043743.1, ENSGALT00000029093.1
computing variance of betas
> 
> # perform likelihood ratio test to identify transcripts whose fit is significantly better under full model relative to reduced model
> sleuth_object <- sleuth_lrt(sleuth_object, 'reduced', 'full')
> 
> # check that sleuth object is OK
> models(sleuth_object)
[  full  ]
formula:  ~condition 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
 	conditionlow
[  reduced  ]
formula:  ~1 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
> 
> #summarize the sleuth results for DE genes with q-values < 0.05
> sleuth_table <- sleuth_results(sleuth_object, 'reduced:full', 'lrt', show_all = FALSE)
> sleuth_significant <- dplyr::filter(sleuth_table, qval <= 0.05)
> 
> #print the summary table for DE genes with q-values < 0.05
> write.csv(x = sleuth_significant, file = "high_vs_low_ileum_sleuth_q_0.05.csv", row.names = FALSE)
> 
> #visualize results for the 10 most significant DE genes
> #TODO determine if more genes should be visualized 
> pdf(file="Sleuth_ileum_Results.pdf")
> for(i in sleuth_significant$target_id[1:10]) {
+   p1 <- plot_bootstrap(sleuth_object, i, units = "tpm", color_by = "condition")
+   print(p1)
+   print("significant genes identified: ")
+   print(lenght(sleuth_significant$target_id))
+ }
Error in get_bootstrap_summary(obj, target_id, units) : 
  couldn't find target_id 'NA'
Calls: plot_bootstrap -> get_bootstrap_summary
Execution halted
running sleuth on jejunum results

R version 3.6.1 (2019-07-05) -- "Action of the Toes"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-conda_cos6-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> #!/usr/bin/env Rscript
> # Written by Casey Bergman https://github.com/cbergman
> suppressMessages({
+  library("sleuth")
+ })
> 
> #TODO update paths to correct dirs 
> 
> #set input and output dirs
> datapath <- "/home/bjl34716/gene8940-term-paper/data/kallisto/jejunum"  # you need to modify this line to match the path made by your BASH script
> resultdir <- "/work/gene8940/bjl34716/term_paper/results"   # you need to modify this line to match the path made by your BASH script
> setwd(resultdir)
> 
> #TODO update this metadata section to be true to the current analysis
> #create a sample-to-condition metadata object
> sample <- c("SRR8265631", "SRR8265652", "SRR8265656", "SRR8265658", "SRR8265632", "SRR8265651", "SRR8265655", "SRR8265657") #create vector of sample IDs
> kallisto_dirs <- file.path(datapath, sample) #create vector of paths to kallisto output directories
> condition <- c(rep('high',4),rep('low',4)) #create vector of treatments in same order as sample IDs
> samples_to_conditions <- data.frame(sample,condition) #create dataframe associating treatments to sample IDs
> samples_to_conditions <- dplyr::mutate(samples_to_conditions, path = kallisto_dirs) #add kallisto output paths to dataframe
> 
> # check that directories and metadata object are OK
> # print(kallisto_dirs)
> # print(samples_to_conditions)
> 
> # read data into sleuth_object, import bootstrap summaries and TPMs, and perform normalization/filtering steps
> sleuth_object <- sleuth_prep(samples_to_conditions, extra_bootstrap_summary = TRUE, read_bootstrap_tpm=TRUE)
reading in kallisto results
dropping unused factor levels
........
normalizing est_counts
11548 targets passed the filter
normalizing tpm
merging in metadata
summarizing bootstraps
........
> 
> # estimate parameters for the full linear model that includes the conditions as factors
> sleuth_object <- sleuth_fit(sleuth_object, ~condition, 'full')
fitting measurement error models
shrinkage estimation
6 NA values were found during variance shrinkage estimation due to mean observation values outside of the range used for the LOESS fit.
The LOESS fit will be repeated using exact computation of the fitted surface to extrapolate the missing values.
These are the target ids with NA values: ENSGALT00000013689.5, ENSGALT00000032155.3, ENSGALT00000036503.2, ENSGALT00000039674.2, ENSGALT00000042756.1, ENSGALT00000046143.1
computing variance of betas
> 
> # estimate parameters for the reduced linear model that assumes equal transcript abundances in both conditions
> sleuth_object <- sleuth_fit(sleuth_object, ~1, 'reduced')
fitting measurement error models
shrinkage estimation
computing variance of betas
> 
> # perform likelihood ratio test to identify transcripts whose fit is significantly better under full model relative to reduced model
> sleuth_object <- sleuth_lrt(sleuth_object, 'reduced', 'full')
> 
> # check that sleuth object is OK
> models(sleuth_object)
[  full  ]
formula:  ~condition 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
 	conditionlow
[  reduced  ]
formula:  ~1 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
> 
> #summarize the sleuth results for DE genes with q-values < 0.05
> sleuth_table <- sleuth_results(sleuth_object, 'reduced:full', 'lrt', show_all = FALSE)
> sleuth_significant <- dplyr::filter(sleuth_table, qval <= 0.05)
> 
> #print the summary table for DE genes with q-values < 0.05
> write.csv(x = sleuth_significant, file = "high_vs_low_jejunum_sleuth_q_0.05.csv", row.names = FALSE)
> 
> #visualize results for the 10 most significant DE genes
> #TODO determine if more genes should be visualized 
> pdf(file="Sleuth_jejunum_Results.pdf")
> for(i in sleuth_significant$target_id[1:10]) {
+   p1 <- plot_bootstrap(sleuth_object, i, units = "tpm", color_by = "condition")
+   print(p1)
+   print("significant genes identified: ")
+   print(lenght(sleuth_significant$target_id))
+ }
Error in get_bootstrap_summary(obj, target_id, units) : 
  couldn't find target_id 'NA'
Calls: plot_bootstrap -> get_bootstrap_summary
Execution halted
running sleuth on liver results

R version 3.6.1 (2019-07-05) -- "Action of the Toes"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-conda_cos6-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> #!/usr/bin/env Rscript
> # Written by Casey Bergman https://github.com/cbergman
> suppressMessages({
+  library("sleuth")
+ })
> 
> #TODO update paths to correct dirs 
> 
> #set input and output dirs
> datapath <- "/home/bjl34716/gene8940-term-paper/data/kallisto/liver"  # you need to modify this line to match the path made by your BASH script
> resultdir <- "/work/gene8940/bjl34716/term_paper/results"   # you need to modify this line to match the path made by your BASH script
> setwd(resultdir)
> 
> #TODO update this metadata section to be true to the current analysis
> #create a sample-to-condition metadata object
> sample <- c("SRR8265554", "SRR8265556", "SRR8265612", "SRR8265614", "SRR8265616", "SRR8265618", "SRR8265620", "SRR8265553", "SRR8265555", "SRR8265611", "SRR8265613", "SRR8265615", "SRR8265617", "SRR8265619") #create vector of sample IDs
> kallisto_dirs <- file.path(datapath, sample) #create vector of paths to kallisto output directories
> condition <- c(rep('high',7),rep('low',7)) #create vector of treatments in same order as sample IDs
> samples_to_conditions <- data.frame(sample,condition) #create dataframe associating treatments to sample IDs
> samples_to_conditions <- dplyr::mutate(samples_to_conditions, path = kallisto_dirs) #add kallisto output paths to dataframe
> 
> # check that directories and metadata object are OK
> # print(kallisto_dirs)
> # print(samples_to_conditions)
> 
> # read data into sleuth_object, import bootstrap summaries and TPMs, and perform normalization/filtering steps
> sleuth_object <- sleuth_prep(samples_to_conditions, extra_bootstrap_summary = TRUE, read_bootstrap_tpm=TRUE)
reading in kallisto results
dropping unused factor levels
..............
normalizing est_counts
9006 targets passed the filter
normalizing tpm
merging in metadata
summarizing bootstraps
..............
> 
> # estimate parameters for the full linear model that includes the conditions as factors
> sleuth_object <- sleuth_fit(sleuth_object, ~condition, 'full')
fitting measurement error models
shrinkage estimation
1 NA values were found during variance shrinkage estimation due to mean observation values outside of the range used for the LOESS fit.
The LOESS fit will be repeated using exact computation of the fitted surface to extrapolate the missing values.
These are the target ids with NA values: ENSGALT00000029093.1
computing variance of betas
> 
> # estimate parameters for the reduced linear model that assumes equal transcript abundances in both conditions
> sleuth_object <- sleuth_fit(sleuth_object, ~1, 'reduced')
fitting measurement error models
shrinkage estimation
1 NA values were found during variance shrinkage estimation due to mean observation values outside of the range used for the LOESS fit.
The LOESS fit will be repeated using exact computation of the fitted surface to extrapolate the missing values.
These are the target ids with NA values: ENSGALT00000029093.1
computing variance of betas
> 
> # perform likelihood ratio test to identify transcripts whose fit is significantly better under full model relative to reduced model
> sleuth_object <- sleuth_lrt(sleuth_object, 'reduced', 'full')
> 
> # check that sleuth object is OK
> models(sleuth_object)
[  full  ]
formula:  ~condition 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
 	conditionlow
[  reduced  ]
formula:  ~1 
data modeled:  obs_counts 
transform sync'ed:  TRUE 
coefficients:
	(Intercept)
> 
> #summarize the sleuth results for DE genes with q-values < 0.05
> sleuth_table <- sleuth_results(sleuth_object, 'reduced:full', 'lrt', show_all = FALSE)
> sleuth_significant <- dplyr::filter(sleuth_table, qval <= 0.05)
> 
> #print the summary table for DE genes with q-values < 0.05
> write.csv(x = sleuth_significant, file = "high_vs_low_liver_sleuth_q_0.05.csv", row.names = FALSE)
> 
> #visualize results for the 10 most significant DE genes
> #TODO determine if more genes should be visualized 
> pdf(file="Sleuth_liver_Results.pdf")
> for(i in sleuth_significant$target_id[1:10]) {
+   p1 <- plot_bootstrap(sleuth_object, i, units = "tpm", color_by = "condition")
+   print(p1)
+   print("significant genes identified: ")
+   print(lenght(sleuth_significant$target_id))
+ }
Error in get_bootstrap_summary(obj, target_id, units) : 
  couldn't find target_id 'NA'
Calls: plot_bootstrap -> get_bootstrap_summary
Execution halted
```

The main error is: 

  "Error in get_bootstrap_summary(obj, target_id, units) : 
    couldn't find target_id 'NA'
  Calls: plot_bootstrap -> get_bootstrap_summary"

and the result files are empty. We will have to run the code line by line to see what the issue is.

So my gut check was correct, all of the genes/transcripts are being filtered out since their q-values are greater than 0.05 and even less that 0.1. I also followed the wald test format of study design, and this also followed the same trend.

I sent this message to Dr. Bergman and Jingxuan:

```
Hi Dr. Bergman and Jingxuan, I am working on my DEG analysis of RNA seq data in 5 different tissues in chickens comparing high feed efficiency vs low feed efficiency birds. I have successfully run my data through kallisto and am working in sleuth. 

My current issue is that when filtering transcripts based on q-values I have no significant hits, while the paper I am referencing (https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6754422/) (where they were using STAR and HTSeq) had a little over a thousand hits (although they were using p-values and Fold changes > 1.5) I’m guessing that they used p-value because some of their adjusted p-vals were N/A so they wanted to have a value for every observation. I also ran the wald test with similar results. 

My main question is: to accurately replicate their study (GO/ functional analysis of DEG) should I use the non-corrected p-values or end the analysis with no significantly differentially expressed genes (even using q<= 0.1 as a cutoff does not return any genes), I’d be open to discussing possible methods to move forward if either of you had input, Thanks!
```

My thought is I can still generate a gene list using the FC > 1.5 && p-val <= 0.05, and then examine those genes, it will just be less robust than if they were true hits. Otherwise I can look for a different dataset possibly.

I need to post a weekly update on the github issue for what progress we have made so far. 

### Shailes' Data 


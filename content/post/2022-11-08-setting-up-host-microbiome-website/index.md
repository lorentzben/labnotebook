---
title: Setting Up Host Microbiome Website
author: 'Ben Lorentz'
date: '2022-11-08'
slug: setting-up-host-microbiome-website
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
  - find better index page
  - continue to migrate data from synology dir to the ssd one and push
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

I want to finish website migration, Then Finish importing and synthesizing Tillocca, find taxa table from Tillocca references, then maybe Shailes data, and finally during class time start one tissue analysis. 

### Host Microbiome Interactions Website

I was able to get the website set up pretty close to the format I want to start with. One improvement might be the sections part in like citations etc, but that is something we'll have to figure out a little later. We also must update all of the links to make sure they lead to the correct location and add DOI links for the papers cited. Then we also need to make sure all the citations are digested into the proper sections. The updated page is [here](https://lorentz-host-microbe-interaction.netlify.app/).

I was able to fix most of the links on the site so far and have a plan to use going forward. The secret sauce is using this stub to link to chunks of text the way that obsidian does.

```bash
<a id="^d0c6ae"></a>
```

Things to next would be to add these stublinks in all the citations, and to add DOI links to every citation so that people can cross reference.

### Term Project

I am going to log into class to have some work-partners while I get a tissue analysis set up. While logged in, I decided that it makes more sense to just run all the kallisto runs at once and creates a nested directory of kallisto results. The next step will be making different sleuth scripts for each tissue. (because of the metadata I think this is easiest) 

### Todos for Tomorrow:

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segement
    - they may have done some of this heavy lifting for us.
- site for microbiome
  - fix paragraph links
  - add doi links to citation pages
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


### Git Commits

#### Lab Notebook

```bash
6489133 - Benjamin Lorentz, Tue Nov 8 15:26:44 2022 -0500 : added updates to term project progress
5f6d1e1 - Benjamin Lorentz, Tue Nov 8 12:44:31 2022 -0500 : updates for tuesday
e142335 - Benjamin Lorentz, Tue Nov 8 09:41:21 2022 -0500 : added page for tuesday
```

#### Gene-8950-Term-Paper

```bash
44b329f - Benjamin Lorentz, Tue Nov 8 16:49:56 2022 -0500 : malformed srr accession
4d49a38 - Benjamin Lorentz, Tue Nov 8 15:25:14 2022 -0500 : fixed accessions that were smashed together
a93f3ac - Benjamin Lorentz, Tue Nov 8 14:56:15 2022 -0500 : we do not need srr access
7094c04 - Benjamin Lorentz, Tue Nov 8 14:14:51 2022 -0500 : check if the directories exist before creating them
19636e3 - Benjamin Lorentz, Tue Nov 8 14:09:40 2022 -0500 : needed to update the galgal4cds var
cb663b1 - Benjamin Lorentz, Tue Nov 8 14:05:37 2022 -0500 : order metadata file, kallisto script set
df4d517 - Benjamin Lorentz, Tue Nov 8 13:55:54 2022 -0500 : removed kallisto and sleuth combo script
ddc4ad4 - Benjamin Lorentz, Tue Nov 8 13:55:12 2022 -0500 : added todos to sleuth analysis.r
3720172 - Benjamin Lorentz, Tue Nov 8 13:53:01 2022 -0500 : separate kallisto and sleuth because of directory structure
edc4e48 - Benjamin Lorentz, Tue Nov 8 13:44:30 2022 -0500 : added skeleon for analysis and sleuth analysis
196a292 - Benjamin Lorentz, Tue Nov 8 13:38:48 2022 -0500 : moved the metadata creation yaml file
971e7bb - Benjamin Joseph Lorentz, Tue Nov 8 13:33:02 2022 -0500 : updated fastqc environment file
b87d1f8 - Benjamin Lorentz, Tue Nov 8 13:22:00 2022 -0500 : updated analysis to use conda as opposed to the module system
feae9df - Benjamin Lorentz, Tue Nov 8 13:01:16 2022 -0500 : added command to download the reference CDS from Ensemble
d2f51ad - Benjamin Lorentz, Tue Nov 8 12:58:21 2022 -0500 : update readme and add script to run kallisto
```

#### Host-Microbe-Interaction-Protein

```bash
e9e56d5 - Benjamin Lorentz, Tue Nov 8 16:43:57 2022 -0500 : update definitions links
f7af819 - Benjamin Lorentz, Tue Nov 8 16:26:48 2022 -0500 : trying to use a html link
cb3d56c - Benjamin Lorentz, Tue Nov 8 16:23:15 2022 -0500 : updated first definition
d872f11 - Benjamin Lorentz, Tue Nov 8 16:22:10 2022 -0500 : have fixed the links in bigqs
0678d41 - Benjamin Lorentz, Tue Nov 8 16:13:03 2022 -0500 : fixed stomach links
4268954 - Benjamin Lorentz, Tue Nov 8 16:11:07 2022 -0500 : updated small intestine doc
7daf644 - Benjamin Lorentz, Tue Nov 8 16:03:42 2022 -0500 : update liver links
679ca24 - Benjamin Lorentz, Tue Nov 8 15:51:37 2022 -0500 : add the forward slash before the citations
336cfed - Benjamin Lorentz, Tue Nov 8 15:49:59 2022 -0500 : updated links in ceca
b638205 - Benjamin Lorentz, Tue Nov 8 11:46:59 2022 -0500 : made the index links larger
dd2c176 - Benjamin Lorentz, Tue Nov 8 11:31:17 2022 -0500 : correct definition links
53febe9 - Benjamin Lorentz, Tue Nov 8 11:29:17 2022 -0500 : adding Links to the landing page
0e9a817 - Benjamin Lorentz, Tue Nov 8 11:25:42 2022 -0500 : unpaired braces
71d9211 - Benjamin Lorentz, Tue Nov 8 11:23:59 2022 -0500 : inded html not R
c323750 - Benjamin Lorentz, Tue Nov 8 11:12:11 2022 -0500 : use menu main instead of primary
3f50697 - Benjamin Lorentz, Tue Nov 8 11:04:38 2022 -0500 : modify menu main to menu primary
6310c7b - Benjamin Lorentz, Tue Nov 8 11:03:31 2022 -0500 : remove main menu
6d8d5f2 - Benjamin Lorentz, Tue Nov 8 11:01:03 2022 -0500 : add reference to index.html
7248088 - Benjamin Lorentz, Tue Nov 8 10:58:18 2022 -0500 : add index.html
6e43e5a - Benjamin Lorentz, Tue Nov 8 10:55:45 2022 -0500 : update config
8846303 - Benjamin Lorentz, Tue Nov 8 10:37:53 2022 -0500 : remove the formatting in config where the index is all the posts
64b85a3 - Benjamin Lorentz, Tue Nov 8 10:34:53 2022 -0500 : use _index to see
550e9bc - Benjamin Lorentz, Tue Nov 8 10:29:20 2022 -0500 : add home
eb4e19e - Benjamin Lorentz, Tue Nov 8 10:28:12 2022 -0500 : changed permalinks
0a66243 - Benjamin Lorentz, Tue Nov 8 10:25:56 2022 -0500 : remove config.yaml
d968ef3 - Benjamin Lorentz, Tue Nov 8 10:25:32 2022 -0500 : added toml
cf78a1c - Benjamin Lorentz, Tue Nov 8 09:52:11 2022 -0500 : added definitions and gut segments
```

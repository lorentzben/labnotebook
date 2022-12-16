---
title: Ampliseq Depth
author: Ben Lorentz
date: '2022-10-26'
slug: ampliseq-depth
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- When is TAP due?
  - Nov 15th. 
- Look into classes for the Spring semester
- lecture for Thursday.
- continue reading jones
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running
- Collect reference genome and annotations.
- Shaile’s compare flip/flop

I want to, after watching the lecture for tomorrow, look into the ampliseq depth selection. After that I want to follow up on the multi qc analysis for my data. 

### Classes List

I made an excel sheet to track what my course list looks like. I have classes slated till 2029... Though I have no summer classes for the last 4-5 years, that means really digging into what kind of project work I want to do during the summer. This mapping does make me feel frustrated with how long this process might take. I just need to make sure I am doing the work to make it worthwhile by learning all the tools I can and integrating everything. 

### Life notes

I found the company ASTR where you work under them as a contractor to the CDC. You would be doing public health work and surveillance. One of the positions I found looks at genomic analysis of eukaryotic pathogens in clinical and animal samples, qc, assembly, annotations and analysis of isolate based genomic sequences. Develops WGS and wgMLST (what is this) tools. 

Present at conferences:
- Sequencing, Finishing, and Analysis in the Future
- ASM Conference on Rapid Applied Microbial NGS
- Bioinformatics Pipelines
- International Conference on Research in Computational Molec. Bio.
- International R User Conference 
- Oxford Nanopore User Group Meetings

So the things I would need to dig into a little more are Isolate NGS sequencing,etc. SQL & relational databases. 
Population genetics (Bensassen and Leebens-Mack). Ask Bergman about how he finds his datasets and develop a mini-project to showcase skills. 

One tool to learn is [BioSQL](https://biopython.org/wiki/BioSQL) as well as just [SQL](https://www.codecademy.com/learn/learn-sql) and [Mongo DB](https://www.codecademy.com/learn/learn-mongodb)
[Learn what linkml is](https://linkml.io/linkml/intro/tutorial.html) and then understand [Mixs](https://github.com/GenomicsStandardsConsortium/mixs)

### Linkml

I was working on the tutorial in the directory: /home/bjl34716/linkml-tutorial

What is it? A metadata creation tool (at least that's how I think I will approach it). I want to create a strong data collection and management.

Okay so its a yaml based framework to make data objects to store information. You can use python to [generate and manipulate objects](https://linkml.io/linkml/intro/tutorial05.html) following the schema. So all this does is make the tables that you intend to fill. This can be json objects you store in like a mongo db or it can generate tables for storage in a sql database, or somehow python can manipulate the objects it seems. It still doesn't have a front-end (without me building one) so I'm not 100% certain how useful it would be. I did come across [qiimp](https://qiita.ucsd.edu/qiimp/) which does have a front end and could be a little helpful? But this feels like an ongoing process. It might be good to try to catalog the Villegas, Shailes, and Ellestad-Rothrock Data that I have and use that as my basic SQL, monog-db example data. I spent a decent amount of time just figuring out how to understand what this whole schema thing is. I'm not sure I see deep value in going through this whole process but I feel like more documented data the better. 

### Todos for Tomorrow:

- Submit TAP for the stats class
- continue reading jones
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running
- Collect reference genome and annotations.
- Shaile’s compare flip/flop
- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
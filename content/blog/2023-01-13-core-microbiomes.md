---
title: 'Core Microbiomes'
date: 2023-01-13T14:05:21Z
draft: true
meta_img: "images/image.png"
tags:
  - "core microbiome"
  - "mock communities"
description: "Description for the page"
---

### Todos for Today:

- Go Back to the Original question from Aggrey (from 8-22-22)
  - Explained to Dr. Aggrey my progress on papers
  - He suggested I begin by characterizing the taxa present in each gut segment
  - Then see what functional data we have for those and see what substrates will make it to the end 
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Examine some papers collected


I want to examine the exact results these papers to see if they identify taxonomy, I could go in myself and try to re-create what the authors have identified.

Things to examine:
  - taxa based on shotgun sequences
  - function based on shotgun sequences
  - metabolic function (based on those functionality) when taxa are supplied ? A hacky picrust alternative
  - A metabolomics catalog for chicken
    - metabolytes of interest for protien/ nitrogen maybe a third way to measure them.
    
Things we have:
  - annotated chicken genome
  - a chicken transcriptome (https://pubmed.ncbi.nlm.nih.gov/34276773/)
  - a set of metagenomic assembled genomes (bacteria that live in the chicken gut in multiple segments) 10.1093/gigascience/giac116

Can we find:
  - a chicken gut proteome (what proteins the bacteria are making) https://pubmed.ncbi.nlm.nih.gov/24212578/
  - a chicken gut metabolome (what substrates are being acted on in the gut?) https://link.springer.com/article/10.1007/s11306-016-1105-7

Is it helpful to screen out common functions for players or to look at the magnitude of their capacity to characterize them?

Let's Follow the Central Dogma 

### Options to explore

Short read catalogs: 
- Huang 2018 ~9 million genes from 495 chicken from 7 farms
- Glendinning 2020 469 MAGS from 24 chickens
- Segura-Wang 2021 155 MAGS from 751 chicken
- Gilroy 2021 5,595 MAGS from 632 chicken
- Feng 12,339 MAGs integrating 799 chicken samples from 10 countries

Long Reads:
- Zhang 2022 150 samples from 5 compartments (duodenum, jejunum, ileum, cecum, and colorectum) of 30 chickens

This paper https://www.nature.com/articles/s42003-021-02827-2 gives a good overview of how to approach the process when I have more shotgun reads. 

### Summarize the Zhang MAGs Catalog

- Huang 2018 ~9 million genes from 495 chicken from 7 farms
- ftp://ftp.agis.org.cn/∼fanwei/Chicken_gut_metagenome_ Hifi/

Readme from the Zhang Paper

```md
[Title] Supporting data for "Improved microbial genomes and gene catalog of chicken gut from metagenome sequencing  of high-fidelity long reads"

Summary:
-------------
    We collected 150 digesta samples from the five intestinal compartments (duodenum, jejunum, 
    ileum, cecum, and colorectum) of 30 chickens (Lingnan yellow broilers)  slaughtered on day 42, 
    extracted the DNA separately for each sample, and combined the DNA samples from 30 chicken 
    individuals and constructed sequencing libraries for each intestinal compartment. Then, we  
    generated 22 Gb, 45 Gb, 73 Gb, 81 Gb, 112 Gb PacBio HiFi reads for duodenum, jejunum, ileum, 
    cecum, and colorectum, respectively (Table 1). For the total 332 Gb HiFi reads, the N50 read length 
    is 17 Kb, and the median read quality value is 32. Then, we assembled 461 microbial genomes at 
    strain level (ANI 99%) and 369 microbial genomes at species level (ANI 95%), of which 246 (53%) 
    and 209 (57%) are circular genomes, respectively, using high-fidelity long reads of the five intestinal 
    compartments of chickens. Among the 461 genomes, 439 (95%) genomes are “RNA complete” 
    which meets the criteria of having at least one full-length rRNA of all three types and at least 18 
    copies of full-length tRNA genes.

Files:
--------
01.assembled_contigs:
    01.assembled_contigs/Cecum.out.p_ctg.gfa.seq.fa.gz - Assembled contigs of cecum by hifiasm-meta
    01.assembled_contigs/Cecum.out.p_ctg.noseq.gfa - GFA  files of cecum by hifiasm-meta, can view with software Bandage
    01.assembled_contigs/Duodenum.out.p_ctg.gfa.seq.fa.gz - Assembled contigs of duodenum by hifiasm-meta
    01.assembled_contigs/Duodenum.out.p_ctg.noseq.gfa - GFA  files of duodenum by hifiasm-meta, can view with software Bandage
    01.assembled_contigs/Ileum.out.p_ctg.gfa.seq.fa.gz - Assembed contigs of ileum by hifiasm-meta
    01.assembled_contigs/Ileum.out.p_ctg.noseq.gfa - GFA  files of ileum by hifiasm-meta, can view with software Bandage
    01.assembled_contigs/jejunum.out.p_ctg.gfa.seq.fa.gz - Assembled contigs of jejunum by hifiasm-meta
    01.assembled_contigs/jejunum.out.p_ctg.noseq.gfa - GFA  files of jejunum by hifiasm-meta, can view with software Bandage
    01.assembled_contigs/Rectum.out.p_ctg.gfa.seq.fa.gz - Assembled contigs of colorectum by hifiasm-meta
    01.assembled_contigs/Rectum.out.p_ctg.noseq.gfa - GFA  files of colorectum by hifiasm-meta, can view with software Bandage

02.microbial_genomes:
    02.microbial_genomes/Cecum.microbial.genomes.summary.xls - Charateristics of all MAGs from cecum, including genome size, sequencing depth, checkm value, and GTDB-tk taxonomy
    02.microbial_genomes/Cecum.microbial.genomes.tar.gz - Fasta sequences of all MAGs from cecum
    02.microbial_genomes/Duodenum.microbial.genomes.summary.xls - Charateristics of all MAGs from duodenum, including genome size, sequencing depth, checkm value, and GTDB-tk taxonomy
    02.microbial_genomes/Duodenum.microbial.genomes.tar.gz - Fasta sequences of all MAGs from duodenum
    02.microbial_genomes/Ileum.microbial.genomes.summary.xls - Charateristics of all MAGs from ileum, including genome size, sequencing depth, checkm value, and GTDB-tk taxonomy
    02.microbial_genomes/Ileum.microbial.genomes.tar.gz - Fasta sequences of all MAGs from ileum
    02.microbial_genomes/jejunum.microbial.genomes.summary.xls - Charateristics of all MAGs from jejunum, including genome size, sequencing depth, checkm value, and GTDB-tk taxonomy
    02.microbial_genomes/Jejunum.microbial.genomes.tar.gz - Fasta sequences of all MAGs from jejunum
    02.microbial_genomes/Rectum.microbial.genomes.summary.xls - Charateristics of all MAGs from colorectum, including genome size, sequencing depth, checkm value, and GTDB-tk taxonomy
    02.microbial_genomes/Rectum.microbial.genomes.tar.gz - Fasta sequences of all MAGs from colorectum

03.microbial_genomes_nr:
    03.microbial_genomes_nr/Intestinal.microbial.genomes.species.ANI95.summary.nr.xls - Charateristics of non-redundant MAGs (dereplicated with 95% ANI value), including genome size, sequencing depth, checkm value, and GTDB-tk taxonomy
    03.microbial_genomes_nr/Intestinal.microbial.genomes.species.ANI95.tar.gz - Fasta sequences of non-redundant MAGs (dereplicated with 95% ANI value)
    03.microbial_genomes_nr/Intestinal.microbial.genomes.strains.ANI99.annotated.genes.tar.gz - Fasta sequences of non-redundant MAGs (dereplicated with 99% ANI value)
    03.microbial_genomes_nr/Intestinal.microbial.genomes.strains.ANI99.annotated.rRNAs.tar.gz - Predicted rRNA sequences of non-redundant MAGs (dereplicated with 99% ANI value)
    03.microbial_genomes_nr/Intestinal.microbial.genomes.strains.ANI99.annotated.tRNAs.tar.gz - Predicted tRNA sequences of non-redundant MAGs (dereplicated with 99% ANI value)
    03.microbial_genomes_nr/Intestinal.microbial.genomes.strains.ANI99.summary.nr.xls - Charateristics of non-redundant MAGs (dereplicated with 99% ANI value), including genome size, sequencing depth, checkm value, and GTDB-tk taxonomy
    03.microbial_genomes_nr/Intestinal.microbial.genomes.strains.ANI99.tar.gz - Fasta sequences of non-redundant MAGs (dereplicated with 99% ANI value)

04.gene_catalog_nr:
    04.gene_catalog_nr/Chicken_five_gut_segment.combined.nr.identity95.overlap90.nr.fa.gz - Fasta sequences of the non-redundant gene catalog from all five gut segment (cds sequences)
    04.gene_catalog_nr/Chicken_five_gut_segment.combined.nr.identity95.overlap90.nr.fa.len - Length of each gene sequence in the non-redundant gene catalog 
    04.gene_catalog_nr/Chicken_five_gut_segment.combined.nr.identity95.overlap90.nr.fa.len.stat - Length statment of all gene sequences in the non-redundant gene catalog

05.plasmid_and_virus:
    05.plasmid_and_virus/Cecum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving.fa - Circular sequences of plasmid and virus from cecum
    05.plasmid_and_virus/Cecum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving_result_table.csv - Results from ViralVerify of the circular sequences from cecum
    05.plasmid_and_virus/Duodenum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving.fa - Circular sequences of plasmid and virus from duodenum
    05.plasmid_and_virus/Duodenum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving_result_table.csv - Results from ViralVerify of the circular sequences from duodenum
    05.plasmid_and_virus/Ileum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving.fa - Circular sequences of plasmid and virus from ileum
    05.plasmid_and_virus/Ileum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving_result_table.csv - Results from ViralVerify of the circular sequences from ileum
    05.plasmid_and_virus/jejunum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving.fa - Circular sequences of plasmid and virus from jejunum
    05.plasmid_and_virus/jejunum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving_result_table.csv - Results from ViralVerify of the circular sequences from jejunum
    05.plasmid_and_virus/Rectum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving.fa - Circular sequences of plasmid and virus from colorectum
    05.plasmid_and_virus/Rectum.out.p_ctg.gfa.seq.fa.len.circular.fa.leaving_result_table.csv - Results from ViralVerify of the circular sequences from colorectum

06_Graphlan_Plot:
    06_Graphlan_Plot/01_Figure_7_Data/run.sh - Running shell for Graphlan
    06_Graphlan_Plot/01_Figure_7_Data/zcomb_checkm_taxa.txt.anno.txt - Annotation file for drawing graphlan plot figure          
    06_Graphlan_Plot/01_Figure_7_Data/zcomb_checkm_taxa.txt.basedata.txt - Input_tree file for drawing graphlan plot figure         
    06_Graphlan_Plot/01_Figure_7_Data/zcomb_checkm_taxa.txt.basedata.txt.xml - Output file from Graphlan (in PhyloXML format)      
    06_Graphlan_Plot/02_Sup_Fig_S4/Cecum.microbial.genomes.summary.xls.comb.anno.txt - Annotation file for drawing graphlan plot figure       
    06_Graphlan_Plot/02_Sup_Fig_S4/Cecum.microbial.genomes.summary.xls.comb.basedata.txt - Input_tree file for drawing graphlan plot figure   
    06_Graphlan_Plot/02_Sup_Fig_S4/Cecum.microbial.genomes.summary.xls.comb.basedata.txt.xml - Output file from Graphlan (in PhyloXML format)      
    06_Graphlan_Plot/02_Sup_Fig_S4/Duodenum.microbial.genomes.summary.xls.comb.anno.txt - Annotation file for drawing graphlan plot figure      
    06_Graphlan_Plot/02_Sup_Fig_S4/Duodenum.microbial.genomes.summary.xls.comb.basedata.txt - Input_tree file for drawing graphlan plot figure  
    06_Graphlan_Plot/02_Sup_Fig_S4/Duodenum.microbial.genomes.summary.xls.comb.basedata.txt.xml - Output file from Graphlan (in PhyloXML format)      
    06_Graphlan_Plot/02_Sup_Fig_S4/Ileum.microbial.genomes.summary.xls.comb.anno.txt - Annotation file for drawing graphlan plot figure       
    06_Graphlan_Plot/02_Sup_Fig_S4/Ileum.microbial.genomes.summary.xls.comb.basedata.txt - Input_tree file for drawing graphlan plot figure          
    06_Graphlan_Plot/02_Sup_Fig_S4/Ileum.microbial.genomes.summary.xls.comb.basedata.txt.xml - Output file from Graphlan (in PhyloXML format)        
    06_Graphlan_Plot/02_Sup_Fig_S4/jejunum.microbial.genomes.summary.xls.comb.anno.txt - Annotation file for drawing graphlan plot figure         
    06_Graphlan_Plot/02_Sup_Fig_S4/jejunum.microbial.genomes.summary.xls.comb.basedata.txt - Input_tree file for drawing graphlan plot figure       
    06_Graphlan_Plot/02_Sup_Fig_S4/jejunum.microbial.genomes.summary.xls.comb.basedata.txt.xml - Output file from Graphlan (in PhyloXML format)        
    06_Graphlan_Plot/02_Sup_Fig_S4/Rectum.microbial.genomes.summary.xls.comb.anno.txt - Annotation file for drawing graphlan plot figure        
    06_Graphlan_Plot/02_Sup_Fig_S4/Rectum.microbial.genomes.summary.xls.comb.basedata.txt - Input_tree file for drawing graphlan plot figure        
    06_Graphlan_Plot/02_Sup_Fig_S4/Rectum.microbial.genomes.summary.xls.comb.basedata.txt.xml - Output file from Graphlan (in PhyloXML format) 
    06_Graphlan_Plot/02_Sup_Fig_S4/run.sh - Running shell of five gut segment for Graphlan
```

Can we filter and dereplicate each tissue one by one? This way I can use each tissue as a separate catalog, we don't need to, we can just pull out of the NR databases, either species or strain. This is sick.

I want to take a look at all of the databases that I have listed above and can we make some kind of PCA or something to show how similar or different the communities are?

### Todos for Next Week:

- Examine all MAGs uncovered
  - Summarize major players in each segment 
  - Summarize gene content in each segment
  - Figure out how to present this to Dr. Aggrey
- Go Back to the Original question from Aggrey (from 8-22-22)
  - Explained to Dr. Aggrey my progress on papers
  - He suggested I begin by characterizing the taxa present in each gut segment
  - Then see what functional data we have for those and see what substrates will make it to the end 
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
- Examine some papers collected
---
title: 'Send Something to Ade'
date: 2023-03-31T12:54:12Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "negative control"
  - "positive control"
  - "visualize-ampliseq"
description: "Description for the page"
---

### Todos for Today

- Class
  - Meet and discuss
- Jackwood Blast
  - Go to Ben's Defense @ 1pm
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Ade

#### Recreate ordinations with NMDS by hand (BC)

I want to see what the ordination looks like when you use NMDS. One thing I might have noticed is that the plot is based off the qiime results as opposed to the table I have created which may be wrong, aka it is looking at a very subset version (4 in this case).

Let's compare the qiime bray and my bray, the first problem is that the table in the dir is the non-rarefied one.

From this site: [Cancer NIH](https://btep.ccr.cancer.gov/docs/qiime2/Lesson5/)
"Note: you may want to skip rarefaction if library sizes are fairly even. Rarefaction is more beneficial when there is a greater than ~10x difference in library size (Weiss et al. 2017)."

I dug into the qiime source code and they do use the rarefied table. So I want to pull that one in and compare to the qiime table. 

```r 

#in "/scratch/bjl34716/ade/cycle-4/work/23/2c9ff2ef62e6e595ec6ad135bbe0b4"
rooted_tree <- "results/qiime2/phylogenetic_tree/rooted-tree.qza"
taxonomy_file <- "taxonomy.qza"
metadata_file <- "metadata.tsv"
table_dada2 <- "rarefied_table.qza"

metadata<-read_q2metadata(metadata_file)

metadata[[ioi]] <- factor(metadata[[ioi]], levels=ioi_ord)
cycle_1 <- qza_to_phyloseq(table_dada2,rooted_tree,taxonomy_file,metadata_file) 

> colSums(otu_table(cycle_1))
LT100 LT101 LT102 LT103 LT104 LT106 LT107 LT108 LT109 LT110 LT111 LT112 LT113
16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589
LT114 LT115 LT117 LT118 LT119 LT120  LT74  LT75  LT76  LT77  LT78  LT79  LT80
16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589
 LT81  LT82  LT84  LT85  LT86  LT87  LT88  LT89  LT90  LT91  LT92  LT93  LT95
16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589 16589
 LT98  LT99
16589 16589
# correct

ord <- ordinate(cycle_1, "NMDS", "bray")

> ord

Call:
metaMDS(comm = veganifyOTU(physeq), distance = distance)

global Multidimensional Scaling using monoMDS

Data:     wisconsin(sqrt(veganifyOTU(physeq)))
Distance: bray

Dimensions: 2
Stress:     0.1172569
Stress type 1, weak ties
No convergent solutions - best solution after 20 tries
Scaling: centring, PC rotation, halfchange scaling
Species: expanded scores based on ‘wisconsin(sqrt(veganifyOTU(physeq)))’

p2 = plot_ordination(cycle_1, ord, type="samples", color='Treatment')

ggsave(filename='treatment_bray_nmds.png',plot=p2)

p3 = p2 + geom_polygon(aes(fill=Treatment)

ggsave(filename='treatment_bray_nmds_shape.png',plot=p3)

### Looking to see the old table/what we lose in taxa

> table_dada2 <- "feature-table.qza"
> cycle_2 <- qza_to_phyloseq(table_dada2,rooted_tree,taxonomy_file,metadata_file)
> cycle_2
phyloseq-class experiment-level object
otu_table()   OTU Table:         [ 1040 taxa and 47 samples ]
sample_data() Sample Data:       [ 47 samples by 5 sample variables ]
tax_table()   Taxonomy Table:    [ 1040 taxa by 7 taxonomic ranks ]
phy_tree()    Phylogenetic Tree: [ 1040 tips and 1037 internal nodes ]
> colSums(otu_table(cycle_2))
 LT100  LT101  LT102  LT103  LT104  LT105  LT106  LT107  LT108  LT109  LT110
 48746  66405  48401  48539  41517     96  60333  43099  63962  54520  44780
 LT111  LT112  LT113  LT114  LT115  LT116  LT117  LT118  LT119  LT120   LT73
 56839  64728  94560 100639  59086  16509  45220  51688  40942  52908      5
  LT74   LT75   LT76   LT77   LT78   LT79   LT80   LT81   LT82   LT83   LT84
 31748  21837  33615  29848  30543  23055  28649  19470  24674      4  26625
  LT85   LT86   LT87   LT88   LT89   LT90   LT91   LT92   LT93   LT95   LT96
 51316  47702  59751  45944  63414  35689  40697  35294  52495  52158   2857
  LT97   LT98   LT99
    28  54464  64066
    
> largest <- max(colSums(otu_table(cycle_2)))
> my_rare <- 16589


> largest/my_rare
[1] 6.06661

#6x difference
```

Okay so the plots kinda look the same...
Should we try to use [SRS](https://github.com/vitorheidrich/SRS) to transform the table as opposed to rarefy it?

### What does an SRS table look like?

I generated a SRS docker image and am working on implementing it as a form for normalization. 


### Multi-qc

We should remove these samples, they did not undergo PCR correctly or there was sequencing errors.

```bash
LT83_2	13.2%	55%	0.0
LT73_2	15.2%	56%	0.0
LT97_2	32.7%	54%	0.0
LT105_2	33.5%	51%	0.0
LT83_1	44.7%	54%	0.0
LT73_1	45.5%	54%	0.0
LT105_1	57.0%	50%	0.0
LT97_1	61.2%	52%	0.0
LT96_2	88.8%	56%	0.0
LT96_1	92.2%	55%	0.0
```

cycle 4 rev: e4229618f46863f33d516d798ebee917fb3f85c7
visualize ampliseq rev: 6282c8ec40a4cd89d11c552b5eb7b14c41ad4e77
slurm job: 20477067

```bash
```

#### What does reddit and NIH suggest?

They suggest rarefying it, but I am not super satisfied by that.

#### Contam Downstream


### Todos for Next Week

- Class
  - Examine Comments on Word Doc
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Examine HQ analysis
  - Examine How SRS changes result vs rarefying
  - Fix Downstream Uses of table with filtered
  - Fix the rarefaction script to use the qiime ASV table and alt filtered table
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Git Commits

#### Lab Notebook

```bash
f7aaee1 - Ben Lorentz, Fri Mar 31 16:56:28 2023 -0400 : most notes for fri
3723554 - Ben Lorentz, Fri Mar 31 16:49:06 2023 -0400 : poor quality samples
cd63def - Benjamin Lorentz, Fri Mar 31 12:34:50 2023 -0400 : added notes before Bens Defense
9a91432 - Ben Lorentz, Fri Mar 31 08:56:00 2023 -0400 : add page for friday
e04803f - Ben Lorentz, Thu Mar 30 21:41:45 2023 -0400 : final notes for today
53e5966 - Ben Lorentz, Thu Mar 30 19:30:14 2023 -0400 : added some more notes
5399431 - Ben Lorentz, Thu Mar 30 17:42:20 2023 -0400 : first note from at home
ba070b5 - Benjamin Lorentz, Thu Mar 30 17:05:25 2023 -0400 : final notes for Thursday
```

#### Cycle 4 

```bash
e422961 - Ben Lorentz, Fri Mar 31 16:45:41 2023 -0400 : add files for HQ analysis
f527258 - Ben Lorentz, Fri Mar 31 14:53:46 2023 -0400 : remove one whitespace
bb9b63b - Ben Lorentz, Thu Mar 30 19:26:28 2023 -0400 : update the vis params
d4a9419 - Ben Lorentz, Thu Mar 30 19:22:26 2023 -0400 : update params file
b8c6d97 - Ben Lorentz, Thu Mar 30 17:38:39 2023 -0400 : Update driver script
```

#### Visualize Ampliseq

```bash
eef8f7d - Ben Lorentz, Fri Mar 31 16:22:25 2023 -0400 : add dockefile and renv for srs docker
```


---
title: visualize ampliseq, unzip diversity matricies
author: Ben Lorentz
date: '2022-11-22'
slug: visualize-ampliseq-unzip-diversity-matricies
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Check in on Medium Richness analysis
- Run the data through DESeq after samtools(?) or alignment.
- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- Re-Run the low med high analyses
  - Run Visualize Ampliseq
    - on low med high richness samples
- re-watch the lecture for ChIP-seq
- Check in on classifier still running

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca


### Visualize Ampliseq

I added a process to uncompress the diversity metric qzas and export them as TSV files. I then updated the scripts paths, and have started the analysis on sapelo2.

I re-submitted the job:
slurm 15474870
revision: a0c7be6811d7624ca00ea53203f4a3820b24b110

```bash

```

### Term Paper

#### HTSeq results

HTSeq finished successfully but since I did not write the table out to file, I have to manually attach the filenames to the counts. To fix this in the future I piped the data out to file and saved the bam filenames to file too.

Based on what I am seeing from bam counts to outputs, I believe the data is stranded so I am re-running htseq-counts again with the stranded flag

slurm:  32753
revision: dd319da5bdaa3f8c6cc8df47163d5caadd734e10

```bash

```


#### Star results compared to HTSeq

Bam Results From Star

```bash
*Aligned.sortedByCoord.out.bam

SRR8265548	7274162
SRR8265549	9482888
SRR8265550	7228413
SRR8265553	7136724
SRR8265554	9900991
SRR8265555	20676948
SRR8265556	15694760
SRR8265557	8685256
SRR8265558	11889495
SRR8265559	6031697
SRR8265560	5558186
SRR8265561	11561222
SRR8265562	10065574
SRR8265591	13040996
SRR8265592	4809951
SRR8265593	7785741
SRR8265594	8385284
SRR8265595	9720168
SRR8265596	9891482
SRR8265597	9933836
SRR8265598	9653543
SRR8265599	8093441
SRR8265600	8877748
SRR8265611	6816258
SRR8265612	9937460
SRR8265613	12440752
SRR8265614	9004846
SRR8265615	11907341
SRR8265616	6698072
SRR8265617	3872268
SRR8265618	6195834
SRR8265619	9070427
SRR8265620	18142520
SRR8265621	5902484
SRR8265622	10836800
SRR8265623	16012002
SRR8265624	7923908
SRR8265625	15870276
SRR8265626	9375276
SRR8265627	5459306
SRR8265628	7737658
SRR8265629	11066160
SRR8265630	7556032
SRR8265631	7411850
SRR8265632	10960368
SRR8265633	14104963
SRR8265634	17144132
SRR8265635	11380361
SRR8265636	9473475
SRR8265637	5879663
SRR8265638	6828362
SRR8265639	11390710
SRR8265640	16151774
SRR8265651	8309784
SRR8265652	9212919
SRR8265653	10723092
SRR8265654	9444480
SRR8265655	9974809
SRR8265656	7882818
SRR8265657	9130718
SRR8265658	8800128
SRR8265659	8636059
SRR8265660	12945730
```

Sum of recovered features by HTSeq

```bash
SRR8265548	2502453
SRR8265549	3045008
SRR8265550	2510114
SRR8265553	2779690
SRR8265554	3889834
SRR8265555	8069813
SRR8265556	6098785
SRR8265557	2797380
SRR8265558	4531590
SRR8265559	2209577
SRR8265560	1853480
SRR8265561	3895496
SRR8265562	3549166
SRR8265591	2290018
SRR8265592	1666118
SRR8265593	2818050
SRR8265594	2829217
SRR8265595	3277129
SRR8265596	3483267
SRR8265597	3317317
SRR8265598	3603634
SRR8265599	2674373
SRR8265600	3023668
SRR8265611	2807106
SRR8265612	3941806
SRR8265613	4506569
SRR8265614	3707230
SRR8265615	4575013
SRR8265616	2596609
SRR8265617	313659
SRR8265618	2477104
SRR8265619	3552791
SRR8265620	7067840
SRR8265621	2028012
SRR8265622	3584621
SRR8265623	5316465
SRR8265624	2198435
SRR8265625	2535516
SRR8265626	2804269
SRR8265627	1366459
SRR8265628	2662245
SRR8265629	3765043
SRR8265630	2171331
SRR8265631	2601825
SRR8265632	3815993
SRR8265633	4925659
SRR8265634	6293027
SRR8265635	3996523
SRR8265636	3324421
SRR8265637	2044604
SRR8265638	2340246
SRR8265639	4179190
SRR8265640	5739578
SRR8265651	2880335
SRR8265652	3206023
SRR8265653	3125905
SRR8265654	2918313
SRR8265655	3417027
SRR8265656	2733871
SRR8265657	3165846
SRR8265658	3079885
SRR8265659	2663606
SRR8265660	4404736
```

When looking at features recovered (Sum of featues in sample/Number of aligned reads in bamfile)

```bash
 min  median   max
8.10%	34.68%	41.18%
```

This suggests to me that the data is stranded, to be confirmed by the star run.


### Classifier

The classifier timed out after 30 days, is there a way we can speed up the process with more cores?

### Todos for Next Week:

- Examine htseq-count results slurm 32753
  - do we have to use --stranded reverse
- rebuild the supplemental tables 1-5 with my results
- Run DESeq2 analysis on htseq-count table
- Visualize Ampliseq
  - examine slurm run 15474870
  
  
---

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- re-watch the lecture for ChIP-seq

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca

### Git Commits

#### Lab Notebook

```bash
e38ecd7 - Benjamin Lorentz, Tue Nov 22 16:16:32 2022 -0500 : updates about visualize ampliseq
0325494 - Benjamin Lorentz, Tue Nov 22 11:11:23 2022 -0500 : added page for tuesday
26ae1a7 - Benjamin Lorentz, Mon Nov 21 16:45:44 2022 -0500 : added some background for the visualize ampliseq issue
af76d29 - Benjamin Lorentz, Mon Nov 21 16:33:04 2022 -0500 : added notes as to how I solved the ID join
```

#### Visualize Ampliseq

```bash
a0c7be6 - Benjamin Lorentz, Tue Nov 22 16:14:56 2022 -0500 : update paths in 10 report
186941a - Benjamin Lorentz, Tue Nov 22 15:07:54 2022 -0500 : added script for uncompress diversity and porcess
```

#### Ampliseq Benchmark

```bash
e30e261 - Benjamin Lorentz, Tue Nov 22 16:21:43 2022 -0500 : comment out the analysis for medium to run more quickly
```

#### Term paper

```bash
dd319da - Benjamin Lorentz, Tue Nov 22 10:48:29 2022 -0500 : tell htseq that the data was stranded
5034e19 - Benjamin Lorentz, Tue Nov 22 10:12:12 2022 -0500 : added output to file, removed num cpus
dbc9c14 - Benjamin Lorentz, Tue Nov 22 09:51:38 2022 -0500 : re-order parameters again
7931573 - Benjamin Lorentz, Tue Nov 22 09:42:20 2022 -0500 : move the params around
ca0bdca - Benjamin Lorentz, Tue Nov 22 09:37:24 2022 -0500 : write the count table to file
2451d92 - Benjamin Lorentz, Mon Nov 21 16:30:27 2022 -0500 : add conda env file, make sure to use Renv to restore projec
t
7dc6ccd - Benjamin Lorentz, Mon Nov 21 16:25:15 2022 -0500 : added common deg results
da490eb - Benjamin Lorentz, Mon Nov 21 16:24:31 2022 -0500 : add common DEG results tables
```

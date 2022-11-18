---
title: Continue to test Visualize Ampliseq
author: Ben Lorentz
date: '2022-11-18'
slug: continue-to-test-visualize-ampliseq
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

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

#### Low Richness


#### Medium Richness

The analysis ran sucessfully, so I added the visualize amplise run right after and submitted it

slurm 15427624
revision: 0826a4b0ffa2f08532eb8633a36696aa3dd0d9b1

```bash
No such file: /scratch/bjl34716/nf_dev/ampliseq-benchmark/med_richness

No such file: /scratch/bjl34716/nf_dev/ampliseq-benchmark/med_richness/balanced_rich_metadata.tsv
```

I had to change med_richness to medium_richness

slurm 15428845
revision f030c1686f07a5fe83c07f741285de6a6ef53d1f 

```bash

```


### Term Paper

#### HTSeq Results

I should have checked my results from STAR earlier, I think I am missing a sample

fastqs in:
```bash
-rw-r--r--. 1 bjl34716 gene8940_class  421190794 Nov  1 10:21 data/SRR8265548_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  519691875 Oct 25 12:45 data/SRR8265549_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  419938946 Oct 25 12:52 data/SRR8265550_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  345333547 Oct 25 12:59 data/SRR8265553_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  541437194 Oct 25 13:08 data/SRR8265554_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class 1177360814 Oct 25 13:28 data/SRR8265555_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  789736969 Oct 25 13:43 data/SRR8265556_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  450209419 Oct 25 13:50 data/SRR8265557_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  629031730 Oct 25 14:02 data/SRR8265558_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  281813437 Oct 25 14:06 data/SRR8265559_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  253000914 Oct 25 14:10 data/SRR8265560_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  626657065 Oct 25 14:22 data/SRR8265561_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  548687152 Oct 25 14:31 data/SRR8265562_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  545134465 Oct 25 14:40 data/SRR8265591_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  293621077 Oct 25 14:45 data/SRR8265592_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  435534762 Oct 25 14:52 data/SRR8265593_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  466291395 Oct 25 15:00 data/SRR8265594_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  543961735 Oct 25 15:10 data/SRR8265595_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  549690477 Oct 25 15:19 data/SRR8265596_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  553940245 Oct 25 15:29 data/SRR8265597_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  497701056 Oct 25 15:37 data/SRR8265598_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  451070161 Oct 25 15:44 data/SRR8265599_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  500158317 Oct 25 15:53 data/SRR8265600_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  317633856 Oct 25 15:58 data/SRR8265611_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  608542664 Oct 25 16:08 data/SRR8265612_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  530498882 Oct 25 16:16 data/SRR8265613_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  403630863 Oct 25 16:23 data/SRR8265614_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  608339082 Oct 25 16:34 data/SRR8265615_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  321896302 Oct 25 16:40 data/SRR8265616_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  226953581 Oct 25 16:44 data/SRR8265617_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  293178146 Oct 25 16:48 data/SRR8265618_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  475404833 Oct 25 16:56 data/SRR8265619_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class 1056667933 Oct 25 17:15 data/SRR8265620_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  357338678 Oct 25 17:21 data/SRR8265621_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  600434980 Oct 25 17:31 data/SRR8265622_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  896374305 Oct 25 17:47 data/SRR8265623_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  418683967 Oct 25 17:54 data/SRR8265624_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  512112976 Oct 25 18:03 data/SRR8265625_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  506621321 Oct 25 18:11 data/SRR8265626_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  319853540 Oct 25 18:16 data/SRR8265627_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  500636633 Oct 25 18:24 data/SRR8265628_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  608270249 Oct 25 18:35 data/SRR8265629_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  414785326 Oct 25 18:42 data/SRR8265630_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  417722110 Oct 25 18:50 data/SRR8265631_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  649625271 Oct 25 19:00 data/SRR8265632_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  800989838 Oct 25 19:15 data/SRR8265633_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  969715864 Oct 25 19:32 data/SRR8265634_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  635000671 Oct 25 19:43 data/SRR8265635_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  525232999 Oct 25 19:52 data/SRR8265636_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  302654269 Oct 25 19:58 data/SRR8265637_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  345628184 Oct 25 20:04 data/SRR8265638_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  653298005 Oct 25 20:16 data/SRR8265639_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  895200793 Oct 25 20:32 data/SRR8265640_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  500415548 Oct 25 20:40 data/SRR8265651_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  506627824 Oct 25 20:49 data/SRR8265652_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  579704246 Oct 25 20:59 data/SRR8265653_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  499409666 Oct 25 21:08 data/SRR8265654_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  592417681 Oct 25 21:18 data/SRR8265655_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  460028167 Oct 25 21:26 data/SRR8265656_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  537480544 Oct 25 21:35 data/SRR8265657_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  498996057 Oct 25 21:43 data/SRR8265658_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  471562875 Oct 25 21:52 data/SRR8265659_1.fastq.gz
-rw-r--r--. 1 bjl34716 gene8940_class  712330300 Oct 25 22:04 data/SRR8265660_1.fastq.gz
```

Bam Files out from STAR

```bash
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 19:00 data/bam_files/SRR8265549Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2021 Nov 15 16:26 data/bam_files/SRR8265550Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2017 Nov 15 21:08 data/bam_files/SRR8265553Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 18:27 data/bam_files/SRR8265554Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2025 Nov 15 21:17 data/bam_files/SRR8265555Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 18:34 data/bam_files/SRR8265556Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2019 Nov 15 19:32 data/bam_files/SRR8265557Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 16:58 data/bam_files/SRR8265558Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2017 Nov 15 19:37 data/bam_files/SRR8265559Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2016 Nov 15 17:03 data/bam_files/SRR8265560Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 19:44 data/bam_files/SRR8265561Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 17:09 data/bam_files/SRR8265562Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2024 Nov 15 19:05 data/bam_files/SRR8265591Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 17:36 data/bam_files/SRR8265592Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 20:15 data/bam_files/SRR8265593Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2021 Nov 15 17:41 data/bam_files/SRR8265594Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 20:20 data/bam_files/SRR8265595Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 17:46 data/bam_files/SRR8265596Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 20:26 data/bam_files/SRR8265597Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2018 Nov 15 17:50 data/bam_files/SRR8265598Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 20:30 data/bam_files/SRR8265599Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 17:55 data/bam_files/SRR8265600Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2013 Nov 15 21:20 data/bam_files/SRR8265611Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2019 Nov 15 18:38 data/bam_files/SRR8265612Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2016 Nov 15 21:24 data/bam_files/SRR8265613Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2015 Nov 15 18:41 data/bam_files/SRR8265614Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 21:29 data/bam_files/SRR8265615Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2018 Nov 15 18:44 data/bam_files/SRR8265616Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2011 Nov 15 21:34 data/bam_files/SRR8265617Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2014 Nov 15 18:46 data/bam_files/SRR8265618Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2019 Nov 15 21:37 data/bam_files/SRR8265619Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 18:56 data/bam_files/SRR8265620Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 16:30 data/bam_files/SRR8265621Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 19:11 data/bam_files/SRR8265622Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 16:38 data/bam_files/SRR8265623Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2018 Nov 15 19:13 data/bam_files/SRR8265624Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2023 Nov 15 16:43 data/bam_files/SRR8265625Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 19:18 data/bam_files/SRR8265626Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2018 Nov 15 16:47 data/bam_files/SRR8265627Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2021 Nov 15 19:23 data/bam_files/SRR8265628Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 16:53 data/bam_files/SRR8265629Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2017 Nov 15 19:26 data/bam_files/SRR8265630Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2021 Nov 15 18:08 data/bam_files/SRR8265631Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 20:50 data/bam_files/SRR8265632Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 17:18 data/bam_files/SRR8265633Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 19:54 data/bam_files/SRR8265634Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 17:24 data/bam_files/SRR8265635Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 19:58 data/bam_files/SRR8265636Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 17:27 data/bam_files/SRR8265637Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 20:01 data/bam_files/SRR8265638Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2023 Nov 15 17:33 data/bam_files/SRR8265639Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 20:10 data/bam_files/SRR8265640Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 20:55 data/bam_files/SRR8265651Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 18:13 data/bam_files/SRR8265652Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2019 Nov 15 20:36 data/bam_files/SRR8265653Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2019 Nov 15 18:00 data/bam_files/SRR8265654Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 21:00 data/bam_files/SRR8265655Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2023 Nov 15 18:18 data/bam_files/SRR8265656Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 21:05 data/bam_files/SRR8265657Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 18:23 data/bam_files/SRR8265658Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2020 Nov 15 18:04 data/bam_files/SRR8265659Log.final.out
-rw-r--r--. 1 bjl34716 gene8940_class 2022 Nov 15 20:44 data/bam_files/SRR8265660Log.final.out
```

logfile from star is /work/gene8940/bjl34716/log.32576

SRR8265548 is the missing sample, from the logfile:

```bash
        STAR --genomeDir /home/bjl34716/gene8940-term-paper/data/galgal4 --runThreadN 8 --readFilesIn SRR8265548_1.fastq.gz SRR8265548_2.fastq.gz --readFilesCommand gunzip -c --outFileNamePrefix /home/bjl34716/gene8940-term-paper/data/bam_files/SRR8265548 --outSAMtype BAM SortedByCoordinate
        STAR version: 2.7.10b   compiled: 2022-11-01T09:53:26-04:00 :/home/dobin/data/STAR/STARcode/STAR.master/source
Nov 15 16:18:49 ..... started STAR run
Nov 15 16:18:49 ..... loading genome
Nov 15 16:19:12 ..... started mapping

gzip: SRR8265548_2.fastq.gz: unexpected end of file
EXITING because of FATAL ERROR in reads input: quality string length is not equal to sequence length
@SRR8265548.3785902
GCTAAAATTTGAGCGAACCCGTCTCTGTTGCAAAAGAGTGGGATGACTTGCCAGTAGAGGTGAAAAGCCTACCGAGCTGGGTGATAGCTGGTTACCTGTCAAACGAATCTAAGTTCCCCCTTAACCCACCCC

SOLUTION: fix your fastq file

Nov 15 16:22:22 ...... FATAL ERROR, exiting
```

I have re-downloaded and extracted the fastq files, the number of records based on "@" don't quite match, but I want to try to run the analysis by hand to see if it errors out again, and then we can cull that sample. 


```bash
KILLED
```

This got killed, so I re-submitted the 4_run-star script:

slurm:  32668
revision: 2464f13c2d19d1978eadd1846aeef9d93a59ce02

```bash

```

HTSeq results
slurm job
revision

```bash

```

Alignment Result
slurm job
revision

```bash

```

#### Join Sleuth Results and Papers Supplementals


### Host Microbiome Interaction

I ingested the papers [Adhikari](/papers/adhikariEffectsHousingTypes2020), [Bhattacharya](/papers/bhattacharyaSupervisedMachineLearning2022), and [Blokker](/papers/blokkerEvaluationNovelPrecision2022) into this repo since they were not really directly related to the host microbiome project but were still interesting. 



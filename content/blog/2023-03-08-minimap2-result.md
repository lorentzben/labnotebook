---
title: 'Minimap2 Result'
date: 2023-03-08T15:53:48Z
draft: false
meta_img: "images/image.png"

description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### gg-catalog-nf

#### Samtools view

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: baa43921ad60d52048fb4842662f28e8668d9b57
slurm sub: 19742122

```bash

N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/gg-catalog-nf ...
 Fast-forward
Launching `https://github.com/lorentzben/gg-catalog-nf` [goofy_colden] DSL2 - revision: baa43921ad [main]
V I S U A L I Z E   P I P E L I N E
===================================
input    : /home/bjl34716/my_utils/gg-catalog/code/mapping.tsv
contam    : /home/bjl34716/my_utils/gg-catalog/code/contam.tsv
single_end : false
pacbio : true
iontorrent : false
extension : /*.fastq
metadata: /home/bjl34716/my_utils/gg-catalog/code/metadata.tsv
outdir   : results
profile : slurm,singularity

Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/JfZyomcroMRPy
executor >  slurm (43)
[ba/34a78b] process > FILTLONG (SRR19732514)         [100%] 7 of 7, cached: 7 ✔
[fa/898530] process > MINIMAP2_INDEX (1)             [100%] 1 of 1, cached: 1 ✔
[d1/8f1170] process > MINIMAP2_ALIGN (SRR19726169)   [100%] 7 of 7, cached: 7 ✔
[14/767973] process > SAMTOOLS_VIEW (SRR19736685)    [100%] 7 of 7 ✔
[0d/aa9835] process > SAMTOOLS_FASTQ (SRR19683890)   [100%] 7 of 7 ✔
[fe/5fbabf] process > SAMTOOLS_FASTA (SRR19736685)   [100%] 7 of 7 ✔
[20/4394fe] process > SEQKIT_STATS (SRR19726169)     [100%] 7 of 7, cached: 7 ✔
[bd/fde0b4] process > CSVTK_CONCAT (raw)             [100%] 1 of 1, cached: 1 ✔
[75/ead805] process > SEQKIT_STATS_FILT (SRR19732... [100%] 7 of 7, cached: 7 ✔
[f2/ad6f8c] process > CSVTK_CONCAT_FILT (filtlong)   [100%] 1 of 1, cached: 1 ✔
[b7/6f332b] process > SEQKIT_STATS_UNMAP (SRR1968... [100%] 21 of 21 ✔
[e5/9d3dc0] process > CSVTK_CONCAT_UNMAP (minimap)   [100%] 1 of 1 ✔
Completed at: 08-Mar-2023 02:00:33
Duration    : 8h 52m 23s
CPU hours   : 1097.1 (38.4% cached)
Succeeded   : 43
Cached      : 31

```


```bash

bjl34716@ss-sub3 code$ less /scratch/bjl34716/nf_dev/gg-catalog/work/f2/ad6f8cfc19b6b97753376d098933c6

file    format  type    num_seqs        sum_len min_len avg_len max_len Q1      Q2      Q3      sum_gap N50     Q20(%)  Q30(%)
SRR19726169.fastq.gz    FASTQ   DNA     516348  8512378786      2016    16485.7 44765   14341.0 15704.0 17869.0 0       16183
   99.21   98.07
SRR19683891.fastq.gz    FASTQ   DNA     2730287 22192490145     2000    8128.3  46626   4742.0  7160.0  10575.0 0       9776
    98.91   97.40
SRR15214153.fastq.gz    FASTQ   DNA     1965108 33312767376     2000    16952.1 52396   12960.0 15963.0 19852.0 0       17616
   98.03   95.27
SRR19732514.fastq.gz    FASTQ   DNA     2126922 35601162605     2006    16738.3 50018   14438.0 15918.0 18250.0 0       16470
   98.68   96.76
SRR19732729.fastq.gz    FASTQ   DNA     1914473 35535370004     2008    18561.4 50558   15000.0 17367.0 21045.0 0       18627
   98.26   95.90
SRR19736685.fastq.gz    FASTQ   DNA     4240693 72100323222     2000    17002.0 53591   14331.0 16109.0 18784.0 0       16851
   98.68   96.83
SRR19683890.fastq.gz    FASTQ   DNA     3896255 75237772044     2008    19310.3 63490   15551.0 18188.0 22018.0 0       19533
   98.28   95.85
   
bjl34716@ss-sub3 code$ less /scratch/bjl34716/nf_dev/gg-catalog/work/e5/9d3dc0867b7add613591eccdaf8faa/minimap.tsv

file    format  type    num_seqs        sum_len min_len avg_len max_len Q1      Q2      Q3      sum_gap N50     Q20(%)  Q30(%)
SRR19726169_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00
    0.00
SRR19683891_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00
    0.00
SRR19732729_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00
    0.00
SRR15214153_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00
    0.00
SRR19732514_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00
    0.00
SRR19736685_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00
    0.00
SRR19683890_1.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0       0.00
    0.00
SRR19683891_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0
       0.00    0.00
SRR19726169_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0
       0.00    0.00
SRR19732729_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0
       0.00    0.00
SRR15214153_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0
       0.00    0.00
SRR19736685_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0
       0.00    0.00
SRR19683890_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0
       0.00    0.00
SRR19732514_singleton.fastq.gz                  0       0       0       0.0     0       0.0     0.0     0.0     0       0
       0.00    0.00
SRR19726169_other.fastq.gz      FASTQ   DNA     516312  8511703069      2016    16485.6 44765   14341.0 15704.0 17869.0 0
       16183   99.21   98.07
SRR19683891_other.fastq.gz      FASTQ   DNA     2687401 22015314087     2000    8192.0  46626   4814.0  7237.0  10636.0 0
       9816    98.90   97.39
SRR15214153_other.fastq.gz      FASTQ   DNA     1964192 33298316466     2000    16952.7 52396   12961.0 15963.0 19853.0 0
       17616   98.03   95.27
SRR19732729_other.fastq.gz      FASTQ   DNA     1914271 35531147338     2008    18561.2 50558   15000.0 17367.0 21045.0 0
       18627   98.26   95.90
SRR19732514_other.fastq.gz      FASTQ   DNA     2126764 35598352645     2006    16738.3 50018   14438.0 15918.0 18250.0 0
       16470   98.68   96.76
SRR19736685_other.fastq.gz      FASTQ   DNA     4240352 72094033171     2000    17001.9 53591   14331.0 16108.0 18784.0 0
       16851   98.68   96.83
SRR19683890_other.fastq.gz      FASTQ   DNA     3895696 75225651438     2008    19309.9 63490   15551.0 18188.0 22018.0 0
       19533   98.28   95.85
```
  
This is cool, most of my reads are lining up with what the rearchers had the only thing is that the reads are not 1:1 with tissues right now. We can change this. 

#### Concat FASTQ reads by tissue 

cat SRR15214153.fastq SRR19732730.fastq > cecum.fastq

gg-catalog rev: 5a1fbe512c1f18dad9a5771dba821d0f1a598557
slurm job: 19758400

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - yes, but Need to confirm with cat samples
    - make cat metadata and mapping
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Git Commits

#### Lab notebook

```bash
b9946b2 - Benjamin Lorentz, Wed Mar 8 11:05:55 2023 -0500 : modify to bash
86b17fd - Benjamin Lorentz, Wed Mar 8 11:04:11 2023 -0500 : duh its the parens
5f6ac2f - Benjamin Lorentz, Wed Mar 8 10:57:52 2023 -0500 : change to md
2f130fb - Benjamin Lorentz, Wed Mar 8 10:57:02 2023 -0500 : just remove the tags
36351b5 - Benjamin Lorentz, Wed Mar 8 10:55:06 2023 -0500 : reset a new page
a1530ba - Benjamin Lorentz, Wed Mar 8 10:51:42 2023 -0500 : remove a tag?
a1c5db6 - Benjamin Lorentz, Wed Mar 8 10:48:07 2023 -0500 : updated for wednesday
b9c1c1c - Benjamin Lorentz, Wed Mar 8 10:44:13 2023 -0500 : added a table for minimapped reads
ead077e - Benjamin Lorentz, Wed Mar 8 10:43:45 2023 -0500 : added a table for minimapped reads
57806ab - Benjamin Lorentz, Wed Mar 8 09:29:50 2023 -0500 : added page for wednesday
b6bb24b - Benjamin Lorentz, Tue Mar 7 17:09:43 2023 -0500 : final notes for tuesday
```

#### gg-catalog

```bash
5a1fbe5 - Benjamin Lorentz, Wed Mar 8 16:45:41 2023 -0500 : add code 00_cat_samples.sh
```
---
title: 'Compare Minimap Separate or Join'
date: 2023-02-03T15:26:10Z
draft: false
meta_img: "images/image.png"
tags:
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - add in the isolate field into parser and output
  - meet with Ben to talk about two points above 2/2/23
- gg-catalog
  - Zhang
    - followup on slurm-18160757
    - create a minimap process (either concat or separate)
      - create a channel/process for each screening reference
    - check for read loss (does it match the paper?)
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Jackwood Blast Parser

1. Email Ben Jackwood back (done)

#### add in isolate column to results


### gg-catalog-nf

#### compare of minimap results from joined and individual runs

- followup on slurm-18160757

```bash
INFO:    Converting OCI blobs to SIF format
INFO:    Starting build...
Getting image source signatures
Copying blob sha256:0dfa4d6d32846900cdf518b31b7420c8e3bee78df56f061347f079b085e55eed
Copying blob sha256:325ba66a34e9b2cf96e7958749a4fdd29a90699b6cd7eb67976c266a8277a26b
Copying blob sha256:bb6382425bb0d013b4122cc28ffc63f8bce680a6562260cb6fa715f6f16a59db
Copying blob sha256:bc16b5b173870a7a352f79080d004b34c4ef664a52851d9e53a7bf33af01035d
Copying blob sha256:967f73d309824e3b429d0bc9f3a19fcb24e18ee8c778103677225f2551f54cb9
Copying config sha256:fa5927a8bf6f48a693b14fd53727382027d1225d15e375fb444f3ca19de997e9
Writing manifest to image destination
Storing signatures
2023/02/02 14:27:42  info unpack layer: sha256:0dfa4d6d32846900cdf518b31b7420c8e3bee78df56f061347f079b085e55eed
2023/02/02 14:27:43  info unpack layer: sha256:325ba66a34e9b2cf96e7958749a4fdd29a90699b6cd7eb67976c266a8277a26b
2023/02/02 14:27:43  info unpack layer: sha256:bb6382425bb0d013b4122cc28ffc63f8bce680a6562260cb6fa715f6f16a59db
2023/02/02 14:27:43  info unpack layer: sha256:bc16b5b173870a7a352f79080d004b34c4ef664a52851d9e53a7bf33af01035d
2023/02/02 14:27:43  info unpack layer: sha256:967f73d309824e3b429d0bc9f3a19fcb24e18ee8c778103677225f2551f54cb9
INFO:    Creating SIF file...
[bam_sort_core] merging from 62 files and 1 in-memory blocks...
INFO:    Using cached SIF image
[bam_sort_core] merging from 62 files and 1 in-memory blocks...
INFO:    Using cached SIF image
[bam_sort_core] merging from 62 files and 1 in-memory blocks...
INFO:    Using cached SIF image
```

Filesizes 

```bash
# concat
$ bjl34716@ss-sub3 diagnostic$ ls -lah /scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/concat-ref
total 127G
drwxr-xr-x. 2 bjl34716 sealab 4.0K Feb  2 11:28 .
drwxr-xr-x. 4 bjl34716 sealab 4.0K Feb  2 11:19 ..
-rw-r--r--. 1 bjl34716 sealab 1.2G Feb  2 11:28 contam-refs.fna.gz
-rw-r--r--. 1 bjl34716 sealab 126G Feb  2 12:07 SRR15214153.sam

# gal-gal
$ bjl34716@ss-sub3 diagnostic$ ls -lah /scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/indv-ref/gal-gal
total 126G
drwxr-xr-x. 2 bjl34716 sealab  12K Feb  2 15:09 .
drwxr-xr-x. 5 bjl34716 sealab 4.0K Feb  2 16:29 ..
-rw-r--r--. 1 bjl34716 sealab  63G Feb  2 13:05 SRR15214153_gal_gal.sam
-rw-r--r--. 1 bjl34716 sealab  63G Feb  2 15:09 SRR15214153_gal_gal_sorted.sam

# glycine-max
$ bjl34716@ss-sub3 diagnostic$ ls -lah /scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/indv-ref/glycine-max
total 126G
drwxr-xr-x. 2 bjl34716 sealab  12K Feb  2 15:41 .
drwxr-xr-x. 5 bjl34716 sealab 4.0K Feb  2 16:29 ..
-rw-r--r--. 1 bjl34716 sealab  63G Feb  2 13:38 SRR15214153_glycine_max.sam
-rw-r--r--. 1 bjl34716 sealab  63G Feb  2 15:40 SRR15214153_glycine_max_sorted.sam

# zea-mays
$ bjl34716@ss-sub3 diagnostic$ ls -lah /scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/indv-ref/zea-mays
total 126G
drwxr-xr-x. 2 bjl34716 sealab  12K Feb  2 16:29 .
drwxr-xr-x. 5 bjl34716 sealab 4.0K Feb  2 16:29 ..
-rw-r--r--. 1 bjl34716 sealab  63G Feb  2 13:52 SRR15214153_zea_mays.sam
-rw-r--r--. 1 bjl34716 sealab  63G Feb  2 16:29 SRR15214153_zea_mays_sorted.sam

# merged
$ bjl34716@ss-sub3 diagnostic$ ls -lah /scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/indv-ref
total 189G
drwxr-xr-x. 5 bjl34716 sealab 4.0K Feb  2 16:29 .
drwxr-xr-x. 4 bjl34716 sealab 4.0K Feb  2 11:19 ..
drwxr-xr-x. 2 bjl34716 sealab  12K Feb  2 15:09 gal-gal
drwxr-xr-x. 2 bjl34716 sealab  12K Feb  2 15:41 glycine-max
-rw-r--r--. 1 bjl34716 sealab 189G Feb  2 17:07 merged_reads.sam
drwxr-xr-x. 2 bjl34716 sealab  12K Feb  2 16:29 zea-mays

```

189 > 126G, this is not fastq records which we could examine.

How do you count the number of samtools records?

```bash
samtools view -c -F 260 SAMPLE.bam
```
This counts only mapped (primary aligned) reads

This gave me weird results, so I am going to make fastqs then count the outputs.

gg-catalog rev: 5d829f9f8db3babcd26ca8a2446c9f2ecf903bdc
gg-catalog-nf rev: N/A
slurm sub: 18217928

```bash
/var/lib/slurmd/job18217928/slurm_script: line 19: samtools: command not found
/var/lib/slurmd/job18217928/slurm_script: line 19: samtools: command not found
INFO:    Using cached SIF image
[bam_sort_core] merging from 188 files and 1 in-memory blocks...
/var/lib/slurmd/job18217928/slurm_script: line 23: samtools: command not found
/var/lib/slurmd/job18217928/slurm_script: line 23: samtools: command not found
INFO:    Using cached SIF image
[E::sam_parse1] no SQ lines present in the header
[W::sam_read1] Parse error at line 1778
samtools sort: truncated file. Aborting
```

I set this up to just call singularity shell docker://lorentzb/samtools

gg-catalog rev: 600a2d7bd826b5f13b750d1629385585655d3d5c
gg-catalog-nf rev: N/A
slurm sub: 18229465

```bash
INFO:    Using cached SIF image
/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
/var/lib/slurmd/job18229465/slurm_script: line 21: samtools: command not found
/var/lib/slurmd/job18229465/slurm_script: line 21: samtools: command not found
/var/lib/slurmd/job18229465/slurm_script: line 21: samtools: command not found
/var/lib/slurmd/job18229465/slurm_script: line 25: samtools: command not found
```

It did not like that, I added a singularity call before each samtools invocation.

gg-catalog rev: 1c927b7e9b123a453815421bc270e70a52f048be
gg-catalog-nf rev: N/A
slurm sub: 18229634

```bash
A whole jumble of data, since I didnt write the file out
```

gg-catalog rev: 9151c76456aa96916adcd52d3e4c52ca5a10320a
gg-catalog-nf rev: N/A
slurm sub: 18246719

```bash
```

This process is still running at about 5pm so I might shelve it for the week and take a look first thing next week.

Since the data summed to different values we might have to look at this flag:

If the files already have defined read groups inside them, then doing a merge without the -r option should work:

samtools merge merged.bam s1.sort.sam s2.sort.sam s3.sort.sam

If there are multiple input files that share the same read group, then by default they will have random strings appended to make the read groups unique. This can be stopped by using the -c option, as mentioned in man samtools merge:

   -c      When  several  input files contain @RG headers with the same ID, emit only
           one of them (namely, the header line from the first file we find  that  ID
           in) to the merged output file.  Combining these similar headers is usually
           the right thing to do when the files being merged originated from the same
           file.

from [this source](https://bioinformatics.stackexchange.com/questions/908/how-to-merge-sam-files-together-with-adding-read-groups)



### Homework 1 

#### Go over every calculation 

Go over each question and re-calculate all of the results, and then check f-val as well as p-value to ensure correct results. Done, I feel confident in my conclusions.

### Update for Dr. Aggrey 

I made a simple PPT to outline the two datasets I'm currently working with and some potential ones to examine in the future (f:/mnt/aggrey/status-update-2-3-23.ppt). I also fully expect to be asked for what I've completed in the past year so that's a good thing to start thinking over. 

### Todos for Next Week

- Jackwood Blast
  - add in the isolate field into parser and output
  - meet with Ben to talk about two points above 2/2/23
- gg-catalog
  - Zhang
    - followup on slurm-18229634
    - try to incorporate the -c flag when samtools merging to see if the filesize is the same as concat
    - create a minimap process (either concat or separate)
      - create a channel/process for each screening reference
    - check for read loss (does it match the paper?)
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
a0e7bd9 - Benjamin Lorentz, Fri Feb 3 10:32:12 2023 -0500 : page for friday
```


#### gg-catalog

```bash
9151c76 - Benjamin Lorentz, Fri Feb 3 15:34:35 2023 -0500 : update 06
1c927b7 - Benjamin Lorentz, Fri Feb 3 13:27:05 2023 -0500 : update 06
600a2d7 - Benjamin Lorentz, Fri Feb 3 13:21:47 2023 -0500 : update 06
5d829f9 - Benjamin Lorentz, Fri Feb 3 11:46:59 2023 -0500 : add 06 script
```

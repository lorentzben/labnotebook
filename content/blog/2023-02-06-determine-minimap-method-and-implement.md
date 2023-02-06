---
title: 'Determine Minimap Method and Implement'
date: 2023-02-06T14:12:08Z
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
  
### gg-catalog-nf

#### slurm process 18246719

gg-catalog rev: 9151c76456aa96916adcd52d3e4c52ca5a10320a
gg-catalog-nf rev: N/A
slurm sub: 18246719

```bash
it printed the results to the logfile, again...
```

let's save the intermediaries and then delete them at the end if needed.

we need to remove the files: 
  slurm-18229634.out
  slurm-18246719.out
  nearly 200GB
  
gg-catalog rev: d1cb13b370fbbbe293eee6695f8a8aadf1646252
gg-catalog-nf rev: N/A
slurm sub: 18436360

```bash
it printed it all to the log AGAIN!!!
```

```bash
cat /home/bjl34716/my_utils/gg-catalog/code/diagnostic/slurm-18436360.out |
     awk 'NR%4==2{c++; l+=length($0)}
          END{
                print "Number of reads: "c; 
                print "Number of bases in reads: "l
              }'
```

#### Merging sam files with colliding ID flag to see if that produces a smaller filesize

from the forums, cited in 02/03/2023, I found the flag samtools merge -c which will "combine @RG headers with colliding IDs [alter IDs to be distinct] Combine @PG headers with colliding IDs [alter IDs to be distinct]" I added both the c and p flags to see if this filesize will match the combined db size of 126G

gg-catalog rev: c4cff620c145854095baf9e7559fd638d345d842
gg-catalog-nf rev: N/A
slurm sub: 18441011

```bash
bjl34716@ss-sub3 diagnostic$ ls -lah /scratch/bjl34716/nf_dev/gg-catalog/compare-minimap/indv-ref
-rw-r--r--. 1 bjl34716 sealab 189G Feb  2 17:07 merged_reads.sam
-rw-r--r--. 1 bjl34716 sealab 189G Feb  6 11:38 merged_reads_V2.sam
```

These resulted in the same output :/ So we have to work on the merging to see if that gives us better results.

Based on this [user's writing](https://yiweiniu.github.io/blog/2018/07/Remove-Contamination-of-Pokaryotic-Organisms-in-Reads/):

Prepare the contamination library

    Download all the sequences of bacteria, viral, fungi, protozoa, and archaea using refseq2kraken. See note Detect Microbial Contamination in Contigs by Kraken for details. We can also use ncbi-genome-download to download them.

# folder structures
$ ls genomes/refseq/
archaea  bacteria  fungi  protozoa  viral

Merge all the sequences into one single Fasta.

Since I’ve got the mitochondrion DNA sequences of the target organism, I added them in the contaminant library to remove reads from mtDNA too. This library is refered as to $contaminants below.

We should just merge the fastas and then make the index off that and use that to screen.

#### Try to implement MINIMAP2 into gg-catalog-nf

If this works then we can get rid of the parse contam file and all. 


gg-catalog rev: 695521be87c81960d7df863e37cf6f0bfdade525
gg-catalog-nf rev: 44121283d62d329885451ef1067ef2c4504c145d
slurm sub: 18457644

```bash
Error executing process > 'MINIMAP2_INDEX (1)'

Caused by:
  Not a valid path value type: org.codehaus.groovy.runtime.NullObject (null)
```

gg-catalog rev: 695521be87c81960d7df863e37cf6f0bfdade525
gg-catalog-nf rev: 3da85127daa71b9bdde9545bc4fe2de82e55f23d
slurm sub: 18457731

```bash
Error executing process > 'MINIMAP2_INDEX'

Caused by:
  Not a valid path value type: groovyx.gpars.dataflow.DataflowBroadcast (DataflowBroadcast around DataflowStream[?])
```

Reverting to the parsing method

gg-catalog rev: 13f2c079f6f50521dde3ace3c971583f83e51ba7
gg-catalog-nf rev: 8644cdb726e7e9b37cd6624e1813a37fe8fc3ef9
slurm sub: 18457990

```bash
executor >  slurm (1)
[4c/f37e69] process > FILTLONG (7)       [100%] 7 of 7, cached: 7 ✔
[04/8835f7] process > MINIMAP2_INDEX (1) [100%] 1 of 1 ✔
[-        ] process > MINIMAP2_ALIGN     -
Execution cancelled -- Finishing pending tasks before exit
WARN: Input tuple does not match input set cardinality declared by process `MINIMAP2_ALIGN` -- offending value: /scratch/bjl34716/nf_dev/gg-catalog/work/bf/cd0e9d90cf34cdb99a3d93ff058a35/SRR15214153.fastq.gz
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/minimap2/align/main.nf' at line: 2 or see '.nextflow.log' file for more details
```

gg-catalog rev: 13f2c079f6f50521dde3ace3c971583f83e51ba7
gg-catalog-nf rev: 5b33b8f7dc88c11360ea6693d74fc97ddfc8a4f8
slurm sub: 18459761

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/5E1c2KiqWIEnF7
[4c/f37e69] process > FILTLONG (7)       [100%] 7 of 7, cached: 7 ✔
[04/8835f7] process > MINIMAP2_INDEX (1) [100%] 1 of 1, cached: 1 ✔
[-        ] process > MINIMAP2_ALIGN     -
Execution cancelled -- Finishing pending tasks before exit
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/minimap2/align/main.nf' at line: 2 or see '.nextflow.log' file for more details
```

I wanted to try to see if I emit the input and paths at the same time, will we be able to pass that into the next process? (probably not but lets see!)

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: b043ab620e18d4b34e08da1c52902558ebebb13e
slurm sub: 18467903

```bash
Monitor the execution with Nextflow Tower using this url https://tower.nf/user/bjl34716/watch/4a4QV6lHuvnpA1
[1f/d0449c] process > FILTLONG (3)       [100%] 3 of 3, cached: 3
[fa/898530] process > MINIMAP2_INDEX (1) [100%] 1 of 1, cached: 1 ✔
[-        ] process > MINIMAP2_ALIGN     -
Execution cancelled -- Finishing pending tasks before exit
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/minimap2/align/main.nf' at line: 2 or see '.nextflow.log' file for more details
[c3/cb0257] Cached process > FILTLONG (4)

Feb-06 15:44:54.313 [Actor Thread 2] ERROR nextflow.processor.TaskProcessor - Execution aborted due to an unexpected error
java.lang.NullPointerException: Cannot get property 'id' on null object
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: c75c4168630452bb8c33231dde6e630e0f473484
slurm sub: 18468358

```bash
no
```

Right now we have this going into filtlong:

```bash
[id:SRR15214153, single_end:true]
[id:SRR19683890, single_end:true]
[id:SRR19732729, single_end:true]
[id:SRR19683891, single_end:true]
[id:SRR19736685, single_end:true]
[id:SRR19726169, single_end:true]
[id:SRR19732514, single_end:true]
[/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]
[/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19683890.fastq]
[/scratch/bjl34716/gg-catalog/zhang/reads/colorectum/SRR19732729.fastq]
[/scratch/bjl34716/gg-catalog/zhang/reads/duodenum/SRR19683891.fastq]
[/scratch/bjl34716/gg-catalog/zhang/reads/ileum/SRR19736685.fastq]
[/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19726169.fastq]
[/scratch/bjl34716/gg-catalog/zhang/reads/jejunum/SRR19732514.fastq]
```
and trying to push this into minimap:

```bash
[[id:SRR19683890, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/77/dd425f456f21a3fbacf529ba5a640b/SRR19683890.fastq.gz]
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/bf/cd0e9d90cf34cdb99a3d93ff058a35/SRR15214153.fastq.gz]
```

but it won't recognize the first val is meta, so it wont find the id. I think the solution is in the map function but I still can't quite figure it out.

It is [documented by nextflow](https://nf-co.re/docs/contributing/modules#what-is-the-meta-map) so I should read this deeply tomorrow morning. 

### Todos for Tomorrow

- Jackwood Blast
  - add in the isolate field into parser and output
  - meet with Ben to talk about two points above 2/2/23
- gg-catalog
  - Zhang
    - create a minimap process (either concat or separate)
      - read about what a meta map is and if we can implement it
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

#### labnotebook

```bash
105a7ae - Benjamin Lorentz, Mon Feb 6 11:50:24 2023 -0500 : updates before lunch
c480239 - Ben Lorentz, Mon Feb 6 09:13:34 2023 -0500 : add page for monday
```

#### gg-catalog

```bash
100ef9b - Benjamin Lorentz, Mon Feb 6 15:03:48 2023 -0500 : update contam.tsv
13f2c07 - Benjamin Lorentz, Mon Feb 6 14:23:27 2023 -0500 : modify test_params and contam.tsv
695521b - Benjamin Lorentz, Mon Feb 6 14:11:30 2023 -0500 : update code/params/test_params.yaml
7191b56 - Benjamin Lorentz, Mon Feb 6 13:46:42 2023 -0500 : update 00_collect_data.sh
6be2027 - lorentzben, Mon Feb 6 11:09:33 2023 -0500 : dos2unix
c4cff62 - Benjamin Lorentz, Mon Feb 6 11:07:09 2023 -0500 : add 07_merge
d1cb13b - Benjamin Lorentz, Mon Feb 6 10:36:04 2023 -0500 : update 06
```

#### gg-catalog-nf

```bash
f09a327 - Benjamin Lorentz, Mon Feb 6 16:30:23 2023 -0500 : update to map
9e2acae - Benjamin Lorentz, Mon Feb 6 16:19:31 2023 -0500 : update main.nf
3a9bdf0 - Benjamin Lorentz, Mon Feb 6 16:14:50 2023 -0500 : update main.nf
67b5077 - Benjamin Lorentz, Mon Feb 6 16:13:25 2023 -0500 : update main.nf
6dbbef7 - Benjamin Lorentz, Mon Feb 6 16:09:39 2023 -0500 : update main.nf
7278771 - Benjamin Lorentz, Mon Feb 6 16:04:29 2023 -0500 : update main.nf
372629f - Benjamin Lorentz, Mon Feb 6 15:59:20 2023 -0500 : update main.nf
c75c416 - Benjamin Lorentz, Mon Feb 6 15:52:20 2023 -0500 : update main.nf
b043ab6 - Benjamin Lorentz, Mon Feb 6 15:44:24 2023 -0500 : update main.nf
5df6779 - Benjamin Lorentz, Mon Feb 6 15:19:07 2023 -0500 : update main.nf
a13f2a2 - Benjamin Lorentz, Mon Feb 6 15:15:31 2023 -0500 : updates
2726fee - Benjamin Lorentz, Mon Feb 6 15:13:52 2023 -0500 : update main.nf
:...skipping...
f09a327 - Benjamin Lorentz, Mon Feb 6 16:30:23 2023 -0500 : update to map 
9e2acae - Benjamin Lorentz, Mon Feb 6 16:19:31 2023 -0500 : update main.nf
3a9bdf0 - Benjamin Lorentz, Mon Feb 6 16:14:50 2023 -0500 : update main.nf
67b5077 - Benjamin Lorentz, Mon Feb 6 16:13:25 2023 -0500 : update main.nf
6dbbef7 - Benjamin Lorentz, Mon Feb 6 16:09:39 2023 -0500 : update main.nf
7278771 - Benjamin Lorentz, Mon Feb 6 16:04:29 2023 -0500 : update main.nf
372629f - Benjamin Lorentz, Mon Feb 6 15:59:20 2023 -0500 : update main.nf
c75c416 - Benjamin Lorentz, Mon Feb 6 15:52:20 2023 -0500 : update main.nf
b043ab6 - Benjamin Lorentz, Mon Feb 6 15:44:24 2023 -0500 : update main.nf
5df6779 - Benjamin Lorentz, Mon Feb 6 15:19:07 2023 -0500 : update main.nf
a13f2a2 - Benjamin Lorentz, Mon Feb 6 15:15:31 2023 -0500 : updates       
2726fee - Benjamin Lorentz, Mon Feb 6 15:13:52 2023 -0500 : update main.nf
5b33b8f - Benjamin Lorentz, Mon Feb 6 14:38:15 2023 -0500 : update main.nf
8644cdb - Benjamin Lorentz, Mon Feb 6 14:21:45 2023 -0500 : revert main.nf
3da8512 - Benjamin Lorentz, Mon Feb 6 14:17:14 2023 -0500 : update main.nf
4412128 - Benjamin Lorentz, Mon Feb 6 14:10:01 2023 -0500 : update main.nf
```
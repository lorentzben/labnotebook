---
title: 'Example Clean Read Mapping'
date: 2023-03-13T14:23:38Z
draft: false
meta_img: "images/image.png"
tags:
  - "BWA2"
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---


### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - yes, but Need to confirm with cat samples
    - try out the indexing and mapping steps with BWA
      - rev c60deddafd6ce2b4d8dcc57e0b9301ef046d2f82
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

#### Slurm Job 19824367

```bash
Name

MINIMAP2_ALIGN (cecum)

Command


minimap2 \
    -ax map-hifi --split-prefix temp_sam_ \
    -t 6 \
    "concat-gal-zea-glycine.fna.gz" \
    "cecum.fastq.gz" \
     \
    -L \
    -a | samtools sort | samtools view -@ 6 -b -h -o cecum.bam


cat <<-END_VERSIONS > versions.yml
"MINIMAP2_ALIGN":
    minimap2: $(minimap2 --version 2>&1)
END_VERSIONS

Status

Exit: 140 (FAILED) Attempts: 1 (action: FINISH)

Work directory

/scratch/bjl34716/nf_dev/gg-catalog/work/9e/e1bc1fc4fdce6ce2af967eb3a23044

MINIMAP2_ALIGN (colorectum)

Command


minimap2 \
    -ax map-hifi --split-prefix temp_sam_ \
    -t 6 \
    "concat-gal-zea-glycine.fna.gz" \
    "colorectum.fastq.gz" \
     \
    -L \
    -a | samtools sort | samtools view -@ 6 -b -h -o colorectum.bam


cat <<-END_VERSIONS > versions.yml
"MINIMAP2_ALIGN":
    minimap2: $(minimap2 --version 2>&1)
END_VERSIONS

Status

Exit: 140 (FAILED) Attempts: 1 (action: FINISH)

Work directory

/scratch/bjl34716/nf_dev/gg-catalog/work/de/4d7df060df8239747e53f8e76161e7
Error executing process > 'SAMTOOLS_FASTA (duodenum)'

Caused by:
  Process `SAMTOOLS_FASTA (duodenum)` terminated with an error exit status (1)

Command executed:

  samtools \
      fasta \
       \
      --threads 19 \
      -0 duodenum_other.fasta.gz \
      unmapped.bam \
      -1 duodenum_1.fasta.gz -s duodenum_singleton.fasta.gz

  cat <<-END_VERSIONS > versions.yml
  "SAMTOOLS_FASTA":
      samtools: $(echo $(samtools --version 2>&1) | sed 's/^.*samtools //; s/Using.*$//' ))
  END_VERSIONS

Command exit status:
  1
Command output:
  (empty)

Command error:
  [E::bgzf_read_block] Invalid BGZF header at offset 6040418483
  [E::bgzf_read] Read block operation failed with error 6 after 0 of 4 bytes
  samtools bam2fq: Failed to read bam record
  samtools bam2fq: Error writing to FASTx files.: Invalid argument
  [M::bam2fq_mainloop] discarded 0 singletons
  [M::bam2fq_mainloop] processed 1159732 reads

Work dir:
  /scratch/bjl34716/nf_dev/gg-catalog/work/ba/c020b29ab268a20d50e506bfa9e8bd

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`


slurmstepd: error: *** JOB 19824367 ON c5-3 CANCELLED AT 2023-03-13T10:23:40 ***
```
```

So we have an error with the mapping and an error with the samtools...

Lets try to re-submit with the resume if this also fails out then we can run without the resume and see if it has the same error.

gg-catalog rev: 4b058e842764d643035003abb51235ea63527ced
gg-catalog-nf rev: 6e13ede93201191b89fe3b575dc9f4cbc161b92d
slurm sub: 19868408

```bash
```

#### BWA example so I can calculate relative abundnance

Working directory: /scratch/bjl34716/nf_dev/gg-catalog/work/32/d0957dccda9335bcf3d814a670e5b1/

from http://www.sixthresearcher.com/list-of-helpful-linux-commands-to-process-fastq-files-from-ngs-experiments/

If we want to extract random sequences (1000):

```bash
> cat reads.fq | awk '{ printf("%s",$0); n++; if(n%4==0) { printf("n");} else { printf("X#&X");} }' | shuf | head -n 1000 | sed 's/X#&X/n/g' > reads.1000.fq
```

ended up using: 

```bash
# need to select 4000 since there are 4 lines
cat SRR19683891_other.fastq | head -n 4000 > reads.1000.fastq
# check number of reads == 1000
cat reads.1000.fastq | echo $((`wc -l`/4))
```

and then the index is located in: 
/scratch/bjl34716/nf_dev/gg-catalog/work/43/0370b57b959be32c0c311633aa0ff1/bwamem2/

singularity image:
https://depot.galaxyproject.org/singularity/mulled-v2-e5d375990341c5aef3c9aff74f96f66f65375ef6:2cdf6bf1e92acbeb9b2834b1c58754167173a410-0

```bash
bwa-mem2 map 

Usage: bwa-mem2 <command> <arguments>
Commands:
  index         create index
  mem           alignment
  version       print version number
Singularity> bwa-mem2 mem
Looking to launch executable "/usr/local/bin/bwa-mem2.avx2", simd = .avx2
Launching executable "/usr/local/bin/bwa-mem2.avx2"
-----------------------------
Executing in AVX2 mode!!
-----------------------------
* SA compression enabled with xfactor: 8
Usage: bwa-mem2 mem [options] <idxbase> <in1.fq> [in2.fq]
Options:
  Algorithm options:
    -o STR        Output SAM file name
    -t INT        number of threads [1]
    -k INT        minimum seed length [19]
    -w INT        band width for banded alignment [100]
    -d INT        off-diagonal X-dropoff [100]
    -r FLOAT      look for internal seeds inside a seed longer than {-k} * FLOAT [1.5]
    -y INT        seed occurrence for the 3rd round seeding [20]
    -c INT        skip seeds with more than INT occurrences [500]
    -D FLOAT      drop chains shorter than FLOAT fraction of the longest overlapping chain [0.50]
    -W INT        discard a chain if seeded bases shorter than INT [0]
    -m INT        perform at most INT rounds of mate rescues for each read [50]
    -S            skip mate rescue
    -o            output file name missing
    -P            skip pairing; mate rescue performed unless -S also in use
Scoring options:
   -A INT        score for a sequence match, which scales options -TdBOELU unless overridden [1]
   -B INT        penalty for a mismatch [4]
   -O INT[,INT]  gap open penalties for deletions and insertions [6,6]
   -E INT[,INT]  gap extension penalty; a gap of size k cost '{-O} + {-E}*k' [1,1]
   -L INT[,INT]  penalty for 5'- and 3'-end clipping [5,5]
   -U INT        penalty for an unpaired read pair [17]
Input/output options:
   -p            smart pairing (ignoring in2.fq)
   -R STR        read group header line such as '@RG\tID:foo\tSM:bar' [null]
   -H STR/FILE   insert STR to header if it starts with @; or insert lines in FILE [null]
   -j            treat ALT contigs as part of the primary assembly (i.e. ignore <idxbase>.alt file)
   -5            for split alignment, take the alignment with the smallest coordinate as primary
   -q            dont modify mapQ of supplementary alignments
   -K INT        process INT input bases in each batch regardless of nThreads (for reproducibility) []
   -v INT        verbose level: 1=error, 2=warning, 3=message, 4+=debugging [3]
   -T INT        minimum score to output [30]
   -h INT[,INT]  if there are <INT hits with score >80% of the max score, output all in XA [5,200]
   -a            output all alignments for SE or unpaired PE
   -C            append FASTA/FASTQ comment to SAM output
   -V            output the reference FASTA header in the XR tag
   -Y            use soft clipping for supplementary alignments
   -M            mark shorter split hits as secondary
   -I FLOAT[,FLOAT[,INT[,INT]]]
                 specify the mean, standard deviation (10% of the mean if absent), max
                 (4 sigma from the mean if absent) and min of the insert size distribution.
                 FR orientation only. [inferred]
Note: Please read the man page for detailed description of the command line and options.

Important parameter settings:
        BATCH_SIZE: 512
        MAX_SEQ_LEN_REF: 256
        MAX_SEQ_LEN_QER: 128
        MAX_SEQ_LEN8: 128
        SEEDS_PER_READ: 500
        SIMD_WIDTH8 X: 32
        SIMD_WIDTH16 X: 16
        AVG_SEEDS_PER_READ: 64
```

Mapping example

if we only see ~500 hits then we might need to up the -c flag

```bash

```

### Meet Dr. Aggrey

I wanted to check in with Dr. Aggrey and see if I am on the right path. It seems that I am a little lost. We talked through the data that I have and he suggested I get an easy victory. First he wanted me to identify the genes from the Huang data that are associate with Nitrogen Metabolism. Then he wants me to establish a gene network from those genes. I am not sure what I should do with that gene network once it is established.

Step 2 I was thinking of was to then take those genes of interest and try to find a FCR efficiency study that uses shotgun reads and then examine the abundance of my genes of interest and see if that is correlated with FCR.

### Examine Huang 2018 for what I know now


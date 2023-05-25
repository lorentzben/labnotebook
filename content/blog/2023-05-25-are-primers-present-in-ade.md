---
title: 'Are Primers Present in Ade'
date: 2023-05-25T13:29:43Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "Mock"
  - "Module"
  - "primer-detect"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Try to detect the primers present
  - Use cutadapt to remove primers
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
  - Run a proper analysis to send to Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.

### Ade

#### Picking proper parameters

Who was filtered out of the negative control analysis?



What was the accuracy of the mock analysis?

[] Re-run the analysis with HQ and New Visualize ampliseq?
[] figure out what primers are present?
  - https://github.com/linsalrob/primer-trimming
  - https://github.com/OpenGene/fastp
  - 
[] re-run with cutadapt

#### PRINSEQ Primer-trimming

set up image lorentzb/primer-trimming:1.0

I made a script to try to predict the primers, let's test:

cycle 4 rev: 602c38702e1b75893ba0e973926ef4b36b13b353
slurm job:23015564

```bash
FATAL:   Unable to handle docker://lorentzb/primer-trimmming:1.0 uri: failed to get checksum for docker://lorentzb/primer-trimmming:1.0: reading manifest 1.0 in docker.io/lorentzb/primer-trimmming: errors:
denied: requested access to the resource is denied
unauthorized: authentication required
```



cycle 4 rev: 4815bdb52f65730b319950109cb6ec1ad6933550
slurm job: 23015602

```bash
FATAL:   Unable to handle docker://lorentzb/primer-trimming:1.0 uri: failed to get checksum for docker://lorentzb/primer-trimming:1.0: reading manifest 1.0 in docker.io/lorentzb/primer-trimming: toomanyrequests: You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limit
FATAL:   Unable to handle docker://lorentzb/primer-trimming:1.0 uri: failed to get checksum for docker://lorentzb/primer-trimming:1.0: reading manifest 1.0 in docker.io/lorentzb/primer-trimming: toomanyrequests: You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limit
FATAL:   Unable to handle docker://lorentzb/primer-trimming:1.0 uri: failed to get checksum for docker://lorentzb/primer-trimming:1.0: reading manifest 1.0 in docker.io/lorentzb/primer-trimming: toomanyrequests: You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limit
FATAL:   Unable to handle docker://lorentzb/primer-trimming:1.0 uri: failed to get checksum for docker://lorentzb/primer-trimming:1.0: reading manifest 1.0 in docker.io/lorentzb/primer-trimming: toomanyrequests: You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limit
FATAL:   Unable to handle docker://lorentzb/primer-trimming:1.0 uri: failed to get checksum for docker://lorentzb/primer-trimming:1.0: reading manifest 1.0 in docker.io/lorentzb/primer-trimming: toomanyrequests: You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limit
FATAL:   Unable to handle docker://lorentzb/primer-trimming:1.0 uri: failed to get checksum for docker://lorentzb/primer-trimming:1.0: reading manifest 1.0 in docker.io/lorentzb/primer-trimming: toomanyrequests: You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limit
slurmstepd: error: *** JOB 23015602 ON c2-15 CANCELLED AT 2023-05-25T11:20:58 ***
```

Refactor to driver script and runner

cycle 4 rev: 8b0bac14d16aa04e6a0ff947d30bd585802e216a
slurm job: 23016103

```bash
FATAL:   Unable to handle docker://lorentzb/primer-trimming:1.0 uri: failed to get checksum for docker://lorentzb/primer-trimming:1.0: reading manifest 1.0 in docker.io/lorentzb/primer-trimming: toomanyrequests: You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limit
```

We have to wait


cycle 4 rev: 3e3c65d4a6ef663250d5d06b58643c907d3ffe75
slurm job: 23016233

```bash
INFO:    Using cached SIF image
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
primer-trim.sh: line 2: $'\r': command not found
primer-trim.sh: line 4: $'\r': command not found
primer-trim.sh: line 6: $'\r': command not found
primer-trim.sh: line 11: syntax error near unexpected token `$'do\r''
primer-trim.sh: line 11: `for file in $RAWDIR*.fastq.gz ; do^M'
```

cycle 4 rev: d42b63c44a090a3f95039f48789537f9621e5a3c
slurm job: 23016236

```bash
INFO:    Using cached SIF image
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)

$ ls -l /work/sealab/bjl34716/ade_cycle_1/ | wc -l 
530
$ ls -l /work/sealab/bjl34716/ade_cycle_1_primer_trimming/ | wc -l 
529

differing file: Cycle 4-20210426T155250Z-001.zip
```

cycle 4 rev: bcf771b86d2d046737aba69aebf13f485e74c50b
slurm job: 23017578

```bash
INFO:    Using cached SIF image
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)

CGAAAGCATGGGTAG 17842
TCGAAAGTGTGGGTA 2136
CGAAAGCGTGGGGA  22280
TGAGGCTCGAAAGC  243
GTGGGGATCAAACA  53
TGAGGTTCGAAAG   692
TGAGAAGCGAAA    9
GAGGCGCGAAAG    104
GGGTAGCGAAC     909
GGGGAGCAAAC     581
TGATGTGCGAA     63
GGGTAGCAAAC     137
GAGGCACGAAAGC   4

ClustalW

primer_0       --------CGAAAGCATGGGTAG	15
primer_1       -------TCGAAAGTGTGGGTA-	15
primer_2       --------CGAAAGCGTGGGGA-	14
primer_4       GTGGGGATCAAACA---------	14
primer_9       --GGGGAGCAAAC----------	11
primer_8       --GGGTAGCGAAC----------	11
primer_11      --GGGTAGCAAAC----------	11
primer_6       -TGAGAAGCGAAA----------	12
primer_10      -TGATGTGCGAA-----------	11
primer_7       --GAGGCGCGAAAG---------	12
primer_12      --GAGGCACGAAAGC--------	13
primer_3       -TGAGGCTCGAAAGC--------	14
primer_5       -TGAGGTTCGAAAG---------	13
```

cycle 4 rev: e98b80f631940c8a46fdb646aac4e90a0c81a603
slurm job: 23020971

```bash
```


#### Fastp

Do we need to store failed reads?
Does "--detect_adapter_for_pe" help?
Does "--correction" help?
We need "--overrepresentation_analysis"
Does "--dont_eval_duplication" help?

cycle 4 rev: c6f40ce8fd1e1c0cd1a5884bc664a7d0648bb82a
slurm job: 23018960

```bash
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/7-21_S271_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/7-28_S343_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/7-7_S223_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/8-0_S200_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/8-14_S248_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/8-21_S272_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/8-28_S344_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/8-7_S224_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/9-0_S201_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/9-14_S249_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/9-21_S273_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/9-28_S345_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/9-7_S225_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/Neg-Con_S168_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/Neg-Con_S287_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/Neg-Con_S324_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/Neg-Con_S72_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/mock-community_S167_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/mock-community_S288_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/mock-community_S323_L001R1_001.fastq.gz
ERROR: Failed to open file: /work/sealab/bjl34716/ade_cycle_1/mock-community_S71_L001R1_001.fastq.gz
```

cycle 4 rev: b24fee34c6208d1f815578670ffd2ff65ed75836
slurm job: 23019292

```bash
```



#### Setup new analysis with both cleaned datasets

Prinseq Analysis

cycle 4 rev: c22a0affcaa12e470c2816214bb49120cb78868f
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23023097

```bash
FATAL:   Unable to handle docker://lorentzb/figaro:1.2 uri: failed to get checksum for docker://lorentzb/figaro:1.2: reading manifest 1.2 in docker.io/lorentzb/figaro: toomanyrequests: You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limit
N E X T F L O W  ~  version 22.04.5
Not a valid params file extension: /home/bjl34716/ade/cycle-4/litter/primer-detect/ade-cycle-4-litter-prinseq.sh -- It must be one of the following: json,yml,yaml
cp: cannot stat ‘/work/sealab/bjl34716/ade/cycle-4/litter-prinseq’: No such file or directory
cp: cannot create regular file ‘/scratch/bjl34716/ade/cycle-4/litter-prinseq/metadata.tsv’: No such file or directory
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
slurmstepd: error: *** JOB 23023097 ON c4-1 CANCELLED AT 2023-05-25T16:37:51 ***
```

cycle 4 rev: 5563d66487fa4bd89861d8f7a0704d8836c7c20f
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 

```bash
```


#### Ben's Other analysis

What steps did he take?

What steps do I take?



#### Longitudinal Analysis

See if it makes a difference in this specific analysis. 


### Questions to ask for new analysis

- What primers did you use for amplification?
- What region were you targeting?
- What sequencer did you use?
- What kind of extraction did you perform? (Kit manual etc)
- Do you have nanodrop/qubit 

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - compare fastp and prinseq analyses
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
  - Run a proper analysis to send to Ade
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.

### Git Commits

#### Labnotebook

```bash
b384a1d - Benjamin Lorentz, Thu May 25 14:10:35 2023 -0400 : notes from before lunch
b0ab321 - Benjamin Lorentz, Thu May 25 09:32:03 2023 -0400 : add page for Thursday
c01bb0b - Benjamin Lorentz, Wed May 24 17:12:17 2023 -0400 : final notes for wednesday:
```

#### Cycle 4

```bash
5563d66 - Benjamin Lorentz, Thu May 25 16:49:54 2023 -0400 : update driver scripts
c22a0af - Benjamin Lorentz, Thu May 25 16:33:51 2023 -0400 : update fastp and prinseq mapping files
391bec1 - Benjamin Lorentz, Thu May 25 16:10:39 2023 -0400 : update prinseq script and paramfiles
f4b55ed - Benjamin Lorentz, Thu May 25 16:01:38 2023 -0400 : add skeletons for fastp vs prinseq comparison analyses
e98b80f - Benjamin Lorentz, Thu May 25 15:43:29 2023 -0400 : update primer-trim.sh
b24fee3 - Benjamin Lorentz, Thu May 25 15:25:38 2023 -0400 : update fastp-trim.sh
c6f40ce - Benjamin Lorentz, Thu May 25 15:23:29 2023 -0400 : update fastp-trim.sh
194e33d - Benjamin Lorentz, Thu May 25 15:22:03 2023 -0400 : update fastp-trim.sh
3f81824 - Benjamin Lorentz, Thu May 25 14:45:14 2023 -0400 : add fastp-trim.sh update fastp-qc.sh
ac88170 - Benjamin Lorentz, Thu May 25 14:42:07 2023 -0400 : update primer-trim.sh
53697ba - Benjamin Lorentz, Thu May 25 14:41:26 2023 -0400 : update primer-trim.sh
bcf771b - Benjamin Lorentz, Thu May 25 14:21:32 2023 -0400 : update primer-trim.sh
:...skipping...
5563d66 - Benjamin Lorentz, Thu May 25 16:49:54 2023 -0400 : update driver scripts
c22a0af - Benjamin Lorentz, Thu May 25 16:33:51 2023 -0400 : update fastp and prinseq mapping files
391bec1 - Benjamin Lorentz, Thu May 25 16:10:39 2023 -0400 : update prinseq script and paramfiles
f4b55ed - Benjamin Lorentz, Thu May 25 16:01:38 2023 -0400 : add skeletons for fastp vs prinseq comparison analyses
e98b80f - Benjamin Lorentz, Thu May 25 15:43:29 2023 -0400 : update primer-trim.sh
b24fee3 - Benjamin Lorentz, Thu May 25 15:25:38 2023 -0400 : update fastp-trim.sh
c6f40ce - Benjamin Lorentz, Thu May 25 15:23:29 2023 -0400 : update fastp-trim.sh
194e33d - Benjamin Lorentz, Thu May 25 15:22:03 2023 -0400 : update fastp-trim.sh
3f81824 - Benjamin Lorentz, Thu May 25 14:45:14 2023 -0400 : add fastp-trim.sh update fastp-qc.sh
ac88170 - Benjamin Lorentz, Thu May 25 14:42:07 2023 -0400 : update primer-trim.sh
53697ba - Benjamin Lorentz, Thu May 25 14:41:26 2023 -0400 : update primer-trim.sh
bcf771b - Benjamin Lorentz, Thu May 25 14:21:32 2023 -0400 : update primer-trim.sh
d42b63c - Benjamin Lorentz, Thu May 25 11:57:27 2023 -0400 : dos2unix
3e3c65d - Benjamin Lorentz, Thu May 25 11:55:19 2023 -0400 : update primer trimming
8b0bac1 - Benjamin Lorentz, Thu May 25 11:26:58 2023 -0400 : driver script and exec script
4815bdb - Benjamin Lorentz, Thu May 25 11:08:48 2023 -0400 : update primer-trimming
602c387 - Benjamin Lorentz, Thu May 25 11:04:52 2023 -0400 : update primer-trimming.sh
```
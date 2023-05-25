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

singularity run docker://lorentzb/primer-trimming:1.0 bash primer-trimming.sh

#### Fastp



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



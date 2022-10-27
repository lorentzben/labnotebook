---
title: Report Chunk 06
author: Ben Lorentz
date: '2022-10-27'
slug: report-chunk-06
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Todos for Today:

- Submit TAP for the stats class *Done*
- Open Enrollment for Work
- continue reading jones 
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- add example params and slurm for ampliseq into ampliseq-vis
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running
- Collect reference genome and annotations.
- Shaile’s compare flip/flop
- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters


I am feeling like I'm running through molasses right now, I think I need to examine some pretty easy to achieve tasks today to get some wind back in my sails. TAP is going to be one and I found the sampling depth determiner, I also think I want to re-submit the job with a higher quality cutoff for dada2 to see if that is causing issues, followed by examining fastqc results to see if something else is more apparent. 

### Understand how sampling depth is determined for ampliseq

Ampliseq

We should use this paradigm to start the pipeline:

```bash
nextflow run nf-core/ampliseq \
    -r 2.3.2 \
    -profile singularity \
    -params-file params.yaml
```

with params.yaml containing:

```yaml
input: 'data'
FW_primer: 'GTGYCAGCMGCCGCGGTAA'
RV_primer: 'GGACTACNVGGGTWTCTAAT'
metadata: 'data/Metadata.tsv'
outdir: './results'
```

my params.yaml looks like:

```yaml
input: '/home/bjl34716/nf_dev/ampliseq-example/all_days_sbm_cec_raw_nf_manifest.tsv'
skip_cutadapt: True
metadata: '/home/bjl34716/nf_dev/ampliseq-example/all_days_sbm_cec_nf_treatment_metadata.tsv'
outdir: '/work/sealab/bjl34716/applegate/cec_raw_nf'
trunc_qmin: 35
```

The way ampliseq determines the --p-sampling-depth parameter is this way:

```bash
mindepth=\$(count_table_minmax_reads.py $stats minimum 2>&1)
    if [ \"\$mindepth\" -gt \"10000\" ]; then echo \$mindepth >\"Use the sampling depth of \$mindepth for rarefaction.txt\" ; fi
    if [ \"\$mindepth\" -lt \"10000\" -a \"\$mindepth\" -gt \"5000\" ]; then echo \$mindepth >\"WARNING The sampling depth of \$mindepth is quite small for rarefaction.txt\" ; fi
    if [ \"\$mindepth\" -lt \"5000\" -a \"\$mindepth\" -gt \"1000\" ]; then echo \$mindepth >\"WARNING The sampling depth of \$mindepth is very small for rarefaction.txt\" ; fi
    if [ \"\$mindepth\" -lt \"1000\" ]; then echo \$mindepth >\"WARNING The sampling depth of \$mindepth seems too small for rarefaction.txt\" ; fi
```

the file [count_table_minmax_reads.py](https://github.com/nf-core/ampliseq/blob/master/bin/count_table_minmax_reads.py) is linked. 

- Compare dada2 ASV-table to the qiime 2 feature-table.biom to see how different they are.

- I was able to run the min/max python file on qiime2/abundance_tables/feature-table.tsv: 507 DADA2_table:519 
  - what is the mismatch? -> go back to raw results
  - the warning I recieved was WARNING The sampling depth of 507 seems too small for rarefaction.txt, so that means go with the qiime2/abundance_tables/feature-table.tsv


### Collecting example runs and Updating the trunc_qmin

I submitted the job slurm-15106068 to see if its the correct start, but that is with the Test profile, I need to find the one that is for my data.

I want to submit two runs, one of the raw data and then one of the primer clipped data.

from /home/bjl34716/applegate/villegas/compare_methods
```bash
#!/bin/bash

#SBATCH --partition=batch
#SBATCH --job-name=villegas_SBM_CEC_RAW_NF
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=1
#SBATCH --nodes=1
#SBATCH --time=96:00:00
#SBATCH --mem=8gb

#Replace this with your UGA email to get notified on completion
#SBATCH --mail-user="bjl34716@uga.edu"
#SBATCH --mail-type=BEGIN,END,FAIL


CURR_META="all_days_sbm_cec_nf_treatment_metadata"
CURR_MANI="all_days_sbm_cec_raw_nf_manifest"

if [[ ! -e /scratch/bjl34716/applegate/villegas_raw_nf ]]; then
    mkdir /scratch/bjl34716/applegate/villegas_raw_nf
        cp /home/bjl34716/applegate/villegas/compare_methods/"$CURR_MANI".tsv /scratch/bjl34716/applegate/villegas_raw_nf
        cp /home/bjl34716/applegate/villegas/compare_methods/"$CURR_META".tsv /scratch/bjl34716/applegate/villegas_raw_nf
fi

cd /scratch/bjl34716/applegate/villegas_raw_nf
module load Nextflow/22.04.5
nextflow run nf-core/ampliseq \
        -r 2.4.0 \
        -with-tower \
        -c /home/bjl34716/applegate/villegas/compare_methods/.nextflow/config/gacrc.config \
        -profile slurm,singularity \
        -params-file /home/bjl34716/nf_dev/ampliseq-example/raw_nf_params.yaml \
        -resume
```

Raw data nf-core with 35 qtrunc
  - submission dir: /home/bjl34716/nf_dev/ampliseq-example
  - params file: /home/bjl34716/nf_dev/ampliseq-example/raw_nf_params.yaml
  - slurm job: 15106266
  - Nf job name: fervent_boyd
  
```yaml
# raw_nf_params.yaml
input: '/home/bjl34716/nf_dev/ampliseq-example/all_days_sbm_cec_raw_nf_manifest.tsv'
skip_cutadapt: True
metadata: '/home/bjl34716/nf_dev/ampliseq-example/all_days_sbm_cec_nf_treatment_metadata.tsv'
outdir: '/work/sealab/bjl34716/applegate/cec_raw_nf'
trunc_qmin: 35
```
  
Primer clipped data nf-core default params
  - submission dir: /home/bjl34716/nf_dev/ampliseq-example
  - params file: /home/bjl34716/nf_dev/ampliseq-example/pc_nf_params.yaml
  - slurm job: 15106759
  - Nf job name: wise_bardeen
  
```yaml
# pc_nf_params.yaml
input: '/home/bjl34716/nf_dev/ampliseq-example/all_days_sbm_cec_nf_pc_manifest.tsv'
skip_cutadapt: True
metadata: '/home/bjl34716/nf_dev/ampliseq-example/all_days_sbm_cec_nf_treatment_metadata.tsv'
outdir: '/work/sealab/bjl34716/applegate/cec_pc_nf'
```

I want to evalute the fastqc/multiqc results of both of these runs. Based on these results I potentially want to use --trunclenf && --trunclenr if the minq is not appropriate. 

### Implementing report 06


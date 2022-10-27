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
- Homework 5
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- re-watch the lecture for ChIP-seq
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

We could also set --min_frequency 2 to remove singletons if there is some weird artifacts!

### Implementing report 06

We want to stay consistent with how nf-core ampliseq selects their --p-sampling-depth. I also just want to check what other people say.

To be able to run core-metric-phylogeny, we need to include the uncompressed ASV table and the compressed QZA table.
This is technically a filtered ASV table which can be affected by the --min_frequency param (I believe have yet to confirm). 

COREMETRIC.out.pcoa looks like:

```bash
[/mnt/c/Users/bjl34716/Documents/my_utils/work/c1/62b8c93358191d1de36fccde36eedb/diversity_core/bray_curtis_pcoa_results.qza, /mnt/c/Users/bjl34716/Documents/my_utils/work/c1/62b8c93358191d1de36fccde36eedb/diversity_core/jaccard_pcoa_results.qza, /mnt/c/Users/bjl34716/Documents/my_utils/work/c1/62b8c93358191d1de36fccde36eedb/diversity_core/unweighted_unifrac_pcoa_results.qza, /mnt/c/Users/bjl34716/Documents/my_utils/work/c1/62b8c93358191d1de36fccde36eedb/diversity_core/weighted_unifrac_pcoa_results.qza]
```

I was able to implement core-phylogenetic-metrics, now I need to figure out how to link this to the r-core I have written before. The result dir for core-metric looks like:

```bash
$ ls work/c1/62b8c93358191d1de36fccde36eedb/diversity_core/
bray_curtis_distance_matrix.qza  jaccard_emperor.qzv                     unweighted_unifrac_emperor.qzv
bray_curtis_emperor.qzv          jaccard_pcoa_results.qza                unweighted_unifrac_pcoa_results.qza
bray_curtis_pcoa_results.qza     observed_features_vector.qza            weighted_unifrac_distance_matrix.qza
evenness_vector.qza              rarefied_table.qza                      weighted_unifrac_emperor.qzv
faith_pd_vector.qza              shannon_vector.qza                      weighted_unifrac_pcoa_results.qza
jaccard_distance_matrix.qza      unweighted_unifrac_distance_matrix.qza
```

I am going to run revision: 6c56278ca8 [dev] which I expect to break but I want to see what files are present in the working directory. My error looks like. 

```bash
Quitting from lines 123-166 (06_report.Rmd)
Error in read_q2metadata(metadata_file) :
  Metadata does not define types (ie second line does not start with #q2:types)
Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> read_q2metadata
```

I am going to cd into the WD (37/ce0125) and then try to read the metadata into a dplyr frame and see if that is a fix

So if I read the table using read_table my dplyr join by's don't work. So what i'm thinking to do is to use the qiime2 formatted metadata (we would have to test this going through ampliseq...) and then be able to use read metadata in Report 06

Todo:

- revert 06 to read_metadata
- check 01-05 for any read_tables for metadata and have to add a skip rows in the read to avoid the meta-metadata column.
- re-run ampliseq using the newer metadata: **started 15112815**. NF name: cheeky_becquerel
- re-run raw with q 35 slurm-15112824.out nf name soggy_bartik


work/1d/ccb7a5 contains which is excellent!

```bash
06_report.Rmd                 item_of_interest.csv          shannon_vector.qza
bray_curtis_pcoa_results.qza  jaccard_pcoa_results.qza      taxonomy.qza
evenness_vector.qza           metadata.tsv                  unweighted_unifrac_pcoa_results.qza
faith_pd_vector.qza           observed_features_vector.qza  weighted_unifrac_pcoa_results.qza
feature-table.qza             order_item_of_interest.csv
Figures                       results
```

### Report 01 Issues

in work/7f/657f4474ffedad9c33d2df75047bf0  I am getting the error

```bash
Quitting from lines 118-157 (01_report_MbA.Rmd)
Error in mbSetObj$dataSet : $ operator is invalid for atomic vectors
Calls: <Anonymous> ... eval_with_user_handlers -> eval -> eval -> PlotTaxaAundanceBar
```
this is after I changed the read.csv to skip=1 so that I can use the qiime formatted metadata file



### Notes from class on Sleuth 

Maybe an optional lecture on FDR which was part of chip-seq and regulatory analysis. 

#### Slides for chip-seq and regulatory analysis

The more molecular biology you know, the better off you are for the analysis. Molecular machines vs silican machines. Regulatory genomics, many processes in cell, many steps, if they can be encoded and they can be understood. 

Many steps in gene regulation in eukaryotes. Basic features like transcription start site, can actually use RNA-seq. 

Organism agnostic and organism specific approaches. Enhancers can bind to proteins at a distance (possibly through looping) move enhancers around (prepositionally independent of transcription), SV-40 was the first enhancer identified. Regulatory process are hierarchical, scale matters. Hi-C can examine some of the hierarchical features. The questions is related to the long range interactions, Topologically associated domains (TADs) enhancer promotoer interaction happening in the tad? Unless there could be some other higher order features these TADs are doing because DNA is packed so deeply.

Hi-C is also used for genomics, biological processes, regulation and Scaffolding. Proximity ligation of long range interactions and identifying what is happening is done by ChIP-seq. 3-4 day protocol to run an analysis, transcription binding factor, specific factors that had antibodies. Overlap ATAC-seq helped add more information to understanding regulation. ChIP-seq can do qpcr to just get a small view of quantification of binding. Genome wide binding map you can link it to nuclease, or ATAC-seq data (transposition in vitro nucleosomes), histome data (chromatin landscape). Transcriptional biology revolutionized. Limited by pull down and analyse the data, good antibody for enrichment and good signal of processing the data, theres a lot of bad data out there. qpcr on certain loci to make sure enrichment is good. Cross-reactivity to other epitomes (minimize) stable source of it (to reproduce), and high enrichment on known targets. ChIP and then ChIP with a second antibody. Protein to protein to DNA interaction. Protien-A + Protein-B + DNA they are bound to. Peaks are just reads mapping to genome, higher peak greater enrichment of pulldown greater probability of interaction between protein and DNA, only true if not due to spurious binding. Mock Pulldown, where would reads map with no antibody, or one that doesn't bind. Stronger peak higher probability of binding, more likely binding event and greater sequence fragment and then you can sequence it (to determine function I guess?). High coverage of mapped reads conditional of ability to map reads there(?). Binding events occur in nucleus, genes could be upstream and downstream, associating binding reagion with gene is an art, not always closest, not right by transcription start sites. Lack of binding isn't always no binding but there could be repetitive elements. 

Bound regions, search what the binding sequence is, find the sequence specificty of Transcption factor, and then search the genome, or check ATAC seq region to see if its there. Generate library or moitf and then search. Bound regions you can do differential binding similar to DGE, you need to define intervals earlier to ask the question if there's a bound region. Counting tags in each region, have replicates in treatment, compare binding between treatments and compare to variability within treatment and statistically compare. 

ATAC-seq similar to nextrera, probe nuclosomes and transcription sites, gets chromatin states, get flanking regions, small input material, dont need antibody, tells you whats open but not whats binding. 

DNA modifications, third gen sequencing, look at kinetics of sequencing and can detect modification, workhorse is methylated sequences, Bisulfite-seq 
Will never go away, so that means I've got to dig into it more. 

#### Demo of Kallisto/Sleuth for the homework. 

Quantification using pseudocounts and then Sleuth to do differential expression. 

What do you do with the gene-list? Go-terms somewhat amorphous. Functional enrichment is skeptical. What is the biological process in a list of genes? that's up the the researcher, did you want to find a gene? then go out and functionally confirm that.  if its evolutionary fine include them all to see what's changing. there are many tools that can answer some of those questions. He's never done a GO analysis, hasn't had that type of research question. 
With transcriptomics you are at least looking at the real genes. What processes are enriched from my list? 

GO each gene is treated equally, bag of genes model. 

The ontology is messy when you're doing ChIP-seq since you don't know which gene your binding site is bound to, two if a gene is really long it can have more spurious binding, then there is a bias toward big genes. 

What does it mean, and does it mean anything? The value of gene ontology, not meant for enrichment was primarily for genome annotation to standardize vocabulary across organisms. 

Run the analysis but if it's unclear or unhelpful then let it go. 

Indexing a set of fasta sequences for transcripts, we do not index the genome. In Eukaryotes there can be multiple splices so k-mers could be assigned to any of the transripts. Indexing and graphing the transcripts, because of alternative splicing parts of the graphs will share transcripts. Index makes T-DBG, use the index structure to assign kmers from reads to nodes. reference transcriptome index, but the fasta names, stranded is important, threaded is good, bootstrap samples helps estimate the technical variation. --pseudobam will make estimated location of reads to transcipts, --genomebam provide gtf file of where transcipts are and will provide bam on genome coordinates, and then you can visualize on IGV where these reads are mapped on genome. 


### Todos for Tomorrow:

- Open Enrollment for Work
- continue reading jones 
- Homework 5
- Visualize Ampliseq
  - Refine chunk 06
  - add example params and slurm for ampliseq into ampliseq-vis repos
  - Fix chunk 01
    - cd into /home/bjl34716/my_utils/work/7f/657f4474ffedad9c33d2df75047bf0 
    - run report 01 line by line in singularity docker://lorentzb/microbiome_analyst:1.1
- nf-core/Ampliseq
  - examine raw results
  - examine pc results
  - examine raw q2 results
- Term Paper
  - Collect reference genome and annotations 
- re-watch the lecture for ChIP-seq
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
  - are keystone species more important in gut microbiomes?
- How can multi-omics projects be implemented in host-microbe interactions
- Check in on classifier still running

---

- Shaile’s compare flip/flop

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters

### Git commits

#### Lab Notebook

```bash
81eabf6 - Benjamin Lorentz, Thu Oct 27 11:10:20 2022 -0400 : updates on new example generation
8846133 - Benjamin Lorentz, Thu Oct 27 08:55:41 2022 -0400 : note for thursday
```

#### Visualize ampliseq
```bash
8cf01df - Benjamin Lorentz, Thu Oct 27 17:15:40 2022 -0400 : metadata won't have a prepend if it is copied in
28f677e - Benjamin Lorentz, Thu Oct 27 17:13:27 2022 -0400 : report 06 is written in R
dbdd3db - Benjamin Lorentz, Thu Oct 27 17:08:08 2022 -0400 : Edits to 01 and 06
2a7baac - Benjamin Lorentz, Thu Oct 27 16:42:16 2022 -0400 : I think i fixed metadata reads
334afd6 - Benjamin Lorentz, Thu Oct 27 16:21:18 2022 -0400 : update paths for 06 report rmd file
6c56278 - Benjamin Lorentz, Thu Oct 27 16:07:59 2022 -0400 : I expect this to break
8d5432c - Benjamin Lorentz, Thu Oct 27 15:47:39 2022 -0400 : must add python3 before script
2749669 - Benjamin Lorentz, Thu Oct 27 15:45:54 2022 -0400 : move from bin into python scripts
2870390 - Benjamin Lorentz, Thu Oct 27 15:42:17 2022 -0400 : Permission Error
9f1febc - Benjamin Lorentz, Thu Oct 27 15:36:56 2022 -0400 : chmod +x, 755 and dos2unix
3ed2c29 - Benjamin Lorentz, Thu Oct 27 15:34:58 2022 -0400 : we must add in the count_table_minmax_reads.py script
4215c7b - Benjamin Lorentz, Thu Oct 27 15:25:51 2022 -0400 : this is how they escaped the bash vars later on, we should be consistent
d7132aa - Benjamin Lorentz, Thu Oct 27 15:23:23 2022 -0400 : put a bash variable with an exclamation point escape
8a4f0d3 - Benjamin Lorentz, Thu Oct 27 15:15:13 2022 -0400 : must tell it the out channel
973b05c - Benjamin Lorentz, Thu Oct 27 15:13:55 2022 -0400 : spell pcoa correctly
dbaa8a8 - Benjamin Lorentz, Thu Oct 27 15:07:47 2022 -0400 : add core metric block
```

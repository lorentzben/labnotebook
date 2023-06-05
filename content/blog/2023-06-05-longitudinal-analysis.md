---
title: 'Longitudinal Analysis'
date: 2023-06-05T13:36:42Z
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
  - Longitudinal Analysis By hand
    - Check out slurm 23139002
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
  
  
### Ade

#### Longitudinal Analysis By hand

Check out slurm 23139002

```bash
 (1/1) Invalid value for '--input-path': File 'collapse-FRESHINF0-table.qza'
  does not exist.
Usage: biom convert [OPTIONS]
Try 'biom convert -h' for help.

Error: Invalid value for '-i' / '--input-fp': File 'collapse-FRESHINF0-frequency/feature-table.biom' does not exist.
Traceback (most recent call last):
  File "/scratch/bjl34716/ade/cycle-4/work/23/45136fe66ebeff567e93bc024c47e4/.command.sh", line 46, in <module>
    table = pd.read_table("otu-"+str(item)+"-table.tsv", sep='  ', header=1)
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 767, in read_table
    return read_csv(**locals())
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 688, in read_csv
    return _read(filepath_or_buffer, kwds)
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 454, in _read
    parser = TextFileReader(fp_or_buf, **kwds)
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 948, in __init__
    self._make_engine(self.engine)
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 1180, in _make_engine
    self._engine = CParserWrapper(self.f, **self.options)
  File "/home/bjl34716/.local/lib/python3.6/site-packages/pandas/io/parsers.py", line 2010, in __init__
    self._reader = parsers.TextReader(src, **kwds)
  File "pandas/_libs/parsers.pyx", line 382, in pandas._libs.parsers.TextReader.__cinit__
  File "pandas/_libs/parsers.pyx", line 674, in pandas._libs.parsers.TextReader._setup_parser_source
FileNotFoundError: [Errno 2] No such file or directory: 'otu-FRESHINF0-table.tsv'`, size: 3064 (max: 255)
```

cycle 4 rev: 2068d8b3d18e3c2271bd0586a8aef4cebaa5bbb0
visualize ampliseq rev: 0230b78148bd5b05bad250cbeade98905ba1031b
slurm job: 23180389

```bash
outdir                    : /work/sealab/bjl34716/ade/cycle-4/litter-figaro-nc-mock-srs-viz-all-sample
Completed at: 02-Jun-2023 20:09:11
Duration    : 3h 39m 11s
CPU hours   : 65.7 (0% cached)
Succeeded   : 43
Cached      : 1
```


Longitudinal analysis

This could be a good setup:
  
  If we had a continuous covariate that we thought was associated with the alpha diversity, we could test that using qiime diversity alpha-correlation. However, the only continuous variable in this dataset is the days_since_transplant.
  
  In some experiments, multiple interacting factors may impact alpha diversity together. If our alpha diversity estimates follow a normal distribution, we may use analysis of variance (ANOVA) to test whether multiple effects significantly impact alpha diversity. This test is present in the q2-longitudinal plugin:
  
  qiime longitudinal anova \
    --m-metadata-file ./core-metrics-results/faith_pd_vector.qza \
    --m-metadata-file ./metadata.tsv \
    --p-formula 'faith_pd ~ genotype * donor_status' \
    --o-visualization ./core-metrics-results/faiths_pd_anova.qzv

otherwise:

1. Control/Treatment Diversity Metric analysis

  qiime longitudinal pairwise-differences \
  --m-metadata-file ecam-sample-metadata.tsv \
  --m-metadata-file shannon.qza \
  --p-metric shannon \
  --p-group-column delivery \
  --p-state-column month \
  --p-state-1 0 \
  --p-state-2 12 \
  --p-individual-id-column studyid \
  --p-replicate-handling random \
  --o-visualization pairwise-differences.qzv

2. Distance Based Control/Treatment analysis

  qiime longitudinal pairwise-distances \
  --i-distance-matrix unweighted_unifrac_distance_matrix.qza \
  --m-metadata-file ecam-sample-metadata.tsv \
  --p-group-column delivery \
  --p-state-column month \
  --p-state-1 0 \
  --p-state-2 12 \
  --p-individual-id-column studyid \
  --p-replicate-handling random \
  --o-visualization pairwise-distances.qzv
  
3. Volatility plot
  Diversity metric volitility over the time
  
  qiime longitudinal volatility \
  --m-metadata-file ecam-sample-metadata.tsv \
  --m-metadata-file shannon.qza \
  --p-default-metric shannon \
  --p-default-group-column delivery \
  --p-state-column month \
  --p-individual-id-column studyid \
  --o-visualization volatility.qzv
  
4. First differences can also do distances

  qiime longitudinal first-differences \
  --m-metadata-file ecam-sample-metadata.tsv \
  --m-metadata-file shannon.qza \
  --p-state-column month \
  --p-metric shannon \
  --p-individual-id-column studyid \
  --p-replicate-handling random \
  --o-first-differences shannon-first-differences.qza
  
  qiime longitudinal first-distances \
  --i-distance-matrix unweighted_unifrac_distance_matrix.qza \
  --m-metadata-file ecam-sample-metadata.tsv \
  --p-state-column month \
  --p-individual-id-column studyid \
  --p-replicate-handling random \
  --o-first-distances first-distances.qza
  
  You evaluate these objects using the linear mixed effect function
  
  qiime longitudinal linear-mixed-effects \
  --m-metadata-file first-distances.qza \
  --m-metadata-file ecam-sample-metadata.tsv \
  --p-metric Distance \
  --p-state-column month \
  --p-individual-id-column studyid \
  --p-group-columns delivery,diet \
  --o-visualization first-distances-LME.qzv
  
5. Setup a baseline measurment and go from there

  qiime longitudinal first-distances \
    --i-distance-matrix unweighted_unifrac_distance_matrix.qza \
    --m-metadata-file ecam-sample-metadata.tsv \
    --p-state-column month \
    --p-individual-id-column studyid \
    --p-replicate-handling random \
    --p-baseline 0 \
    --o-first-distances first-distances-baseline-0.qza
  
6. NMIT

Is an option but since we are light on sampling timepoints, I might wait to try this one towards the end (using an non-rarefied table): 

Within microbial communities, microbial populations do not exist in isolation but instead form complex ecological interaction webs. Whether these interdependence networks display the same temporal characteristics within subjects from the same group may indicate divergent temporal trajectories. NMIT evaluates how interdependencies of features (e.g., microbial taxa, sequence variants, or OTUs) within a community might differ over time between sample groups. NMIT performs a nonparametric microbial interdependence test to determine longitudinal sample similarity as a function of temporal microbial composition. For each subject, NMIT computes pairwise correlations between each pair of features. Between-subject distances are then computed based on a distance norm between each subject’s microbial interdependence correlation matrix. For more details and citation, please see Zhang et al., 2017.
    
7. Feature Volitlity

This is attempting to identify the features (taxa) that explain the state-contition (infected/control) over the time period

  qiime longitudinal feature-volatility \
    --i-table ecam-table.qza \
    --m-metadata-file ecam-sample-metadata.tsv \
    --p-state-column month \
    --p-individual-id-column studyid \
    --p-n-estimators 10 \
    --p-random-state 17 \
    --output-dir ecam-feat-volatility
    
8. Maturity Index

Try to determine maturity based on regression model, I don't think we have enough samples for this but we could try to run them just to see.

  qiime longitudinal maturity-index \
  --i-table ecam-table.qza \
  --m-metadata-file ecam-sample-metadata.tsv \
  --p-state-column month \
  --p-group-by delivery \
  --p-individual-id-column studyid \
  --p-control Vaginal \
  --p-test-size 0.4 \
  --p-stratify \
  --p-random-state 1010101 \
  --output-dir maturity

#### Pairwise difference comparisons

```bash
singularity shell docker://lorentzb/automate_16_nf:2.0

cd /scratch/bjl34716/ade/cycle-4/work/77/612268efdc4825a3fea9db14171743





```

#### Update Visualize Ampliseq Tag and Document Cycle 4 verison

Print params at the top of visualize ampliseq
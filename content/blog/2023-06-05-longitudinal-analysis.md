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
  --p-metric shannon_entropy \
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

1. Pairwise Shannon Comparisions

```bash
singularity shell docker://lorentzb/automate_16_nf:2.0

bash

export LC_ALL=C.UTF-8
export LANG=C.UTF-8

cd /scratch/bjl34716/ade/cycle-4/work/77/612268efdc4825a3fea9db14171743

qiime longitudinal pairwise-differences \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-metric shannon_entropy \
  --p-group-column Infection \
  --p-state-column Age \
  --p-state-1 0 \
  --p-state-2 7 \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-visualization 0-7-pairwise-differences.qzv
  
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Plugin error from longitudinal:

  metric must be a valid metadata or feature table column.

Debug info has been saved to /tmp/qiime2-q2cli-err-1amu1gkg.log

qiime longitudinal pairwise-differences \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-metric shannon_entropy \
  --p-group-column Infection \
  --p-state-column Age \
  --p-state-1 7 \
  --p-state-2 14 \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-visualization 7-14-pairwise-differences.qzv
  
qiime longitudinal pairwise-differences \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-metric shannon_entropy \
  --p-group-column Infection \
  --p-state-column Age \
  --p-state-1 14 \
  --p-state-2 21 \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-visualization 14-21-pairwise-differences.qzv
  
qiime longitudinal pairwise-differences \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-metric shannon_entropy \
  --p-group-column Infection \
  --p-state-column Age \
  --p-state-1 21 \
  --p-state-2 28 \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-visualization 21-28-pairwise-differences.qzv


```

Significant difference comparing Infection between days 14 to 21

```md
Pairwise difference tests
	W (wilcoxon signed-rank test) 	P-value 	FDR P-value
Group 			
NO 	9.0 	0.250000 	0.250000
YES 	8.0 	0.048828 	0.097656

Download scores as tsv
Multiple group tests
	H 	P value
Kruskal Wallis test 	4.934211 	0.02633
Pairwise group comparison tests
		Mann-Whitney U 	P-value 	FDR P-value
Group A 	Group B 			
YES 	NO 	15.0 	0.029489 	0.029489
```

Comparisons That were not significant

0-7

```md
Pairwise difference tests
	W (wilcoxon signed-rank test) 	P-value 	FDR P-value
Group 			
NO 	12.0 	0.8125 	0.8125
YES 	11.0 	0.6875 	0.8125

Download scores as tsv
Multiple group tests
	H 	P value
Kruskal Wallis test 	0.2 	0.654721
Pairwise group comparison tests
		Mann-Whitney U 	P-value 	FDR P-value
Group A 	Group B 			
YES 	NO 	21.0 	0.701478 	0.701478

Download scores as tsv
```

7-14

```md
Pairwise difference tests
	W (wilcoxon signed-rank test) 	P-value 	FDR P-value
Group 			
NO 	17.0 	0.322266 	0.322266
YES 	3.0 	0.004883 	0.009766

Download scores as tsv
Multiple group tests
	H 	P value
Kruskal Wallis test 	1.433058 	0.231266
Pairwise group comparison tests
		Mann-Whitney U 	P-value 	FDR P-value
Group A 	Group B 			
YES 	NO 	72.0 	0.245278 	0.245278

Download scores as tsv
```

21-28

```md
Pairwise difference tests
	W (wilcoxon signed-rank test) 	P-value 	FDR P-value
Group 			
NO 	27.0 	1.000000 	1.0
YES 	18.0 	0.652344 	1.0

Download scores as tsv
Multiple group tests
	H 	P value
Kruskal Wallis test 	0.06 	0.806496
Pairwise group comparison tests
		Mann-Whitney U 	P-value 	FDR P-value
Group A 	Group B 			
YES 	NO 	48.0 	0.838256 	0.838256

Download scores as tsv
```

2. Pairwise Distance Comparisions

```bash
singularity shell docker://lorentzb/automate_16_nf:2.0

bash

export LC_ALL=C.UTF-8
export LANG=C.UTF-8

cd /scratch/bjl34716/ade/cycle-4/work/77/612268efdc4825a3fea9db14171743

#Metadata 2 removes the mock and NC samples since they are not part of the analysis for timepoints

qiime longitudinal pairwise-distances \
  --i-distance-matrix diversity_core/unweighted_unifrac_distance_matrix.qza \
  --m-metadata-file metadata2.tsv \
  --p-group-column Infection \
  --p-state-column Age \
  --p-state-1 0 \
  --p-state-2 7 \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-visualization 0-7-pairwise-distances.qzv

  
qiime longitudinal pairwise-distances \
  --i-distance-matrix diversity_core/unweighted_unifrac_distance_matrix.qza \
  --m-metadata-file metadata2.tsv \
  --p-group-column Infection \
  --p-state-column Age \
  --p-state-1 7 \
  --p-state-2 14 \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-visualization 7-14-pairwise-distances.qzv
  
qiime longitudinal pairwise-distances \
  --i-distance-matrix diversity_core/unweighted_unifrac_distance_matrix.qza \
  --m-metadata-file metadata2.tsv \
  --p-group-column Infection \
  --p-state-column Age \
  --p-state-1 14 \
  --p-state-2 21 \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-visualization 14-21-pairwise-distances.qzv
  
qiime longitudinal pairwise-distances \
  --i-distance-matrix diversity_core/unweighted_unifrac_distance_matrix.qza \
  --m-metadata-file metadata2.tsv \
  --p-group-column Infection \
  --p-state-column Age \
  --p-state-1 21 \
  --p-state-2 28 \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-visualization 21-28-pairwise-distances.qzv
```

Significant Results:

None

Not Significant:

0-7

```md
Multiple group tests
	H 	P value
Kruskal Wallis test 	0.036735 	0.848006
Pairwise group comparison tests
		Mann-Whitney U 	P-value 	FDR P-value
Group A 	Group B 			
YES 	NO 	26.0 	0.898327 	0.898327

Download scores as tsv
```

7-14

```md
Multiple group tests
	H 	P value
Kruskal Wallis test 	0.123967 	0.724771
Pairwise group comparison tests
		Mann-Whitney U 	P-value 	FDR P-value
Group A 	Group B 			
YES 	NO 	50.0 	0.751334 	0.751334

Download scores as tsv

```

14-21

```md
Multiple group tests
	H 	P value
Kruskal Wallis test 	0.123967 	0.724771
Pairwise group comparison tests
		Mann-Whitney U 	P-value 	FDR P-value
Group A 	Group B 			
YES 	NO 	50.0 	0.751334 	0.751334

Download scores as tsv
```

21-28

```md
Multiple group tests
	H 	P value
Kruskal Wallis test 	0.106667 	0.743971
Pairwise group comparison tests
		Mann-Whitney U 	P-value 	FDR P-value
Group A 	Group B 			
YES 	NO 	41.0 	0.775051 	0.775051

Download scores as tsv
```

3. Linear Mixed Effects

```bash

singularity shell docker://lorentzb/automate_16_nf:2.0

bash

export LC_ALL=C.UTF-8
export LANG=C.UTF-8

cd /scratch/bjl34716/ade/cycle-4/work/77/612268efdc4825a3fea9db14171743

qiime longitudinal linear-mixed-effects \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-metric shannon_entropy \
  --p-group-columns Litter,Infection  \
  --p-state-column Age \
  --p-individual-id-column Pen \
  --o-visualization linear-mixed-effects.qzv
  
  Plugin error from longitudinal:

  Linear model will not compute due to singular matrix error. This may occur if input variables correlate closely or exhibit zero variance. Please check your input variables. Removing potential covariates may resolve this issue.
  
qiime longitudinal linear-mixed-effects \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-metric shannon_entropy \
  --p-formula 'shannon_entropy~Age+Litter+Infection' \
  --p-state-column Age \
  --p-individual-id-column Pen \
  --o-visualization linear-mixed-effects.qzv

```

Results

```md
 	Linear mixed effects parameters
Fixed Effects formula 	shannon_entropy~Age+Litter+Infection
Metric 	shannon_entropy
Group column 	[Infection, Litter]
State column 	Age
Individual ID column 	Pen
Random effects 	None
Model summary
	model summary
Model: 	MixedLM
No. Observations: 	102
No. Groups: 	24
Min. group size: 	3
Max. group size: 	5
Mean group size: 	4.2
Dependent Variable: 	shannon_entropy
Method: 	REML
Scale: 	0.1000
Log-Likelihood: 	-37.9396
Converged: 	Yes
	

Download summary as tsv
Model results
	Coef. 	Std.Err. 	z 	P>|z| 	[0.025 	0.975]
Intercept 	5.509 	0.079 	69.740 	0.000 	5.354 	5.664
Litter[T.CYC2] 	-0.018 	0.133 	-0.132 	0.895 	-0.278 	0.243
Litter[T.CYC3] 	-0.129 	0.081 	-1.584 	0.113 	-0.288 	0.031
Litter[T.FRESH] 	-0.641 	0.080 	-8.048 	0.000 	-0.797 	-0.485
Infection[T.YES] 	0.252 	0.063 	4.018 	0.000 	0.129 	0.375
Age 	0.006 	0.004 	1.545 	0.122 	-0.002 	0.013
Group Var 	0.000 	0.036
```

It looks like fresh litter in relation to Age has a significant explanation on Shannon diversity (Fresh litter is less diverse than Cycle 1 or Cycle 3)
Infection also significantly explainse Shannon diversity when comparing with Age (Infected has a higher diversity)

4. Volatility analysis

```bash

singularity shell docker://lorentzb/automate_16_nf:2.0

bash

export LC_ALL=C.UTF-8
export LANG=C.UTF-8

cd /scratch/bjl34716/ade/cycle-4/work/77/612268efdc4825a3fea9db14171743

qiime longitudinal volatility \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-default-metric shannon_entropy \
  --p-default-group-column Infection \
  --p-state-column Age \
  --p-individual-id-column Pen \
  --o-visualization infection-volatility.qzv

qiime longitudinal volatility \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-default-metric shannon_entropy \
  --p-default-group-column Litter \
  --p-state-column Age \
  --p-individual-id-column Pen \
  --o-visualization litter-volatility.qzv
```

We see that Cycle 3 is generally less diverse over the whole time period than cycle 1/cycle 2 and fresh litter is much less.

5. Rate of change analysis

```bash
singularity shell docker://lorentzb/automate_16_nf:2.0

bash

export LC_ALL=C.UTF-8
export LANG=C.UTF-8

cd /scratch/bjl34716/ade/cycle-4/work/77/612268efdc4825a3fea9db14171743

qiime longitudinal first-differences \
  --m-metadata-file metadata.tsv \
  --m-metadata-file diversity_core/shannon_vector.qza \
  --p-state-column Age \
  --p-metric shannon_entropy \
  --p-individual-id-column Pen \
  --p-replicate-handling random \
  --o-first-differences shannon-first-differences.qza
  
qiime longitudinal linear-mixed-effects \
  --m-metadata-file shannon-first-differences.qza \
  --m-metadata-file metadata.tsv \
  --p-metric Difference \
  --p-state-column Age \
  --p-individual-id-column Pen \
  --p-formula 'Difference~Age+Litter+Infection' \
  --o-visualization first-differences-LME.qzv
```

Now Fresh Litter is the only variable that is significant

```md
 	Linear mixed effects parameters
Fixed Effects formula 	Difference~Age+Litter+Infection
Metric 	Difference
Group column 	[Infection, Litter]
State column 	Age
Individual ID column 	Pen
Random effects 	None
Model summary
	model summary
Model: 	MixedLM
No. Observations: 	72
No. Groups: 	24
Min. group size: 	1
Max. group size: 	4
Mean group size: 	3.0
Dependent Variable: 	Difference
Method: 	REML
Scale: 	0.1456
Log-Likelihood: 	-41.5738
Converged: 	No
	

Download summary as tsv
Model results
	Coef. 	Std.Err. 	z 	P>|z| 	[0.025 	0.975]
Intercept 	0.140 	0.136 	1.036 	0.300 	-0.125 	0.406
Litter[T.CYC3] 	0.021 	0.109 	0.193 	0.847 	-0.193 	0.235
Litter[T.FRESH] 	0.358 	0.119 	3.002 	0.003 	0.124 	0.592
Infection[T.YES] 	-0.058 	0.094 	-0.621 	0.534 	-0.243 	0.126
Age 	-0.006 	0.006 	-1.013 	0.311 	-0.018 	0.006
Group Var 	0.004 	
```

6. NMIT

```bash
srun --pty  -p batch --mem=16G --nodes=1 --ntasks-per-node=8 --time=08:00:00 --job-name=qlogin --export=NONE /bin/bash

singularity shell docker://lorentzb/automate_16_nf:2.0

bash

export LC_ALL=C.UTF-8
export LANG=C.UTF-8

cd /scratch/bjl34716/ade/cycle-4/work/77/612268efdc4825a3fea9db14171743

qiime feature-table relative-frequency \
  --i-table feature-table.qza \
  --o-relative-frequency-table rel-feature-table.qza 
  
  
qiime longitudinal nmit \
  --i-table rel-feature-table.qza  \
  --m-metadata-file metadata.tsv \
  --p-individual-id-column Pen \
  --p-corr-method pearson \
  --o-distance-matrix nmit-dm.qza
  
qiime diversity beta-group-significance \
  --i-distance-matrix nmit-dm.qza \
  --m-metadata-file metadata.tsv \
  --m-metadata-column Infection \
  --o-visualization nmit.qzv
  
qiime diversity beta-group-significance \
  --i-distance-matrix nmit-dm.qza \
  --m-metadata-file metadata.tsv \
  --m-metadata-column Litter \
  --o-visualization litter-nmit.qzv
  
```

```md
Overview
	PERMANOVA results
method name 	PERMANOVA
test statistic name 	pseudo-F
sample size 	24
number of groups 	3
test statistic 	1.4759
p-value 	0.001
number of permutations
```

Comparison of community determines that the between group differences in litter is greater than the within group differences. With diversity increasing over use fresh -> cycle 2 -> cycle 3


TODO send Dr. Ade an email about these results

#### Update Visualize Ampliseq Tag and Document Cycle 4 verison

first, I needed to updated the ordered iois so that we don't have a ton of n/a in comparisons this is included in the revision f97e241535c9f7702eeddf9350db760e65172279


Print params at the top of visualize ampliseq

cycle 4 rev: f97e241535c9f7702eeddf9350db760e65172279
visualize ampliseq rev: 33997cdb315d22eaddb6d464542f6e56ffacc3b4 
slurm job: 23272564

```bash
Completed at: 05-Jun-2023 17:01:57
Duration    : 1h 19m 9s
CPU hours   : 68.0 (95.4% cached)
Succeeded   : 11
Cached      : 33
```

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Update Tags for Visualize Ampliseq
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Git Commits


#### Lab Notebook

```bash
d5a26aa - Benjamin Lorentz, Mon Jun 5 15:28:51 2023 -0400 : added notes about longitudinal analysis
cae706b - Benjamin Lorentz, Mon Jun 5 13:13:02 2023 -0400 : notes before lunch
5ae6c3b - Benjamin Lorentz, Mon Jun 5 09:40:17 2023 -0400 : added page for monday
```

#### Cycle 4

```bash
f97e241 - Benjamin Lorentz, Mon Jun 5 15:14:22 2023 -0400 : add updated ordered iois
caa0c60 - Benjamin Lorentz, Mon Jun 5 14:53:31 2023 -0400 : add longitudinal analysis report
```

#### Visualize Amplsieq

```bash
33997cd - Benjamin Lorentz, Mon Jun 5 15:24:48 2023 -0400 : update visualize-ampliseq.nf
```
---
title: 'Mock Community Analysis'
date: 2023-05-18T12:14:45Z
draft: false
meta_img: "images/image.png"
tags:
  - "Ade"
  - "visualize-ampliseq"
  - "normalize"
  - "SRS"
  - "Module"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Check updated output analysis
  - Positive Control Analysis
  - Mock Community Investigation
  - Run a proper analysis to send to Ade
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Ade

#### Positive Control Analysis

First step is to collect the sequences for the mock community:

I had to make an account and agree that I was not going to re-distribute the sequences

from qiime: 

```md 

### Evaluating quality of samples with known composition

Mock communities consist of known microbial strains that are intentionally mixed at defined proportions, such that the composition of the sample is known. Mock communities are useful for benchmarking bioinformatics methods, e.g., to determine how well a given method or pipeline estimates the expected composition. Many investigators also include mock communities or other samples with known compositions on sequencing runs to determine run quality and method optimization on a per-run basis. The q2-quality-control plugin contains two actions to assess mock community accuracy in each of these use cases. evaluate_composition assesses the accuracy with which the expected taxonomic composition (or other feature composition) is reconstructed. evaluate_seqs assesses the similarity of observed sequences to expected sequences, e.g., to determine the accuracy of denoising or OTU picking methods, and is described in the next section.

evaluate_composition compares the feature composition of pairs of observed and expected samples containing the same sample ID in two separate feature tables. Typically, feature composition will consist of taxonomy classifications or other semicolon-delimited feature annotations. Let’s give it a spin.


qiime quality-control evaluate-composition \
  --i-expected-features qc-mock-3-expected.qza \
  --i-observed-features qc-mock-3-observed.qza \
  --o-visualization qc-mock-3-comparison.qzv

Output visualizations:

    qc-mock-3-comparison.qzv: view | download

Taxon accuracy rate, taxon detection rate, and linear regression scores between expected and observed feature abundances are calculated at each semicolon-delimited rank, and plots of per-level accuracy and observation correlations are plotted. A histogram of distance between false positive observations and the nearest expected feature is also generated, where distance equals the number of rank differences between the observed feature and the nearest common lineage in the expected feature. Finally, lists of false positive (misclassified and underclassified) and false negative features are given at the bottom of the visualization. Misclassifications are features that do not match any expected features at the deepest level of classification (e.g., species level), and usually represent either sample contaminants or sub-optimal bioinformatics pipelines (e.g., the presence of chimeric sequences or the use of an overconfident taxonomic classifier). Underclassifications are observed features that match expected features, but are not classified to the expected taxonomic depth (e.g., they are only classified to genus level but that genus classification is correct); these are often valid features (i.e., not contaminants) but are not classified to the desired level either because of technical limitations (e.g., sequences too short), degraded sequence quality, or sub-optimal methods (only a poor carpenter blames his/her tools, but one tool can do better than another). False negatives are features that were expected to be observed, but were not; these can be compared to the false-positives to get an idea of what features may have been mis-/underclassified.

### Evaluating sequence quality

evaluate_seqs aligns a set of query (e.g., observed) sequences against a set of reference (e.g., expected) sequences to evaluate the quality of alignment. The intended use is to align observed sequences against expected sequences (e.g., from a mock community) to determine the frequency of mismatches between observed sequences and the most similar expected sequences, e.g., as a measure of sequencing/method errors. However, any sequences may be provided as input to generate a report on pairwise alignment quality against a set of reference sequences.

qiime quality-control evaluate-seqs \
  --i-query-sequences query-seqs.qza \
  --i-reference-sequences reference-seqs.qza \
  --o-visualization eval-seqs-test.qzv

Output visualizations:

    eval-seqs-test.qzv: view | download

This visualization shows the alignment results for each query sequence, the number of mismatches between expected and observed sequences, and finally pairwise alignments between each query sequence and its closest match among the reference sequences (if --p-show-alignments is set). This ouptut is still quite basic, but is planned for expansion in the near future. Keep your eyes peeled!
```

So we have two steps we can try:

1. See how good the sequences were generated

We just need to import the sequences as qza and then align representative sequences against them, but I don't think this is what we want to do?

2. See how good the analysis was performed

Fake an abundance table:
[wget https://raw.githubusercontent.com/caporaso-lab/mockrobiota/master/data/mock-25/unite/7-1/99-otus/expected-taxonomy.tsv](https://raw.githubusercontent.com/caporaso-lab/mockrobiota/master/data/mock-25/unite/7-1/99-otus/expected-taxonomy.tsv)

and then import it

If we apply this one the correct way, then we can benchmark the pipeline with a tool like Mockrobiota

#### New issue for Visualize-Ampliseq

We need to re-generate the rooted tree, from [qiime2forum](https://forum.qiime2.org/t/should-i-filter-out-my-mock-community/10238/7):

```md
Not needed. You can take your existing feature-table and rep-seqs.qza file that you got from Deblur or DADA2 and work from there.

    Filter the samples you want from your feature table using the filter-sample 11 plugin.
    Use the new filtered table to remove sequences from your rep-seqs.qza file with the filter-seqs 8 plugin.
    Then you can build your new tree with this new rep-seqs file. You can also use the fragment-insertion plugin for tree building.

In the future, if you just want to exclude some samples from your feature-table you can either a) use the filtering options I mentioned above or simply make a new metadata file with those samples removed. With that regards, any downstream tests you do will just draw from those samples only and ignore the rest. Some tests even let you choose specific groups within your metadata file.
```

#### Check updated output analysis

Based on rev: b5cb1caba1d39fc0218304356c9e8cedbb917b45

cycle 4 rev: 1a7409c996516a2541dea5e45167a5d7236b204d
visualize amp rev: b5cb1caba1d39fc0218304356c9e8cedbb917b45
slurm job: 22906206

```bash
Completed at: 18-May-2023 10:50:48
Duration    : 2m 8s
CPU hours   : 2.1 (98.5% cached)
Succeeded   : 2
Cached      : 36
```

#### Future topic

[Examining longitudinal analysis](https://docs.qiime2.org/2023.2/tutorials/longitudinal/)

#### Concating sequenece and making a reference seq from it

```bash
#singularity shell docker://lorentzb/automate_16_nf:2.0

cd /work/sealab/bjl34716/ade/reference-community
cat *.fasta > atcc_20_ref.fasta
head /work/sealab/bjl34716/ade/reference-community/atcc_20_ref.fasta

qiime tools import \
  --input-path /work/sealab/bjl34716/ade/reference-community/atcc_20_ref.fasta \
  --output-path /work/sealab/bjl34716/ade/reference-community/atcc_20_ref.qza \
  --type 'FeatureData[Sequence]'

biom convert \
  -i reftab.tsv \
  -o expected-taxonomy.biom \
  --table-type="OTU table" \
  --to-json

qiime tools import \
 --type FeatureTable[RelativeFrequency] \
 --input-path expected-taxonomy.biom \
 --input-format BIOMV100Format \
 --output-path /work/sealab/bjl34716/ade/reference-community/expected-taxonomy.qza
```

test the implementation

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: 8e5da0a2b72c473aaa3ffaf315dfaab0e567ed25
slurm job: 22911415

```bash
N E X T F L O W  ~  version 22.04.5
Pulling lorentzben/visualize-ampliseq ...
 Fast-forward
Launching `https://github.com/lorentzben/visualize-ampliseq` [cranky_dijkstra] DSL2 - revision: 8e5da0a2b7 [srs]
Cannot find a component with name 'QIIME2_FILTERONLYSAMPLES' in module: /home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/qiime2_filtersamples.nf

Did you mean any of these?
  QIIME2_FILTERSAMPLES
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: 7220389227bd6d9b746f29c08ec6be670f38acde
slurm job: 22911438

```bash
No such variable: query

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/qiime2_evaluate_seqs.nf' at line: 12 or see '.nextflow.log' file for more details
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: c46d3024390e189e6f792adae72444e9058fc31f
slurm job: 22911467

```bash
No such variable: experimental

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/visualize-ampliseq/modules/local/qiime2_evaluate_composition.nf' at line: 12 or see '.nextflow.log' file for more details
```

cycle 4 rev: 05af9c384a45110b1ad5327aa2dfec247eeb44e8
visualize ampliseq rev: eb4caaca03f2354dd382adc66524e4ca9aa8fa8b
slurm job: 22911528

```bash
Error executing process > 'VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_FILTERSEQS (MOCK)'

Caused by:
  Process `VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_FILTERSEQS (MOCK)` terminated with an error exit status (1)

Command executed:

  export XDG_CONFIG_HOME="${PWD}/HOME"

  qiime feature-table filter-seqs \
      --i-data filtered-sequences.qza \
      --m-metadata-file metadata.tsv \
      --p-where "[Treatment]='MOCK'" \
      --o-filtered-data MOCK.qza

  cat <<-END_VERSIONS > versions.yml
  "VISUALIZE_AMPLISEQ:VISUALIZEAMPLISEQ:QIIME2_FILTERSEQS":
      qiime2: $( qiime --version | sed '1!d;s/.* //' )
  END_VERSIONS

Command exit status:
  1

Command output:
Command error:
  QIIME is caching your current deployment for improved performance. This may take a few moments and should only happen once per deployment.
  /opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
    import pandas.util.testing as pdt
  Plugin error from feature-table:

    All features were filtered out of the data.

  Debug info has been saved to /tmp/qiime2-q2cli-err-lfi56ubp.log

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/06/1dceb4078851b11b1ca42cc9a12dd1

Tip: when you have fixed the problem you can continue the execution adding the option `-resume` to the run command line


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `QIIME is caching your current deployment for improved performance. This may take a few moments and should only happen once per deployment.
/opt/conda/envs/qiime2-2020.8/lib/python3.6/site-packages/skbio/util/_testing.py:15: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
  import pandas.util.testing as pdt
Plugin error from feature-table:

  All features were filtered out of the data.

Debug info has been saved to /tmp/qiime2-q2cli-err-lfi56ubp.log`, size: 517 (max: 255)
"'
```
```

So we are having an issue with filtering the sequences we should go back and use the steps outlied by the qiime forum:

```md

You can take your existing feature-table and rep-seqs.qza file that you got from Deblur or DADA2 and work from there.

    Filter the samples you want from your feature table using the filter-sample 11 plugin.
    Use the new filtered table to remove sequences from your rep-seqs.qza file with the filter-seqs 8 plugin.
    Then you can build your new tree with this new rep-seqs file. You can also use the fragment-insertion plugin for tree building.
```

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Positive Control Analysis
  - Mock Community Investigation
  - Run a proper analysis to send to Ade
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Git Communities

#### Lab notebook

```bash
364b835 - Benjamin Lorentz, Thu May 18 12:05:12 2023 -0400 : notes before lunch
2a3a5cd - Benjamin Lorentz, Thu May 18 08:26:51 2023 -0400 : page for thursday
8923282 - Benjamin Lorentz, Wed May 17 17:01:48 2023 -0400 : final notes for wednesday
```

#### Cycle 4

```bash
05af9c3 - Benjamin Lorentz, Thu May 18 16:16:57 2023 -0400 : rename output
6af5b4c - Benjamin Lorentz, Thu May 18 16:11:03 2023 -0400 : add refSeq and refTab and pass in new parafile
1a7409c - Benjamin Lorentz, Thu May 18 10:49:01 2023 -0400 : update paramfile
```

#### Visualize ampliseq

```bash
eb4caac - Benjamin Lorentz, Thu May 18 16:33:25 2023 -0400 : update qiime2filterseqs
646e015 - Benjamin Lorentz, Thu May 18 16:27:37 2023 -0400 : update evaluate composition
c46d302 - Benjamin Lorentz, Thu May 18 16:25:02 2023 -0400 : update evaluate seqs
7220389 - Benjamin Lorentz, Thu May 18 16:18:56 2023 -0400 : update filtersamples
8e5da0a - Benjamin Lorentz, Thu May 18 16:13:54 2023 -0400 : update visualize-ampliseq and qiime2 evalutate composition
3de75d8 - Benjamin Lorentz, Thu May 18 15:36:05 2023 -0400 : update visualize-ampliseq
2f9ba15 - Benjamin Lorentz, Thu May 18 14:58:11 2023 -0400 : update visualize ampliseq
a44b7ac - Benjamin Lorentz, Thu May 18 14:32:33 2023 -0400 : update visualize-ampliseq
```
---
title: 'Primer Detection Benchmark'
date: 2023-05-26T13:48:22Z
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
  
### Ade

#### Rebuild Figaro for Quay.io

#### Fastp

cycle 4 rev: b24fee34c6208d1f815578670ffd2ff65ed75836
slurm job: 23019292

```bash
Duplication rate: 66.6494%

Insert size peak (evaluated by paired-end reads): 253

JSON report: fastp.json
HTML report: /work/sealab/bjl34716/ade_cycle_1_fastp_report/mock-community_S71_L001

fastp -i /work/sealab/bjl34716/ade_cycle_1/mock-community_S71_L001_R1_001.fastq.gz -I /work/sealab/bjl34716/ade_cycle_1/mock-community_S71_L001_R2_001.fastq.gz -o /work/sealab/bjl34716/ade_cycle_1_fastp_clean_fastq/mock-community_S71_L001.R1.fastq.gz -O /work/sealab/bjl34716/ade_cycle_1_fastp_clean_fastq/mock-community_S71_L001.R2.fastq.gz --detect_adapter_for_pe --correction --overrepresentation_analysis --html /work/sealab/bjl34716/ade_cycle_1_fastp_report/mock-community_S71_L001
fastp v0.23.3, time used: 16 seconds
fastp-trim.sh: error reading input file: Stale file handle
```

fastp: 528 files
prinseq: 528 files 

* thumbs up *



#### Setup new analysis with both cleaned datasets

Prinseq Analysis

cycle 4 rev: 5563d66487fa4bd89861d8f7a0704d8836c7c20f
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23042649

```bash
INFO:    Using cached SIF image
Traceback (most recent call last):
  File "/opt/figaro/figaro/figaro.py", line 218, in <module>
    main()
  File "/opt/figaro/figaro/figaro.py", line 208, in main
    parameters = getApplicationParameters()
  File "/opt/figaro/figaro/figaro.py", line 17, in getApplicationParameters
    return getApplicationParametersFromCommandLine()
  File "/opt/figaro/figaro/figaro.py", line 80, in getApplicationParametersFromCommandLine
    raise NotADirectoryError("Unable to find input directory at %s" %inputDirectory)
NotADirectoryError: Unable to find input directory at ade_cycle_1_prinseq_clean_fastq
Traceback (most recent call last):
  File "/home/bjl34716/ade/cycle-4/figaro-find.py", line 73, in <module>
    main(args)
  File "/home/bjl34716/ade/cycle-4/figaro-find.py", line 49, in main
    cutoffs = parse_figaro(arg.figaro_out)
  File "/home/bjl34716/ade/cycle-4/figaro-find.py", line 25, in parse_figaro
    with open(fig_to_parse) as json_data:
FileNotFoundError: [Errno 2] No such file or directory: 'figaro_prinseq_result/trimParameters.json'
```

cycle 4 rev: d0adfb7ab93c539776b081422024bf040d4e84c2
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23042738

```bash
Traceback (most recent call last):
  File "/opt/figaro/figaro/figaro.py", line 218, in <module>
    main()
  File "/opt/figaro/figaro/figaro.py", line 210, in main
    resultTable, forwardCurve, reverseCurve = trimParameterPrediction.performAnalysisLite(parameters.inputDirectory.value, parameters.minimumCombinedReadLength.value, subsample =  parameters.subsample.value, percentile = parameters.percentile.value, forwardPrimerLength=parameters.forwardPrimerLength.value, reversePrimerLength=parameters.reversePrimerLength.value, namingStandardAlias=fileNamingStandard)
  File "/opt/figaro/figaro/trimParameterPrediction.py", line 448, in performAnalysisLite
    forwardReadLength, reverseReadLength = checkReadLengths(fastqList)
  File "/opt/figaro/figaro/trimParameterPrediction.py", line 380, in checkReadLengths
    fastqReadLengthData = easyMultiprocessing.parallelProcessRunner(parallelReadLengthChecker, fastqList)
  File "/opt/figaro/figaro/easyMultiprocessing.py", line 68, in parallelProcessRunner
    return mapper(processor, itemsToProcess, chunkSize)
  File "/usr/local/lib/python3.6/multiprocessing/pool.py", line 288, in map
    return self._map_async(func, iterable, mapstar, chunksize).get()
  File "/usr/local/lib/python3.6/multiprocessing/pool.py", line 670, in get
    raise self._value
IndexError: list index out of range
Traceback (most recent call last):
  File "/home/bjl34716/ade/cycle-4/figaro-find.py", line 73, in <module>
    main(args)
  File "/home/bjl34716/ade/cycle-4/figaro-find.py", line 49, in main
    cutoffs = parse_figaro(arg.figaro_out)
  File "/home/bjl34716/ade/cycle-4/figaro-find.py", line 25, in parse_figaro
    with open(fig_to_parse) as json_data:
FileNotFoundError: [Errno 2] No such file or directory: 'figaro_prinseq_result/trimParameters.json'
```


cycle 4 rev: b87e4b69f97ae165e835f33ee752360bbf3c6249
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23042804

```bash
multiprocessing.pool.RemoteTraceback:
"""
Traceback (most recent call last):
  File "/usr/local/lib/python3.6/multiprocessing/pool.py", line 119, in worker
    result = (True, func(*args, **kwds))
  File "/usr/local/lib/python3.6/multiprocessing/pool.py", line 44, in mapstar
    return list(map(*args))
  File "/opt/figaro/figaro/trimParameterPrediction.py", line 370, in parallelReadLengthChecker
    return fastq, fastqHandler.estimateReadLength(fastq.filePath, getVariance=True)
  File "/opt/figaro/figaro/fastqHandler.py", line 462, in estimateReadLength
    read = fastq.getNextRead()
  File "/opt/figaro/figaro/fastqHandler.py", line 273, in getNextRead
    readBuffer = read4Lines()
  File "/opt/figaro/figaro/fastqHandler.py", line 264, in read4Lines
    readBuffer[3] = readBuffer[3][self.leftTrim:self.rightTrim]
IndexError: list index out of range
"""

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/opt/figaro/figaro/figaro.py", line 218, in <module>
    main()
  File "/opt/figaro/figaro/figaro.py", line 210, in main
    resultTable, forwardCurve, reverseCurve = trimParameterPrediction.performAnalysisLite(parameters.inputDirectory.value, parameters.minimumCombinedReadLength.value, subsample =  parameters.subsample.value, percentile = parameters.percentile.value, forwardPrimerLength=parameters.forwardPrimerLength.value, reversePrimerLength=parameters.reversePrimerLength.value, namingStandardAlias=fileNamingStandard)
    
    Command error:
  WARNING: Skipping mount /var/singularity/mnt/session/etc/resolv.conf [files]: /etc/resolv.conf doesn't exist in container
  Failed to process LT73_1.fastq.gz
  java.util.zip.ZipException: Not in GZIP format
  	at java.base/java.util.zip.GZIPInputStream.readHeader(GZIPInputStream.java:166)
  	at java.base/java.util.zip.GZIPInputStream.<init>(GZIPInputStream.java:80)
  	at java.base/java.util.zip.GZIPInputStream.<init>(GZIPInputStream.java:92)
  	at uk.ac.babraham.FastQC.Utilities.MultiMemberGZIPInputStream.<init>(MultiMemberGZIPInputStream.java:37)
  	at uk.ac.babraham.FastQC.Sequence.FastQFile.<init>(FastQFile.java:80)
  	at uk.ac.babraham.FastQC.Sequence.SequenceFactory.getSequenceFile(SequenceFactory.java:106)
  	at uk.ac.babraham.FastQC.Sequence.SequenceFactory.getSequenceFile(SequenceFactory.java:62)
  	at uk.ac.babraham.FastQC.Analysis.OfflineRunner.processFile(OfflineRunner.java:159)
  	at uk.ac.babraham.FastQC.Analysis.OfflineRunner.<init>(OfflineRunner.java:121)
  	at uk.ac.babraham.FastQC.FastQCApplication.main(FastQCApplication.java:316)
  Failed to process LT73_2.fastq.gz
  java.util.zip.ZipException: Not in GZIP format
  	at java.base/java.util.zip.GZIPInputStream.readHeader(GZIPInputStream.java:166)
  	at java.base/java.util.zip.GZIPInputStream.<init>(GZIPInputStream.java:80)
  	at java.base/java.util.zip.GZIPInputStream.<init>(GZIPInputStream.java:92)
  	at uk.ac.babraham.FastQC.Utilities.MultiMemberGZIPInputStream.<init>(MultiMemberGZIPInputStream.java:37)
  	at uk.ac.babraham.FastQC.Sequence.FastQFile.<init>(FastQFile.java:80)
  	at uk.ac.babraham.FastQC.Sequence.SequenceFactory.getSequenceFile(SequenceFactory.java:106)
  	at uk.ac.babraham.FastQC.Sequence.SequenceFactory.getSequenceFile(SequenceFactory.java:62)
  	at uk.ac.babraham.FastQC.Analysis.OfflineRunner.processFile(OfflineRunner.java:159)
  	at uk.ac.babraham.FastQC.Analysis.OfflineRunner.<init>(OfflineRunner.java:121)
  	at uk.ac.babraham.FastQC.FastQCApplication.main(FastQCApplication.java:316)

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/7d/bc5a5cf3c4bedef65677f30b215cb5

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`
```

we need to compress the output to fastq.gz

updated dockerfile to include parallel rerunning primer-trimming:

TODO come back to this process

cycle 4 rev: 15c66f2089dc1745a7f5890d8647eaf672ca876e 
slurm job: 23044093

```bash
INFO:    Using cached SIF image
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
gzip: /work/sealab/bjl34716/ade_cycle_1_prinseq_clean_fastq/*: No such file or directory
```

cycle 4 rev: 369a02f3135fdce9bd6b5c744f52a8758063f59c
slurm job: 23044827

```bash
INFO:    Using cached SIF image
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
gzip: /work/sealab/bjl34716/ade_cycle_1_prinseq_clean_fastq/*.fastq: No such file or directory
```

cycle 4 rev: 8a3a50f002b1e3ea5df422d9403a989f0f4bc907
slurm job: 23045006

```bash
INFO:    Using cached SIF image
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
^_<8B>^H^@^@^@^@^@^@^C^C^@^@^@^@^@^@^@^@^@/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
/usr/bin/bash: line 1: /work/sealab/bjl34716/ade_cycle_1_prinseq_clean_fastq/1-0_S193_L001_R1_001.fastq: Permission denied
```


cycle 4 rev: 844f04f430da394e9afaa966e931b1205f68224e
slurm job: 23045460

```bash
INFO:    Using cached SIF image
/usr/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
gzip: /work/sealab/bjl34716/ade_cycle_1_prinseq_clean_fastq/*.fastq: No such file or directory
```

cycle 4 rev: 11ec7308685dc135fea473ea88db77c93ef82fc0
slurm job: 23046096

```bash
```

Removing Figaro, do we need to update params?

Fastp Analysis


cycle 4 rev: 3880fe7df5754a7f62b417a6f315975a534a493f
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23043358

```bash
Empty header columns are not allowed in CSV file
```

cycle 4 rev: dd0c5c78368ede54eb4046f0937fa4d2290f72c0
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23043398

```bash
Use DADA2 taxonomy classification
ERROR: Please check input samplesheet -> Forward read FastQ file does not exist!
/work/sealab/bjl34716/ade_cycle_1_fastp_clean_fastq2-21_S266_L001.R1.fastq.gz
```

cycle 4 rev: bb86aa6f52019f4af18ec113f8e4ec3c9d903151
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23043483

```bash
No such file: /scratch/bjl34716/ade/cycle-4/litter-fastp/overall_summary.tsv


No such file: /scratch/bjl34716/ade/cycle-4/litter-fastp/dada2/ASV_tax_species.tsv


No such file: /scratch/bjl34716/ade/cycle-4/litter-fastp/qiime2/phylogenetic_tree/rooted-tree.qza


No such file: /scratch/bjl34716/ade/cycle-4/litter-fastp/qiime2/abundance_tables/feature-table.biom


No such file: /scratch/bjl34716/ade/cycle-4/litter-fastp/qiime2/representative_sequences/filtered-sequences.qza


No such file: /scratch/bjl34716/ade/cycle-4/litter-fastp/qiime2/abundance_tables/feature-table.tsv



cp: cannot stat ‘/home/bjl34716/ade/cycle-4/litter/primer-detect/figaro_fastp_result’: No such file or directory
```

cycle 4 rev:  369a02f3135fdce9bd6b5c744f52a8758063f59c
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23044970

```bash
```

#### Generating an Analysis for Ade

cycle 4 rev:  3097ad09135b2099bd7a6f0a9ab065163f0e4946
visualize ampliseq srs rev: c6b07c621749576e0cd35813d7861d2a5573da36
slurm job: 23046627

```bash
```

#### Ben's Other analysis

What steps did he take?

- 

What steps do I take?

-

#### Report for Dr. Ade

- update the TODO #TODO save these contams to disk so we can examine them in contam_script.r
- understand how good the mock community analysis is
- Describe the difference between SRS and Longitudinal analysis



#### Longitudinal Analysis

See if it makes a difference in this specific analysis. 


### Questions to ask for new analysis

- What primers did you use for amplification?
- What region were you targeting?
- What sequencer did you use?
- What kind of extraction did you perform? (Kit manual etc)
- Do you have nanodrop/qubit 


### Todos for Next Week

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - compare fastp and prinseq analyses
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
  - Run a proper analysis to send to Ade
    - Create Report
      - NC
      - Mock Quality
      - Why SRS?
  - Longitudinal Analysis By hand
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  
### Git Commits

#### Lab Notebook

```bash
d10f437 - Benjamin Lorentz, Fri May 26 12:04:01 2023 -0400 : notes before lunch
16b222a - Benjamin Lorentz, Fri May 26 10:16:52 2023 -0400 : add page for friday
883e8ba - Benjamin Lorentz, Thu May 25 17:13:08 2023 -0400 : final notes for thursday
```

#### Cycle 4

```bash
b4dba1f - Benjamin Lorentz, Fri May 26 16:35:43 2023 -0400 : add markdown report
3097ad0 - Benjamin Lorentz, Fri May 26 15:33:52 2023 -0400 : add new params for figaro-nc-mock-srs-viz analysis
a518ad6 - Benjamin Lorentz, Fri May 26 15:00:17 2023 -0400 : fix command
11ec730 - Benjamin Lorentz, Fri May 26 14:39:30 2023 -0400 : just change to dir and then gzip
844f04f - Benjamin Lorentz, Fri May 26 14:06:18 2023 -0400 : dont try to parallelize
8a3a50f - Benjamin Lorentz, Fri May 26 13:38:14 2023 -0400 : fix the order for parallel
369a02f - Benjamin Lorentz, Fri May 26 13:14:40 2023 -0400 : fix pathname for gzip
15c66f2 - Benjamin Lorentz, Fri May 26 12:34:34 2023 -0400 : update primer-trim.sh
bb86aa6 - Benjamin Lorentz, Fri May 26 11:43:28 2023 -0400 : fix mapping file fastp
dd0c5c7 - Benjamin Lorentz, Fri May 26 11:37:53 2023 -0400 : update fastp mapping
3880fe7 - Benjamin Lorentz, Fri May 26 11:33:24 2023 -0400 : update primer-trimming
28cd67c - Benjamin Lorentz, Fri May 26 11:15:58 2023 -0400 : update driver scripts
:...skipping...
b4dba1f - Benjamin Lorentz, Fri May 26 16:35:43 2023 -0400 : add markdown report
3097ad0 - Benjamin Lorentz, Fri May 26 15:33:52 2023 -0400 : add new params for figaro-nc-mock-srs-viz analysis
a518ad6 - Benjamin Lorentz, Fri May 26 15:00:17 2023 -0400 : fix command
11ec730 - Benjamin Lorentz, Fri May 26 14:39:30 2023 -0400 : just change to dir and then gzip
844f04f - Benjamin Lorentz, Fri May 26 14:06:18 2023 -0400 : dont try to parallelize
8a3a50f - Benjamin Lorentz, Fri May 26 13:38:14 2023 -0400 : fix the order for parallel
369a02f - Benjamin Lorentz, Fri May 26 13:14:40 2023 -0400 : fix pathname for gzip
15c66f2 - Benjamin Lorentz, Fri May 26 12:34:34 2023 -0400 : update primer-trim.sh
bb86aa6 - Benjamin Lorentz, Fri May 26 11:43:28 2023 -0400 : fix mapping file fastp
dd0c5c7 - Benjamin Lorentz, Fri May 26 11:37:53 2023 -0400 : update fastp mapping
3880fe7 - Benjamin Lorentz, Fri May 26 11:33:24 2023 -0400 : update primer-trimming
28cd67c - Benjamin Lorentz, Fri May 26 11:15:58 2023 -0400 : update driver scripts
b87e4b6 - Benjamin Lorentz, Fri May 26 11:10:15 2023 -0400 : revert driver scripts back to docker images       
d0adfb7 - Benjamin Lorentz, Fri May 26 11:01:33 2023 -0400 : update prinseq driver script
5563d66 - Benjamin Lorentz, Thu May 25 16:49:54 2023 -0400 : update driver scripts
```
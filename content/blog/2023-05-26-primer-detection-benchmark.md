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

cycle 4 rev: 3880fe7df5754a7f62b417a6f315975a534a493f
slurm job: 23043349

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

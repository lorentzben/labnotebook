---
title: What is in store for the next three weeks?
author: Ben Lorentz
date: '2022-11-28'
slug: what-is-in-store-for-the-next-three-weeks
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

### Todos for Today:

- Examine htseq-count results slurm 32753
  - do we have to use --stranded reverse
- rebuild the supplemental tables 1-5 with my results
- Run DESeq2 analysis on htseq-count table
- Visualize Ampliseq
  - examine slurm run 15474870
  

### Todos for the next 3 weeks

- Tillocca
  - look at references and see if we can get a generalized taxa table
  - from the taxa table functionally annotate the 'role' of the taxa present in each segment
    - they may have done some of this heavy lifting for us.
- continue reading jones
- re-watch the lecture for ChIP-seq

---

- BIOSQL, SQL or Mongo DB tutorials
- Genome Assembly from Isolates
- Kelly Shotgun Metagenomic Data
- good example 16s data to hone parameters
- read reviews from Tilocca


### Term Paper

#### HTSeq Results

My stranded run of HTSeq finished, the first 10 samples were:

```bash
__no_feature	 837,913 	 1,438,667 	 820,673 	 596,775 	 804,096 	 1,617,511 	 1,242,342 	 1,018,854 	 981,628 	 445,457 
__ambiguous	 53,450 	 48,773 	 46,669 	 50,376 	 87,731 	 203,050 	 177,131 	 196,491 	 111,786 	 129,193 
__too_low_aQual	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   
__not_aligned	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   
__alignment_not_unique	 89,387 	 85,359 	 88,898 	 53,845 	 64,953 	 169,247 	 126,048 	 105,992 	 123,139 	 59,342 
										
features identified	 2,502,453 	 3,045,008 	 2,510,114 	 2,779,690 	 3,889,834 	 8,069,813 	 6,098,785 	 2,797,380 	 4,531,590 	 2,209,577 

__no_feature	 3,323,458 	 4,451,168 	 3,318,584 	 3,372,089 	 4,695,139 	 9,650,167 	 7,293,153 	 3,658,924 	 5,504,214 	 2,638,871 
__ambiguous	 673 	 867 	 607 	 633 	 2,619 	 4,612 	 2,625 	 5,197 	 1,691 	 1,277 
__too_low_aQual	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   
__not_aligned	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   	 -   
__alignment_not_unique	 89,387 	 85,359 	 88,898 	 53,845 	 64,953 	 169,247 	 126,048 	 105,992 	 123,139 	 59,342 
										
features identified	 69,685 	 80,413 	 58,265 	 54,119 	 83,903 	 235,595 	 222,480 	 348,604 	 119,099 	 144,079 
```

I think the last thing I want to do is to run stranded reversed and confirm. A third option is:

```bash
Important: For paired-end reads, although position-sorted BAM files are supported, unsorted BAM files (i.e. in which the two reads of the pair are in consecutive lines of the BAM file) are highly recommended for htseq-count. If you are having trouble or unexpected results, sort your BAM file by name and try again.

Most of my RNA-Seq reads are counted as ``__no_feature``. What could have gone wrong?
Common causes include: - The --stranded option was set wrongly. Use a genome browser (e.g., IGV) to check. - The GTF file uses coordinates from another reference assembly as the SAM file. - The chromosome names differ between GTF and SAM file (e.g., chr1 in one file and jsut 1 in the other).
```

There is another stranded package called [RSeQC](https://github.com/MonashBioinformaticsPlatform/RSeQC#quick-start), I am going to try to collect this and install on the teach cluster.

![IGV Image](https://lorentznotebook.netlify.app/2022-11-28-what-is-in-store-for-the-next-three-weeks/IGV_SRR8265630.png)

#### RSeQC

command to make virtual env

```bash
virtualenv -p python3 rseqc
```

conda env for virtualenv.yaml

```bash
name: virtualenv
channels:
  - defaults
dependencies:
  - _libgcc_mutex=0.1=main
  - _openmp_mutex=5.1=1_gnu
  - bzip2=1.0.8=h7b6447c_0
  - ca-certificates=2022.10.11=h06a4308_0
  - certifi=2022.9.24=py310h06a4308_0
  - ld_impl_linux-64=2.38=h1181459_1
  - libffi=3.4.2=h6a678d5_6
  - libgcc-ng=11.2.0=h1234567_1
  - libgomp=11.2.0=h1234567_1
  - libstdcxx-ng=11.2.0=h1234567_1
  - libuuid=1.41.5=h5eee18b_0
  - ncurses=6.3=h5eee18b_3
  - openssl=1.1.1s=h7f8727e_0
  - python=3.10.8=h7a1cb2a_1
  - readline=8.2=h5eee18b_0
  - setuptools=65.5.0=py310h06a4308_0
  - sqlite=3.40.0=h5082296_0
  - tk=8.6.12=h1ccaba5_0
  - tzdata=2022f=h04d1e81_0
  - wheel=0.37.1=pyhd3eb1b0_0
  - xz=5.2.6=h5eee18b_0
  - zlib=1.2.13=h5eee18b_0
  - pip:
    - distlib==0.3.6
    - filelock==3.8.0
    - pip==22.3.1
    - platformdirs==2.5.4
    - virtualenv==20.17.0
prefix: /home/bjl34716/miniconda/envs/virtualenv
```

The revision that installed successfully was [e5acdd52db4dc3a276baf2f7376e4cba31c71851](https://github.com/MonashBioinformaticsPlatform/RSeQC/commit/e5acdd52db4dc3a276baf2f7376e4cba31c71851)

We want to use the script [infer_experiment.py](https://github.com/MonashBioinformaticsPlatform/RSeQC/blob/master/rseqc/modules/infer_experiment.py) this module would not load or run so I am going to try [check-strand](https://github.com/tjbencomo/check-strand)

#### Check-Strand

Based on the script check-strand.py from the repo above most of the strands are reversed, so I think that's the way to go.

```bash
name: check-strand
channels:
  - bioconda
  - defaults
dependencies:
  - _libgcc_mutex=0.1=main
  - _openmp_mutex=5.1=1_gnu
  - blas=1.0=mkl
  - bottleneck=1.3.5=py310ha9d4c09_0
  - bzip2=1.0.8=h7b6447c_0
  - ca-certificates=2022.10.11=h06a4308_0
  - certifi=2022.9.24=py310h06a4308_0
  - hdf5=1.10.2=hba1933b_1
  - intel-openmp=2021.4.0=h06a4308_3561
  - kallisto=0.44.0=h7d86c95_2
  - ld_impl_linux-64=2.38=h1181459_1
  - libffi=3.4.2=h6a678d5_6
  - libgcc-ng=11.2.0=h1234567_1
  - libgfortran-ng=7.5.0=ha8ba4b0_17
  - libgfortran4=7.5.0=ha8ba4b0_17
  - libgomp=11.2.0=h1234567_1
  - libstdcxx-ng=11.2.0=h1234567_1
  - libuuid=1.41.5=h5eee18b_0
  - mkl=2021.4.0=h06a4308_640
  - mkl-service=2.4.0=py310h7f8727e_0
  - mkl_fft=1.3.1=py310hd6ae3a3_0
  - mkl_random=1.2.2=py310h00e6091_0
  - ncurses=6.3=h5eee18b_3
  - numexpr=2.8.4=py310h8879344_0
  - numpy=1.23.4=py310hd5efca6_0
  - numpy-base=1.23.4=py310h8e6c178_0
  - openssl=1.1.1s=h7f8727e_0
  - packaging=21.3=pyhd3eb1b0_0
  - pandas=1.5.1=py310h1128e8f_0
  - pip=22.2.2=py310h06a4308_0
  - pyparsing=3.0.9=py310h06a4308_0
  - python=3.10.8=h7a1cb2a_1
  - python-dateutil=2.8.2=pyhd3eb1b0_0
  - pytz=2022.1=py310h06a4308_0
  - readline=8.2=h5eee18b_0
  - setuptools=65.5.0=py310h06a4308_0
  - six=1.16.0=pyhd3eb1b0_1
  - sqlite=3.40.0=h5082296_0
  - tk=8.6.12=h1ccaba5_0
  - tzdata=2022f=h04d1e81_0
  - wheel=0.37.1=pyhd3eb1b0_0
  - xz=5.2.6=h5eee18b_0
  - zlib=1.2.13=h5eee18b_0
prefix: /home/bjl34716/miniconda/envs/check-strand
```

```bash
$ python3 ../determine_strand/check-strand/check-strand.py -i Galgal4 metadata_strand.csv

fq1,fq2,strand
SRR8265548_1.fastq.gz,SRR8265548_2.fastq.gz,reverse
SRR8265550_1.fastq.gz,SRR8265550_2.fastq.gz,reverse
SRR8265621_1.fastq.gz,SRR8265621_2.fastq.gz,reverse
SRR8265623_1.fastq.gz,SRR8265623_2.fastq.gz,reverse
SRR8265625_1.fastq.gz,SRR8265625_2.fastq.gz,reverse
SRR8265627_1.fastq.gz,SRR8265627_2.fastq.gz,reverse
SRR8265629_1.fastq.gz,SRR8265629_2.fastq.gz,reverse
SRR8265549_1.fastq.gz,SRR8265549_2.fastq.gz,reverse
SRR8265591_1.fastq.gz,SRR8265591_2.fastq.gz,reverse
SRR8265622_1.fastq.gz,SRR8265622_2.fastq.gz,reverse
SRR8265624_1.fastq.gz,SRR8265624_2.fastq.gz,reverse
SRR8265626_1.fastq.gz,SRR8265626_2.fastq.gz,reverse
SRR8265628_1.fastq.gz,SRR8265628_2.fastq.gz,reverse
SRR8265630_1.fastq.gz,SRR8265630_2.fastq.gz,reverse
SRR8265558_1.fastq.gz,SRR8265558_2.fastq.gz,reverse
SRR8265560_1.fastq.gz,SRR8265560_2.fastq.gz,reverse
SRR8265562_1.fastq.gz,SRR8265562_2.fastq.gz,reverse
SRR8265633_1.fastq.gz,SRR8265633_2.fastq.gz,reverse
SRR8265635_1.fastq.gz,SRR8265635_2.fastq.gz,reverse
SRR8265637_1.fastq.gz,SRR8265637_2.fastq.gz,reverse
SRR8265639_1.fastq.gz,SRR8265639_2.fastq.gz,reverse
SRR8265557_1.fastq.gz,SRR8265557_2.fastq.gz,reverse
SRR8265559_1.fastq.gz,SRR8265559_2.fastq.gz,reverse
SRR8265561_1.fastq.gz,SRR8265561_2.fastq.gz,reverse
SRR8265634_1.fastq.gz,SRR8265634_2.fastq.gz,reverse
SRR8265636_1.fastq.gz,SRR8265636_2.fastq.gz,reverse
SRR8265638_1.fastq.gz,SRR8265638_2.fastq.gz,reverse
SRR8265640_1.fastq.gz,SRR8265640_2.fastq.gz,reverse
SRR8265592_1.fastq.gz,SRR8265592_2.fastq.gz,reverse
SRR8265594_1.fastq.gz,SRR8265594_2.fastq.gz,reverse
SRR8265596_1.fastq.gz,SRR8265596_2.fastq.gz,reverse
SRR8265598_1.fastq.gz,SRR8265598_2.fastq.gz,reverse
SRR8265600_1.fastq.gz,SRR8265600_2.fastq.gz,reverse
SRR8265654_1.fastq.gz,SRR8265654_2.fastq.gz,reverse
SRR8265659_1.fastq.gz,SRR8265659_2.fastq.gz,reverse
SRR8265593_1.fastq.gz,SRR8265593_2.fastq.gz,reverse
SRR8265595_1.fastq.gz,SRR8265595_2.fastq.gz,reverse
SRR8265597_1.fastq.gz,SRR8265597_2.fastq.gz,reverse
SRR8265599_1.fastq.gz,SRR8265599_2.fastq.gz,reverse
SRR8265653_1.fastq.gz,SRR8265653_2.fastq.gz,reverse
SRR8265660_1.fastq.gz,SRR8265660_2.fastq.gz,reverse
SRR8265631_1.fastq.gz,SRR8265631_2.fastq.gz,reverse
SRR8265652_1.fastq.gz,SRR8265652_2.fastq.gz,reverse
SRR8265656_1.fastq.gz,SRR8265656_2.fastq.gz,reverse
SRR8265658_1.fastq.gz,SRR8265658_2.fastq.gz,reverse
SRR8265632_1.fastq.gz,SRR8265632_2.fastq.gz,reverse
SRR8265651_1.fastq.gz,SRR8265651_2.fastq.gz,reverse
SRR8265655_1.fastq.gz,SRR8265655_2.fastq.gz,reverse
SRR8265657_1.fastq.gz,SRR8265657_2.fastq.gz,reverse
SRR8265554_1.fastq.gz,SRR8265554_2.fastq.gz,reverse
SRR8265556_1.fastq.gz,SRR8265556_2.fastq.gz,reverse
SRR8265612_1.fastq.gz,SRR8265612_2.fastq.gz,reverse
SRR8265614_1.fastq.gz,SRR8265614_2.fastq.gz,reverse
SRR8265616_1.fastq.gz,SRR8265616_2.fastq.gz,reverse
SRR8265618_1.fastq.gz,SRR8265618_2.fastq.gz,reverse
SRR8265620_1.fastq.gz,SRR8265620_2.fastq.gz,reverse
SRR8265553_1.fastq.gz,SRR8265553_2.fastq.gz,reverse
SRR8265555_1.fastq.gz,SRR8265555_2.fastq.gz,reverse
SRR8265611_1.fastq.gz,SRR8265611_2.fastq.gz,reverse
SRR8265613_1.fastq.gz,SRR8265613_2.fastq.gz,reverse
SRR8265615_1.fastq.gz,SRR8265615_2.fastq.gz,reverse
SRR8265617_1.fastq.gz,SRR8265617_2.fastq.gz,unstranded
SRR8265619_1.fastq.gz,SRR8265619_2.fastq.gz,reverse
```

#### Re-run HTSeq2

revision: 4673b5b60ad4e04e0889121a95b22f60c59d328d
slurm: 33056

```bash

```

### Host Microbiome Interaction

I read Bergen 2009 and ingested it into the repo, it is more related to pigs and humans. I read more of the jones paper. 

### Todos for Tomorrow:

- Examine htseq-count results slurm 33056
  - do we have to use --stranded reverse; yes.
- rebuild the supplemental tables 1-5 with my results
- Run DESeq2 analysis on htseq-count table
- Visualize Ampliseq
  - examine slurm run 15474870
  

### Git Commits

#### Gene 8940 Term Paper

```bash
4673b5b - Benjamin Lorentz, Mon Nov 28 16:36:18 2022 -0500 : changed htseq to reverse for stranded
```

#### Host Microbiome Interaction

```bash
dba844a - Benjamin Lorentz, Mon Nov 28 10:24:26 2022 -0500 : add bergen 2009 paper to citations
```

#### Lab Notebook

```bash
3dc9385 - Benjamin Lorentz, Mon Nov 28 11:49:57 2022 -0500 : add image
a90cf72 - Benjamin Lorentz, Mon Nov 28 09:01:17 2022 -0500 : add page for monday
```


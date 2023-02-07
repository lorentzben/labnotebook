---
title: 'Understanding Meta Maps'
date: 2023-02-07T13:56:40Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - add in the isolate field into parser and output
  - meet with Ben to talk about two points above 2/2/23
- gg-catalog
  - Zhang
    - create a minimap process (either concat or separate)
      - read about what a meta map is and if we can implement it
    - check for read loss (does it match the paper?)
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### gg-catalog-nf

#### what is a meta map?

The information below comes from [nf-core docs](https://nf-co.re/docs/contributing/modules#what-is-the-meta-map)

The object type is a [groovy map](https://www.tutorialspoint.com/groovy/groovy_maps.htm). 

A meta map is structured like this:

```groovy
// meta map
meta_map = [
    [id: 'test', single_end: false], // meta map
    [/my/data/SRR493366_1.fastq, /my/data/SRR493366_2.fastq]
]
```

There is a function [SAMPLESHEET_CHECK](https://github.com/nf-core/rnaseq/blob/587c61b441c5e00bd3201317d48b95a82afe6aaa/subworkflows/local/input_check.nf#L23-L45) which will create a metamap for the reads from a csv file. We can refactor my process to use this.

#### Implementing samplesheet_check

FutureNote there are modules for samtools!

```bash
 samtools/ampliconclip                                 │
│ samtools/bam2fq                                       │
│ samtools/calmd                                        │
│ samtools/collate                                      │
│ samtools/collatefastq                                 │
│ samtools/convert                                      │
│ samtools/depth                                        │
│ samtools/dict                                         │
│ samtools/faidx                                        │
│ samtools/fasta                                        │
│ samtools/fastq                                        │
│ samtools/fixmate                                      │
│ samtools/flagstat                                     │
│ samtools/getrg                                        │
│ samtools/idxstats                                     │
│ samtools/index                                        │
│ samtools/markdup                                      │
│ samtools/merge                                        │
│ samtools/mpileup                                      │
│ samtools/sort                                         │
│ samtools/stats                                        │
│ samtools/view
```

Can we use the parse sheet that we have implemented? or Do we have to use the 'new' one?

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: a65e70f4008b4a99139eb6f0795b539d9b1567fc
slurm sub: 18579614 

```bash
ch_reads.view()
[[id:SRR15214153, single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: a49a9a2c925afc308d673bc0a17b54f441138705
slurm sub: 18580205

```bash
[[id:[id:SRR15214153, single_end:true], single_end:true], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
```

This isn't quite what we want, what we want is closer to 

[[id:SRR15214153, single_end:true], [],[/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: b809e60339eef42d375c8ff17d85446cab98aefe
slurm sub: 18580665

```bash
[[id:SRR15214153, single_end:true], [], [/scratch/bjl34716/gg-catalog/zhang/reads/cecum/SRR15214153.fastq]]
```

This looks like what we could be looking for 

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 939805c703f6046cadf9e89c4f39e1472f2ae0d1
slurm sub: 18581105

```bash
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
Missing process or function with name 'FILTLONG'

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 92 or see '.nextflow.log' file for more details
```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: e4b6ea02410ba9bd2cf31f3cc8d7c3feb806a185
slurm sub: 18581374

```bash
No such variable: info

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/parse_input.nf' at line: 60 or see '.nextflow.log' file for more details
No such variable: Exception evaluating property 'dual' for nextflow.script.ChannelOut, Reason: groovy.lang.MissingPropertyException: No such property: dual for class: groovyx.gpars.dataflow.DataflowBroadcast
Possible solutions: head

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 109 or see '.nextflow.log' file for more details
No such variable: info

```


gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 87afd9268a39ed58fcee84e67bbe3da0418933f4
slurm sub: 18582792

```bash
Pulling Singularity image https://depot.galaxyproject.org/singularity/filtlong:0.2.1--h9a82719_0 [cache /scratch/bjl34716/singularity/depot.galaxyproject.org-singularity-filtlong-0.2.1--h9a82719_0.img]
Invalid method invocation `call` with arguments: [id:SRR15214153, single_end:true] (java.util.LinkedHashMap) on _closure9 type


WARN: Tower request field `workflow.errorMessage` exceeds expected size | offending value: `No signature of method: Script_824c2fbf$_runScript_closure1$_closure3$_closure9.call() is applicable for argument types: (LinkedHashMap) values: [[id:SRR15214153, single_end:true]]
Possible solutions: any(), any(), doCall(groovy.lang.Tuple), any(groovy.lang.Closure), each(groovy.lang.Closure), tap(groovy.lang.Closure)`, size: 319 (max: 255)
[fa/898530] Cached process > MINIMAP2_INDEX (1)
```

It looks like this process is going!

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 99ca86af0f99a66a269ad9241c28ac3e0f0105d8
slurm sub: 18583334

```bash
Feb-07 16:50:04.562 [Task monitor] DEBUG n.processor.TaskPollingMonitor - Task completed > TaskHandler[jobId: 18583433; id: 3; name: FILTLONG (SRR19683890); status: COMPLETED; exit: 140; error: -; workDir: /scratch/bjl34716/nf_dev/gg-catalog/work/10/c282556a2175a28172de84931f51df started: 1675785003943; exited: 2023-02-07T21:49:48Z; ]
Feb-07 16:51:04.563 [Task monitor] DEBUG n.processor.TaskPollingMonitor - Task completed > TaskHandler[jobId: 18583474; id: 6; name: FILTLONG (SRR19736685); status: COMPLETED; exit: 140; error: -; workDir: /scratch/bjl34716/nf_dev/gg-catalog/work/a1/7457215db7d0040b1b067a720837f8 started: 1675785063929; exited: 2023-02-07T21:50:18Z; ]
Feb-07 16:51:04.616 [main] DEBUG nextflow.Session - Session await > all barriers passed
```

I think this timed out

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: dc8f550e9d2554470bfe39c5f2a67398edeecf60
slurm sub: 18610158

```bash
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.log]
[[id:SRR19732729, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/a3/c70037853d4f88163ea1c618a68d60/SRR19732729.log]
[[id:SRR19683891, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/52/bb6f1fa9fb318ce7d5d2b310f7e3f8/SRR19683891.log]
Execution cancelled -- Finishing pending tasks before exit
Execution aborted due to an unexpected error

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/modules/nf-core/minimap2/align/main.nf' at line: 2 or see '.nextflow.log' file for more detai$

```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 358a425c5719dcf84e3616e4296b43e4556d6620
slurm sub: 18610193

```bash
java.lang.NullPointerException: Cannot get property 'id' on null object
```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: 8dca95c36a2624d8cefdee266e3129d69dc21fb4
slurm sub: 18610222

```bash
-- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/subworkflows/local/contam_input.nf' at line: 60 or see '.nextflow.log' file for more details
Access to 'MINIMAP2_ALIGN.out' is undefined since the process 'MINIMAP2_ALIGN' has not been invoked before accessing the output attribute

 -- Check script '/home/bjl34716/.nextflow/assets/lorentzben/gg-catalog-nf/main.nf' at line: 106 or see '.nextflow.log' file for more details
[-        ] process > FILTLONG       -
[-        ] process > MINIMAP2_INDEX -

```

gg-catalog rev: 100ef9b13f4a7de3246709c7327c522e90f0bb57
gg-catalog-nf rev: e1278972655c5d3a9c38d853c2556856e7aee742
slurm sub: 18610239

```bash
[a3/c70037] process > FILTLONG (SRR19732729) [ 75%] 3 of 4, cached: 3
[fa/898530] process > MINIMAP2_INDEX (1)     [100%] 1 of 1, cached: 1 ✔
[-        ] process > MINIMAP2_ALIGN         -
[[id:SRR15214153, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/04/9731d4e4998e55cee8ffcd6801d02d/SRR15214153.fastq.gz]
[[id:combined, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/fa/8985309130258a2e58dc2c8d66168e/concat-gal-zea-glycine.fna.mmi]
Execution cancelled -- Finishing pending tasks before exit
[[id:SRR19683891, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/52/bb6f1fa9fb318ce7d5d2b310f7e3f8/SRR19683891.fastq.gz]
[[id:SRR19732729, single_end:true], /scratch/bjl34716/nf_dev/gg-catalog/work/a3/c70037853d4f88163ea1c618a68d60/SRR19732729.fastq.gz]
Execution aborted due to an unexpected error
```

I think we have to map the it.last() for those...

#### How is the relative abundance calculated

The abundance calculation came from the paper [A human gut microbial gene catalog established by metagenomic sequencing](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3779803/). 

The exact wording from the supps is:

***Relative abundance of microbial genomes among individuals of the cohort.***

We computed the genome coverage by uniquely mapping Illumina reads and normalized it to 1 Gb of sequence, to correct for different sequencing levels in different individuals. The coverage was summed over all species of the nonredundant bacterial genome set for each individual and the proportion of each species relative to the sum calculated

from the Huang paper:

To calculate of relative gene abundance, the clean reads from each sample were aligned against the gene catalog by BWA-MEM with the criteria of alignment length ≥ 50 bp and identity > 95%. Sequenced-based abundance profiling was performed as previously described.

Phylum, genus, species, KO, and OG relative abundances were calculated by summing the abundance of the respective genes belonging to each category per sample, based on the taxonomic assignments, KO and OG annotations, respectively. 


### Jackwood Blast Parser

I cannot use my hacky "sci_res = soup_sci.findAll("gbseq_organism")" since the tag is "GBQualifier_name" which is all of them!

so I found a parser that makes sense from [Stack Overflow](https://stackoverflow.com/questions/2148119/how-to-convert-an-xml-string-to-a-dictionary)

```python3
from lxml import objectify as xml_objectify


def xml_to_dict(xml_str):
    """ Convert xml to dict, using lxml v3.4.2 xml processing library """
    def xml_to_dict_recursion(xml_object):
        dict_object = xml_object.__dict__
        if not dict_object:
            return xml_object
        for key, value in dict_object.items():
            dict_object[key] = xml_to_dict_recursion(value)
        return dict_object
    return xml_to_dict_recursion(xml_objectify.fromstring(xml_str))
    
id_list = 'G999695,MN548286,AY789941,KU556805'

sci_req = requests.get('https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=nuccore'+api_key+'&id='+id_list+'&retmode=xml').content

# pulls out all gbqualifier names and values

qualifiers = soup_sci.findAll("gbqualifier")

# turns gbqualifier names and values into a dict
xml_dict = [xml_to_dict(str(elem)) for elem in qualifiers]

def list_of_dict_to_dict(xml_dict_list):
   res_dict = {}
   for dict in xml_dict_list:
      try:
         new = {list(dict.values())[0]:list(dict.values())[1]}
         res_dict.update(new)
      except IndexError:
         pass
    return res_dict
  
res_dict.get('isolate')
```

TODO need to implement these methods into the qualifiers, and then generate a third dictionary that is the isolate name/count?

### Todos for Tomorrow

- Jackwood Blast
  - implement the two xml parsers
  - create a new dict that holds isolate counts
  - meet with Ben to talk about two points above 2/9/23
- gg-catalog
  - Zhang
    - follow up on slurm process 18610239
    - create a minimap process (either concat or separate)
      - read about what a meta map is and if we can implement it
    - check for read loss (does it match the paper?)
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community
  
### Git Commits

#### Lab notebook

```bash
bd6c4a0 - Benjamin Lorentz, Tue Feb 7 08:57:48 2023 -0500 : added page for tuesday
```

#### gg-catalog-nf

```bash
8dca95c - Benjamin Lorentz, Tue Feb 7 17:32:55 2023 -0500 : update main.nf
358a425 - Benjamin Lorentz, Tue Feb 7 17:28:28 2023 -0500 : update main.nf \n print out the reads first to see what the issue is
dc8f550 - Benjamin Lorentz, Tue Feb 7 17:22:12 2023 -0500 : update modules.config
99ca86a - Benjamin Lorentz, Tue Feb 7 10:49:06 2023 -0500 : update main.nf
87afd92 - Benjamin Lorentz, Tue Feb 7 10:46:01 2023 -0500 : update main.nf
e4b6ea0 - Benjamin Lorentz, Tue Feb 7 10:35:56 2023 -0500 : update main.nf
939805c - Benjamin Lorentz, Tue Feb 7 10:33:46 2023 -0500 : update main.nf and modules.config
b809e60 - Benjamin Lorentz, Tue Feb 7 10:28:09 2023 -0500 : update main.nf
a49a9a2 - Benjamin Lorentz, Tue Feb 7 10:20:51 2023 -0500 : update main.nf
a65e70f - Benjamin Lorentz, Tue Feb 7 10:13:40 2023 -0500 : update main.nf
```


#### Jackwood Parser

```bash
4d516bb - Benjamin Lorentz, Tue Feb 7 17:13:18 2023 -0500 : update blast_parser.py
1a564c2 - Benjamin Lorentz, Tue Feb 7 15:12:18 2023 -0500 : update main.nf and env_vars.sh
```

 

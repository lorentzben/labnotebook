---
title: 'Generating My Tables'
date: 2023-02-27T15:21:02Z
draft: false
meta_img: "images/image.png"
tags:
  - "metamap"
  - "minimap2"
  - "nextflow"
  - "MAGs"
  - "filtlong"
  - "csvtk"
  - "seqkit"
description: "Description for the page"
---

### Todos for Today

- Ade 
  - find out what version was last used 
  - send code 
- Stat 6220 
  - Homework 2 (ask prof about last question)
- Jackwood Blast
  - meet Ben and Brian TBD
- gg-catalog
  - Zhang
    - check for read loss (does it match the paper?)
      - kinda, but not really
    - fix the mapping method to match the paper 
    - formula for relative abundance
    - what is involved in clean-up
    - calculate relative abundance for zhang data
  - Huang
    - compare to zhang data
  - Other short read results
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Ade 

#### Which version was last used to generate her result files?

I got this email from Ade:

```md
Hope you are doing well. I know it has been a while since you helped performing the 16S analysis on our data.

I was wondering if you could share the code or the methods used for the analysis you performed. 

Also, can you provide us the ASV table including the taxonomy. 
```

The last email I sent to her was:

```md
Here are the reports for day 21 and day 28 with the Treatments in the order we discussed, I think it does look better. 
 
[Day 21](https://outlookuga-my.sharepoint.com/personal/bjl34716_uga_edu/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fbjl34716%5Fuga%5Fedu%2FDocuments%2FAggrey%2Fcycle%5F4%2Fday%5F21%5F50%5Fperc%5Fcorrect%5Forder%2Ehtml&parent=%2Fpersonal%2Fbjl34716%5Fuga%5Fedu%2FDocuments%2FAggrey%2Fcycle%5F4&ga=1)
[Day 28](https://outlookuga-my.sharepoint.com/personal/bjl34716_uga_edu/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fbjl34716%5Fuga%5Fedu%2FDocuments%2FAggrey%2Fcycle%5F4%2Fday%5F28%5F60%5Fperc%5Fioi%5Fordered%2Ehtml&parent=%2Fpersonal%2Fbjl34716%5Fuga%5Fedu%2FDocuments%2FAggrey%2Fcycle%5F4&ga=1)

```

I want to confirm that my current pipeline gives the same results but the git revision that corresponds to these report is [82bf6d435ddb6d4467708e21fc1920d57cd8ad11](https://github.com/lorentzben/automate_16_nf/tree/82bf6d435ddb6d4467708e21fc1920d57cd8ad11)

[the main method](https://github.com/lorentzben/automate_16_nf/blob/82bf6d435ddb6d4467708e21fc1920d57cd8ad11/main.nf)

#### Double check that the results match

I am uploading the data currently, I need to figure out which datasheet is useable.

I can find the metadata for Day 21 but I do not have the day 28 sheet right now. 

He wants a table too, so we need to re-gen the data anyway. I set up a [git repo](https://github.com/lorentzben/cycle-4) to help with this 



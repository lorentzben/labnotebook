---
title: 'Regmi Daily Time Budget'
date: 2023-10-11T13:43:51Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat 8200"
  - "regmi-rfid"
description: "Description for the page"
---

### Todos for Today

- Reply to Shailes

- Class
  - Lab 5

- Sweden
  - Keni's response about UWB for Aggrey
  - Consolidate notes for class
  - read this paper: [https://pubmed.ncbi.nlm.nih.gov/31434210/](https://pubmed.ncbi.nlm.nih.gov/31434210/)
  
- Regmi
  - RFID
    - Build a daily and nightly time budget function
    - Create a plot that shows the average amount of time each bird spends in a zone
    - Statistically Compare the daytime and nighttime proportions.
    - Send to Regmi
  - Microbiome Work
    - Make script to get from raw data to QZAs
    - Compile all params I'm gonna need
    - Make a doc to import data into:
      - QIIME2
      - Phyloseq
      -biopython
  - Heat Stress
    - Re-Run the heat stress analysis to see what the results look like
    - New subset with 9-5/6pm
    - Is there a better way to analyze this type of data
      - What did Lars/Ana/the rest send?
      
- gg-catalog
  - better formatted table so that the clarity is better.
  - what ammino acids are being processed in each segment
    - valine is processed in the duodenum but not the jejunum
  - gene network of all keggs in one network for each tissue
  - go into the literature; gene catalogs for a biological process in an organism.
      - Need to compare/remove the common genes/processes 

- Read papers about microbiome analysis
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation 

### RFID

```{r}
data2$day <- (format(data2$datetime, "%H:%M") > "05:00" & format(data2$datetime, "%H:%M") < "21:59")
night <- data2[data2$day != TRUE,]
night_int <- timeToIntervals(night)

getTimeBudgetProp(night_int)

```

Do we need a new timeToIntervals that is day aware?

POM 1: Make day and night tables

rfid rev: 5c8ba359a93e7db14d7912abe4175add5e1e08c7

I want to add a column for day or night, and a column for date, a column for day of study and a column for week of study at least for the "raw data"

I started this implementation but did not finish it.

POM 2: make day and night record functions

rfid rev: 7e99f2fa14765ca7b2643498ad35f3f7c604b135

```{r diagnostic code}
test_seq <- tsibble(seq(ymd_hms("1997/1/1 00:00:01"), ymd_hms("1997/1/1 23:59:01"), by="hour"))

#test
#test_seq$day <- rep("yes", length(test_seq$"<dttm>"))

start_day <- "05:00"
end_day <- "22:00"

test_seq$day <- (format(test_seq$"<dttm>", "%H:%M") >= start_day & format(test_seq$"<dttm>", "%H:%M") < end_day)

```

Diagnostics for my getDayRecords and my getNightRecords

```{r}
data <- room_2_interval$sampled[[1]]
```
I want to add in the extra columns

rfid rev: f27f8af531a06803a6ad8bb0be5bd3ff659ac8a4 

POM 3: Make days so that we can turn that into day tables

I want to add a column for day or night, and a column for date, a column for day of study and a column for week of study at least for the "raw data"

```{r}
day <- room_2_all_room_day$day[[1]]

day$date <- format(day$datetime, "%Y/%m/%d")

```

rfid-rev: 0401dc08f244345220a22b3d6adcc208c903ff6d

POM 4: More modifications in day table


```{r}
day <- room_2_all_room_day$day[[1]]


```

rfid-rev: ba006deb1e8c4268c5786e26b2986aa31fdf0cc2 

POM 5: Include Dos and wos into day and night table

POMS 6-??:

We were able to separate the days out into separate interval tables and caught some edge cases (where there was no transitions for a whole day or if there was only one transition for the day)

TODO we need to decide how to return the data and make it work nice with the time budget function. 

### Git Commits

#### Regmi RFID

```bash
c09c4a0 - Benjamin Lorentz, Wed Oct 11 17:45:38 2023 -0400 : TODO in the nestedtimetointervals function
2ceeb50 - Benjamin Lorentz, Wed Oct 11 17:39:04 2023 -0400 : separate day interval tables generated
ba006de - Benjamin Lorentz, Wed Oct 11 15:58:46 2023 -0400 : added dos and wos columns
0401dc0 - Benjamin Lorentz, Wed Oct 11 15:30:24 2023 -0400 : pom 3: more modifications in getDayRecords
f27f8af - Benjamin Lorentz, Wed Oct 11 15:05:23 2023 -0400 : pom2: separate out day and night tables
7e99f2f - Benjamin Lorentz, Wed Oct 11 14:34:35 2023 -0400 : pom 1 finish
5c8ba35 - Benjamin Lorentz, Wed Oct 11 14:18:41 2023 -0400 : Update just-room-2-time-analysis.Rmd
```



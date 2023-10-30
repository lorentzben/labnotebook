---
title: '2023 10 30 Continue Unit Test'
date: 2023-10-30T13:32:27Z
draft: false
meta_img: "images/image.png"
tags:
  - "regmi-rfid"
description: "Description for the page"
---

### RFID

to convert epoch to human read

```excel
=(((B5/60)/60)/24)+DATE(1970,1,1)
```

rev: 8abf9c7418c6f5611bf30a96ff9515751edfa4ec
Line 457

```bash
data <-  d1t2_all_room_day$day[[1]]

tmp <- nestedTimeToIntervals(d1t2_all_room_day$day[[1]])
> tmp$daily_int[[1]]
          t1         t2 from_zone to_zone
1 1616580587 1616582279      <NA>  middle
2 1616582279 1616593805    middle  bottom
# should be
1616580587 1616582279 NA middle
1616582279 1616593805 middle bottom
```

The tricky bit is the transition happens at the transition from night to day... So we need to change this but save it as an edge case. 

rev: e7c02390a498023c571b97dba2ab1461eadf8370 

```r
# what we got
> d1t3_overall_interval$interval[[1]]
          t1         t2 from_zone to_zone
1 1616609120 1616617203      <NA>  middle
2 1616617203 1616618947    middle     top
3 1616618947 1616630273       top  middle
# what we expected
1616609122 1616617203 na middle
1616617203 1616618947 middle top
1616618947 1616629105 top middle
1616629105 1616630273 middle top

data <- d1t3_regular$sampled[[1]]
timeToIntervals(data)
``

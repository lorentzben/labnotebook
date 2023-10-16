---
title: 'Unit testing'
date: 2023-10-16T13:08:49Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat 8200"
  - "regmi-rfid"
description: "Description for the page"
---

### Regmi RFID

There's still an issue with the night data:

```bash
room_2_all_room_day$night_int[[1]]$daily_int[[4]]
    t1         t2 from_zone to_zone
1 <NA> 1613951995      <NA>  bottom
> room_2_all_room_day$night_int[[1]]$daily_int[[5]]
    t1         t2 from_zone to_zone
1 <NA> 1614038395      <NA>  bottom
> room_2_all_room_day$night_int[[1]]$daily_int[[6]]
    t1         t2 from_zone to_zone
1 <NA> 1614124795      <NA>  bottom
```

I forgot my external HDD at home today so I had to make a copy of the data on work laptop:

C:\Users\bjl34716\regmi\RFID_bird_tracking

One Issue is: 

```bash
room_2_all_room_day$night_int[[1]]$daily_int

[[77]]
    t1         t2 from_zone to_zone
1 <NA> 1620259195      <NA>  bottom

> room_2_all_room_day$night_int[[1]]$by_day[[77]]
# A tsibble: 5,062 x 3 [1s] <UTC>
   datetime            value  day
   <dttm>              <chr>  <lgl>
 1 2021-05-05 00:00:00 bottom FALSE
 2 2021-05-05 00:00:05 bottom FALSE
 3 2021-05-05 00:00:10 bottom FALSE
 4 2021-05-05 00:00:15 bottom FALSE
 5 2021-05-05 00:00:20 bottom FALSE
 6 2021-05-05 00:00:25 bottom FALSE
 7 2021-05-05 00:00:30 bottom FALSE
 8 2021-05-05 00:00:35 bottom FALSE
 9 2021-05-05 00:00:40 bottom FALSE
10 2021-05-05 00:00:45 bottom FALSE
# … with 5,052 more rows
```

Okay so night function right now is busted, we need to split morning_night and night_night and then to join across the datetime. 

Here's an updated issue: 

```bash
room_2_all_room_day$night_int[[1]]$daily_int[[69]]
          t1         t2 from_zone to_zone
1       <NA> 1618793425      <NA>  bottom
2 1618793425 1618808395    bottom  middle

[[85]]
    t1         t2 from_zone to_zone
1 <NA> 1620017995      <NA>  bottom
```

ID #5
1. Check room_2_all_room_day$night[[5]]$night_int to see if records make sense?

they look good to me 

2. Check that the tsibbles of dos make sense.

this also looks good to me. 


I was able to generate daily and night time time budgets. Now I need to figure out what is a nice way to examine the data. 

Then figuring out how to examine each room effect and some kind of stats. 



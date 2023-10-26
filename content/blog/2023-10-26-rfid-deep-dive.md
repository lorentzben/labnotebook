---
title: 'Rfid Deep Dive'
date: 2023-10-26T13:35:12Z
draft: false
meta_img: "images/image.png"
tags:
  - "regmi-rfid"

description: "Description for the page"
---

We need to update/fix the room 8 and 11 code

Room 2 analysis

rev: 3866244fdcb8be181ed3829a905188425d5cbfbb

```bash
Room 2 Looks good
```

Room 3 Analysis

rev: 0f553521bb5ab79891d130345858f031405b09f5

```bash
x-axis on Daily Time Budget for Room 3 is still not working
```

rev: c397c93fdf419aeb06ec44ab9f77e76b18347cd0

```bash
x-axis on Daily Time Budget for Room 3 is still not working
```

rev: 8eecd07c29d574f9cf3cf73c629df0aeb93c50e6

```bash
putting it after night makes it work for some reason
```

Room 8 Analysis

rev: 2ae665b754cfd3a77610d57d7c144205b86be1de 

``bash
Warning message:
Removed 1677 rows containing missing values (geom_bar).
Saving 7 x 7 in image
Warning message:
Removed 1894 rows containing missing values (geom_bar).
```
Needed to remove 6941

rev: 29d42ea7bba0973bc83f1a525acfee3a1bf38be3

``bash
looks good except for the y axis on concat analysis
```

rev: da5106addfc3a3a2b81e50e3b3fe9d691521b38c

``bash
looks good
```

Room 11 Analysis

rev: c418279129dd5d5d46df2d7a304af8a31ac95542

``bash
Need to fix the count in room 11 for joined tables
```

rev: 9398d4c0ae314712213bbff4d4f10f1ac48637aa

``bash
LGTM
```

Run all individual analyses

rev: 4946358b7e47e0f181eff920609c47310b48ee1a

``bash
LGTM
````

Concat Analysis Script

rev: 228b02cc845f21fa683c0d37415eeefa55f43287

```bash
```

We want the table before it is fed into the time budget function:
  - we want this overall 
  - and for day and night
  - compare adding day and night to overall and see if we get the same result.

Saved interval tables to disk, generating them, then need to use room 2 to test if both sets are equivalent

rev: 8369ca4b47fc9db7a0bc69fb3d3b4ebcc6d01d8

```bash
```

rev: beb18145a363e84bcebcfaa60faff0beb004e2cc

```bash
the count is inflated for some reason...
```

```r
> min(rm_2_nest_overall_int$data[[3]]$t1)
[1] 1613691000
> max(rm_2_nest_overall_int$data[[3]]$t1)
[1] 1620314364



```

Check that room_2_all_room_day$day + room_2_all_room_day$night = room_2_interval$sampled 

```r
> length(room_2_all_room_day$day[[6]]$datetime) + length(room_2_all_room_day$night[[6]]$datetime)
[1] 1332471

> length(room_2_interval$sampled[[6]]$datetime)
[1] 1332471
```

Check that room_2_all_room_day$day_int + room_2_all_room_day$night_int == timeToIntervals(room_2_all_room_day)

```r
> timeToIntervals(room_2_all_room_day$day[[6]])
> timeToIntervals(room_2_all_room_day$night[[6]])

> timeToIntervals(room_2_all_room_day$sampled[[6]]) == room_2_all_room_day$interval[[6]]

> (rm_2_overall$ntrans - (rm_2_day$ntrans + rm_2_night$ntrans))
 [1]  -86 -101  -35  -92 -125   -2 -145 -109  -83 -139
```

```r
> length(room_2_all_room_day$sampled[[6]]$datetime)
[1] 1332471

> length(room_2_all_room_day$day[[6]]$datetime)
[1] 943907

> length(room_2_all_room_day$night[[6]]$datetime)
[1] 388564

length(room_2_all_room_day$day[[6]]$datetime) + length(room_2_all_room_day$night[[6]]$datetime)

> (length(room_2_all_room_day$day[[6]]$datetime) + length(room_2_all_room_day$night[[6]]$datetime)) == length(room_2_all_room_day$sampled[[6]]$datetime)
[1] TRUE
```

Something is not quite right in the timeToIntervals 

the day and night separation is correct but the count of transitions is incorrect, also we need to change the start and end. 


### Git Commits

#### Labnotebook

```bash
e86f90e - Benjamin Lorentz, Thu Oct 26 12:05:10 2023 -0400 : added page for Thursday
```

#### RFID Bird Tracking

```bash
15af66a - Benjamin Lorentz, Thu Oct 26 16:57:28 2023 -0400 : final updates for thurs
beb1814 - Benjamin Lorentz, Thu Oct 26 15:54:05 2023 -0400 : add joint_analysis.r update driverscript      
8369ca4 - Benjamin Lorentz, Thu Oct 26 15:23:01 2023 -0400 : update room 3,8,11 and driver
d99c21a - Benjamin Lorentz, Thu Oct 26 15:21:18 2023 -0400 : saved interval tables to disk
228b02c - Benjamin Lorentz, Thu Oct 26 14:27:55 2023 -0400 : update room 2, driver and cleanup
3d7c2f5 - Benjamin Lorentz, Thu Oct 26 14:16:55 2023 -0400 : started saving interval tables to disk
4946358 - Benjamin Lorentz, Thu Oct 26 13:31:55 2023 -0400 : update driver.sh
9398d4c - Benjamin Lorentz, Thu Oct 26 13:26:00 2023 -0400 : update room_2,3,8,11_analysis
c418279 - Benjamin Lorentz, Thu Oct 26 12:54:48 2023 -0400 : only room 11 analysis
da5106a - Benjamin Lorentz, Thu Oct 26 12:04:16 2023 -0400 : change y lim of concat to 18 birds
29d42ea - Benjamin Lorentz, Thu Oct 26 11:52:47 2023 -0400 : room 8 removed 6941
2ae665b - Benjamin Lorentz, Thu Oct 26 11:41:16 2023 -0400 : room 8 run
8eecd07 - Benjamin Lorentz, Thu Oct 26 11:32:07 2023 -0400 : move day after night to see if that makes a difference
c397c93 - Benjamin Lorentz, Thu Oct 26 11:24:38 2023 -0400 : use the night stacked bar since the xaxis works
0f55352 - Benjamin Lorentz, Thu Oct 26 11:06:16 2023 -0400 : Call room 3
0535db3 - Benjamin Lorentz, Thu Oct 26 10:55:43 2023 -0400 : update indvl scripts
3866244 - Benjamin Lorentz, Thu Oct 26 10:36:38 2023 -0400 : add driver and cleanup script
```
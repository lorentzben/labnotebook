---
title: 'Continue Unit Test Happy Halloween'
date: 2023-10-31T13:31:42Z
draft: false
meta_img: "images/image.png"
tags:
  - "regmi-rfid"
description: "Description for the page"
---

### RFID



rev: a2b6b1addf56c5bf9b052c07550d7a54666ec32a

```bash
Error: d2t0 expect last record t2 is beginning of day not equal to as.numeric(tail(d2t0_all_room_day$day[[1]]$datetime, n = 1)).
1/1 mismatches
[1] 1.62e+09 - 1.62e+09 == -62675
```

rev: 87fd765e3b30e638739de2c465000cc684636823

```bash
all tests pass
```

rev: 8fdeeb154e6d74ad9943bc020ccedd5ef98d534f 

```bash
> expect_equal(unique(d3t0_all_room_day$night[[1]]$dos), c(1,2,3) , label='d3t0 unique dos night counts')
Error: d3t0 unique dos night counts not equal to c(1, 2, 3).
3/3 mismatches (average diff: 1)
[1] 0 - 1 == -1
[2] 1 - 2 == -1
[3] 2 - 3 == -1
> d3t0_all_room_day$night[[1]]

data <- d3t0_overall_interval$slicedTsibble[[1]]
```

rev: 0dfd881cd717f3882742e9774ba1285076bc57a9

```bash
all tests pass
```

rev: 9c12b37d0a41cfd49f1452a11c2746dea1b59329 

```bash
Error: d3t2 sliced tsibble valuecol not equal to c("top", "bottom", "middle").
2/3 mismatches
x[2]: "middle"
y[2]: "bottom"

x[3]: "bottom"
y[3]: "middle"
Execution halted
```

rev: 7a07a9770e8ff52f1add19426cccf8b5a5f5252b

```bash
all tests pass
```

rev: 246b941444c469a49b2d8e5496ce8b0eefcd901d

```bash
Error: d3t3 sliced tsibble valuecol not equal to c("top", "middle", "bottom").
2/3 mismatches
x[1]: "middle"
y[1]: "top"

x[2]: "top"
y[2]: "middle"
Execution halted
```

rev: 57e3774759f528050af5cff08e5d7e27956199d7

```bash
all tests pass
```

### End Unit Tests ###

### Speed up runtime

rev: 091dda940367a3a030b27cea2af1afd868341b3f

```bash
> room_2_all_room_time_budget$night_tb

[[8]][[37]]
          Interval.1.         Interval.2.  X1  X2  X3
1 2021-03-31 22:56:05 2021-03-31 22:56:05 NaN NaN NaN
```

Regmi sent me this email:

"Hi Ben,
I was able to check the video from the RFID birds. The lights went off at 8:30 pm and came on at 4:30 am. Birds took roughly about 30 to 45 minutes to settle after the lights went out.

If it's possible to analyze the data between 10 pm to 4 am, we should be able to capture the night time (sleep) space occupancy.
Let me know if you have any questions or if you want to discuss further. I think it might a good idea for you to briefly look at the videos as well just to get an idea of what we are looking at. Let me know and I can hand you the hard drive.

"

Tomorrow:

We need to go into like:
unique(room_2_all_room_day$night[[8]]$dos)
and to write a function that gives a value to missing DOS so that it is able to be plotted. 
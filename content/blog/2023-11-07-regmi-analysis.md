---
title: 'Regmi Analysis'
date: 2023-11-07T14:34:02Z
draft: false
meta_img: "images/image.png"
tags:
  - "regmi-rfid"
description: "Description for the page"
---

### RFID 


The only thing is a weird artificat if there is a 1 for the first day, I changed line 200 to be 0,1,2,3 as opposed to 0,1,2,3

I was able to fix the code up and have started the analysis to compare high and low activity nesting zones which we can pick up on Monday

rev: b6bf593aa71cd92214b12839981ded91cae84b8e

```bash
all tests pass and all figures generate ok. 1
```

rev: 

```bash
data <- high_act_night_tb$data[[3]]

> print(night_org_table, n=70)
# A tibble: 36 × 4
   tagname ntrans    rm activity
     <dbl>  <dbl> <dbl> <chr>
 1    6929      4     8 low
 2    6988      6     2 low
 3    6939      8     8 low
 4    6942     28     2 low
 5    6931     29     8 low
 6    6950     68     8 low
 7    6997     70     8 low
 8    6996     86     8 low
 9    9042     89    11 low
10    6925    119     2 medium
11    6945    125     8 medium
12    6961    125     8 medium
13    6928    131     8 medium
14    9019    137     2 medium
15    6940    146     8 medium
16    9001    151     2 medium
17    6979    156     8 medium
18    7000    164     8 medium
19    6922    169     3 medium
20    6973    179     8 medium
21    6935    195     2 medium
22    6989    205     2 medium
23    9050    219    11 medium
24    9026    220     2 medium
25    9023    225     8 medium
26    9012    235     8 medium
27    6981    256     2 medium
28    9038    257    11 high
29    6982    274     8 high
30    6984    302     8 high
31    6913    306     8 high
32    6992    311     3 high
33    6934    340     3 high
34    9013    400     3 high
35    6976   1207     3 high
36    6980   1425     3 high
> print(overall_org_table, n=70)
# A tibble: 35 × 4
   tagname ntrans    rm activity
     <dbl>  <dbl> <dbl> <chr>
 1    6929    190     8 low
 2    6988    195     2 low
 3    6939    200     8 low
 4    6942    225     2 low
 5    6996    225     8 low
 6    6997    240     8 low
 7    9042    252    11 low
 8    6961    255     8 low
 9    6945    269     8 medium
10    6986    278     2 medium
11    6950    425     8 medium
12    9023    492     8 medium
13    6989    527     2 medium
14    9050    545    11 medium
15    9001    550     2 medium
16    6940    559     8 medium
17    6979    564     8 medium
18    9019    597     2 medium
19    6925    638     2 medium
20    7000    657     8 medium
21    6935    660     2 medium
22    9026    716     2 medium
23    9038    762    11 medium
24    6982    818     8 medium
25    9012    833     8 medium
26    6981    839     2 medium
27    6922    888     3 high
28    6973   1028     8 high
29    6913   1040     8 high
30    6984   1101     8 high
31    6992   1262     3 high
32    6934   2076     3 high
33    6976   2548     3 high
34    9013   3428     3 high
35    6980   4072     3 high
```

I was able to find the low, medium and high activity birds based on the overall interval table. I also was able to make a table where each row was a week tied to a bird id. 

Next Steps:
- make a low med high classification for each room
- compare each zone time spent to time and bird id and see if the utilization changes over time. 
- share some results with Regmi 
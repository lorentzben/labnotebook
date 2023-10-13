---
title: 'Unit Testing'
date: 2023-10-13T14:55:14Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat 8200"
  - "regmi-rfid"
description: "Description for the page"
---


### Regmi RFID


```{r eval=FALSE}

checkNTrans <- function(big_data,id, len){
  
  return_table <- data.frame()
  
  for(i in 1:len){
    data <- big_data$day_int[[id]]$by_day[[i]]
    first_entry <- head(data,n=1)
    transition_into <- data[which(data$value != dplyr::lag(data$value)),]
    transition_from <- data[which(data$value != dplyr::lag(data$value))-1,]
    last_entry <- tail(data,n=1)
    
    if((first_entry$value == last_entry$value) & length(transition_into$value) == 0 ){
        count = 0
        case <- "no_trans"
    } else if(length(transition_into$value) == 1 &  tail(transition_into,n=1)$value == last_entry$value){
      # if there is only one transition from beginning
      count <- length(transition_into$value)
      case <- "trans_into_len_one"
    } else if(tail(transition_into,n=1)$value == last_entry$value){
        # count length plus the first transition
        # This does not catch the 2 transtion case
        count <- length(transition_into$value)+1
        case <- "len_trans_into_plus_first"
    } else {
      # transition from first to transition into and then into end since last
      count <- length(transition_into$value) + 2
      case <- "should_not_happen"
    }
    
    new_row <- c(i, count,case)
    return_table <- rbind(return_table, new_row)
  }
    
  return(return_table)
}
  
fake_data <- room_2_all_room_day$day_int[[2]]$by_day[[14]]
two_trans <- bind_rows(fake_data[10,],transition_into,tail(fake_data,n=1))
two_trans[3,2] <- "top"

```

if last_entry$zone == tail(transition_into, n=1)$zone{
  set last entry of transition time as the last entry timepoint 
} else {
  append the last entry though should not be used since it would get caught by the which
}

Case 1 Many Transitions: 

five_transitions <- room_2_all_room_day$day_int[[1]]$by_day[[1]]

Case 2 No transitions during the day:

zero_transitions <- room_2_all_room_day$day_int[[1]]$by_day[[27]]

Case 3 One transition during the day:

one_transition <- room_2_all_room_day$day_int[[2]]$by_day[[14]]

Case 4 Two transitions during the day:

Case 5 Three Transitions during the day: 

three_transitions <- <- room_2_all_room_day$day_int[[1]]$by_day[[2]]


We have to figure out where time to Intervals breaks: 

theres still an issue with the night data:

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

### Git commits

#### RFID Analysis

```bash
5f78e21 - Benjamin Lorentz, Fri Oct 13 16:48:17 2023 -0400 : day nestedtime to intervals function works but issue with nighttime function
97af93a - Benjamin Lorentz, Fri Oct 13 14:55:24 2023 -0400 : retooling the time to intervals function
05c89bd - Benjamin Lorentz, Fri Oct 13 11:16:32 2023 -0400 : update just 2
e326920 - Benjamin Lorentz, Thu Oct 12 17:42:37 2023 -0400 : updates for thursday
```

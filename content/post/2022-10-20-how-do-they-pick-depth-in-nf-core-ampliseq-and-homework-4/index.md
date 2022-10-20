---
title: How do they pick depth in nf-core/ampliseq, and homework 4
author: Ben Lorentz
date: '2022-10-20'
slug: []
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

Todos for today:
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- Update repo for Homework for this week
  - do homework 4
- Pick a meeting time with Dr. Bergman
- Attend Seminar about avian influenza @ 3pm
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Check in on classifier still running
- update WSL2 packages locally

### Homework 4

I've been working on the assignment for homework 4 which is varient calling but only for SNPs and indels. 
I think I've gotten most of the code figured out, but I still want to confirm the BCFtools commands to see the decrease in features to make sure everything is run correctly. 

This plus making sure the words in the github issue are also correct. 

### Avian Influenza
2022 High Path Eurasian Strain (only the second time in history)

in 1996 in geese in asia H5N1, Goose Guangdong and now we are seeing a descendant it became global because of migrations. 

in 2015 there was enough circulation in Asia to get into Siberia and into BC Canada, worst animal disease outbreak in US History. Stayed in 3 west flyways.

2021 Big concentration in western europe, in both wild and domestic birds. Infection continued through summer, weather had no difference. Ducks and geese get material into the environment and then can circulate in chickens and then this can go back into the wild birds. They now have a poultry-specifically adapted virus and continue to migrate. 

First NA case was in Very America Great Black Gull, it was in the same area as a european migratory group. 

There is a lot of virus in all 4 flyways. 
GA wildlife die offs 
Die offs/susceptible Black Vulture Lesser scaup Bald Eagle. Raptors (eat small birds), Gulls (share migratory space) Shore Birds, Geese Swans, Ducks, Owls robins, grackle, redwing blackbird. 

Special interest Black Vulture Turkey Vulture and wild turkey 
Symptoms:  cant fly doesn't fear people
Mammals are also getting infected, raccoon, opossum, skunk, red fox coyote 
Marine Mammals, grey seal, harbor seals, poupous in the flyway

Almost double the detection this year and 54% are outside which means more external exposure. 
2015 was feet to feet lateral spread. 
85% of cases in 2022 come from wild birds, as an industry we're better at stopping farm to farm exposure. 

The source of virus is everywhere. In 2015 there were almost no broiler cases, but now 11 cases as of Oct 9. 
Increase mortality, decreased production, decreased water consumption, errily quiet birds.  

Foot bath to clean and keep outside out and inside in. 
The solutions are inexpensive but require a change in behavior, it seems like not if but when an outbreak occurs. Vaccination is off the table for now due to trade partners but may be discussed soon.

Todos for tomorrow:
- Wrap Up Homework 4
  - Check the BCF tools intermediates
  - Run Mpileup without the quality filter
  - Write up the words part of the section
- What is a core microbiome?
  - Can we use this to find the major players in chicken gut segments?
- Look into genomic type project for class (see project description)
  - Reach out to Dr. Aggrey to see if he approves of idea or has an alternative.
- Understand how sampling depth is determined for ampliseq
- Implement chunk 06
- Check in on classifier still running

### Git Commits

#### Lab Notebook

```bash
50dcb1c - Benjamin Lorentz, Thu Oct 20 09:08:07 2022 -0400 : added page for thursday
89c7499 - Benjamin Lorentz, Wed Oct 19 17:02:57 2022 -0400 : end of wednesday
```

#### Gene 8940 Homework

```bash
cd2f7b0 - Ben Lorentz, Thu Oct 20 15:23:41 2022 -0400 : updated homeowork4
9c85569 - Ben Lorentz, Thu Oct 20 14:36:47 2022 -0400 : Update homework_4.sh
1c0602b - Ben Lorentz, Thu Oct 20 14:35:45 2022 -0400 : added some intermediate files
90f90f1 - Ben Lorentz, Thu Oct 20 14:21:50 2022 -0400 : Update homework_4.sh
aa13c64 - Ben Lorentz, Thu Oct 20 14:10:06 2022 -0400 : Update homework_4.sh
dad29a3 - Ben Lorentz, Thu Oct 20 14:06:06 2022 -0400 : Update homework_4.sh
1a6cd73 - Ben Lorentz, Thu Oct 20 13:59:19 2022 -0400 : Update homework_4.sh
24a75f7 - Ben Lorentz, Thu Oct 20 12:02:11 2022 -0400 : Update homework_4.sh
cbba4f6 - Ben Lorentz, Thu Oct 20 11:58:58 2022 -0400 : Update homework_4.sh
9e62269 - Ben Lorentz, Thu Oct 20 11:55:11 2022 -0400 : Update homework_4.sh
168f501 - Ben Lorentz, Thu Oct 20 11:53:03 2022 -0400 : Update homework_4.sh
b481330 - Ben Lorentz, Thu Oct 20 11:47:40 2022 -0400 : Update homework_4.sh
925f468 - Ben Lorentz, Thu Oct 20 11:34:58 2022 -0400 : Update homework_4.sh
87ee8e3 - Ben Lorentz, Thu Oct 20 11:29:35 2022 -0400 : Update homework_4.sh
f67f86a - Ben Lorentz, Thu Oct 20 11:21:16 2022 -0400 : Update homework_4.sh
64678cb - Ben Lorentz, Thu Oct 20 11:13:29 2022 -0400 : Update homework_4.sh
e8cc0c6 - Ben Lorentz, Thu Oct 20 11:03:52 2022 -0400 : Update homework_4.sh
126cd28 - Ben Lorentz, Thu Oct 20 10:59:52 2022 -0400 : Update homework_4.sh
dd14f92 - Ben Lorentz, Thu Oct 20 10:49:59 2022 -0400 : Update homework_4.sh
c69a1e5 - Ben Lorentz, Thu Oct 20 10:26:19 2022 -0400 : added homework 4 script
```
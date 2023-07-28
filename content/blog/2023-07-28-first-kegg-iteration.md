---
title: 'Module 13; First Kegg Iteration'
date: 2023-07-28T12:56:59Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat 6315"
  - "microbiome-review"
  - "kegg ontology network"
  - "gg-catalog"
description: "Description for the page"
---


### Todos for Tomorrow

- gg-catalog
  - Make Tissue, then Pathway, then gene specific tables
  - Select top 25 most abundant genes from these tables
 
  
- Read papers about microbiome analysis

- Look into ggpicrust2 for shailes

- STAT 6315
  - Fill out Survey for Exam next week
  - Watch Module 13
  - Finish Module 13 Homework
  
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
  
### Stat 6313

13.1a two-way anova and interaction

Two explanitory variable. Interaction is in play. 

Overall mean, two factors and the interaction of the factors and then the error condition.

8 combinations of treatments. 

across all meat conditions, does the effect appear to be approximatly the same, if there approx same then no interaction but if differences great interaction

the effect across the meat conditions, appears to be somewhat similar. we will probably find that these two factors (oven setting and meat condition) do not interact to affect the mean response. 

temperature (3 levels)
material type (3 levels)

response is battery life

the effect across the three temperatures does not seem to be similar. we will probably find that temperature and material type interact to affect the mean battery life. 

13.1b cooking energy part 1

independence, not matched pairs; the 40 roasts were randomly assigned to the eight treatment combinations.

normality:

the normal quantile plot of residuals is approximately linear which indicates the normality condition is plausible. 

constant variance: 

The BF p-value is 0.7875 > 0.1 therefore the constant varianace condition is plausible. 


can be structured as a one-way anova of treatment combinations

13.1c cooking energy part 2

check conditions

test equal means for the treatment conditions

H0: the mean fuel required is the same for all 8 combinations of oven setting and meat condition
Ha: at least two differ

F = 11.1186 p-value < 0.0001

Conclusion:
There is enough evidence to conclude the mean fuel required is different for at least two combinations of oven setting and meat condition.

13.1d cooking energy part 3

Step 3 test for interaction

H0: oven setting and meat condition do not interact to affect the mean fuel required.
Ha: oven setting and meat condition do interact to affect the mean fuel required. 

F = 1.6658 p-value= 0.1940

fail to reject H0, there is not enough evidence to conclude oven setting and meat condition interact to affect the mean fuel required. 

13.1e battery life part 1

Independence: not matched pairs; the batteries should have been randomly assigned to the temperature and plate material combinations

Constant Variance: The BF p-value = 0.6081 > 0.1 therefore the constant variance condition is plausible

Normality: The normal quantile plot of residuals adequately follows a straight line pattern indicating the normality condition is plausible 

13.1f battery life part 2

H0: the mean battery life is the same for all 9 combinations of temperature and plate material 
Ha: the mean battery life if different for at least two of these combinations of temperature and plate material.

F: 10.9995 p-value < 0.0001

there is enough evidence to conclude the mean battery life is different for at least two combinations of temperature and plate material. 

H0: temperature and plate material do not interact to affect the mean battery life.
Ha: temperature and plate material do interact to affect mean battery life. 

test stat: 3.5595
p-value: 0.0186
conclusion: reject H0, there is enough evidence to conclude temperature and plate mateiral interact to affect mean battery life. 

use one way anova model to make multiple comparisons based on the treatment combinations.

13.2a cooking energy

oven setting 
h0 the mean fuel required is the same for the two oven settings. 
Ha the mean fuel required is not the same for the two oven settings. 

F = 1.5235 p-value=0.2261

fail to reject h0 there is not enough evidence to conclude the mean fuel required is different for the two oven settings.

Don't make multiple comparisons. 

meat condition

h0 the mean fuel required is the same for all four meat conditions
ha the mean fuel required is different for at least two meat conditions

F= 23.933 p-value <0.0001 

reject H0, there is enough evidence to conclude the mean fuel required is different for at least two meat conditions. 

The mean fuel required is significantly lowest for a fresh roast
The mean fuel required is signficantly different for a frozen roast than one that has thawed for 24 hours
However there is not a significant difference between the mean fuel required for a forzen roast and one that has thawed for 12 hours. Also there is not a significant difference in the mean fuel requiredf for a roas that has thawed for 12 hours or one that has thawed for 24.

13.2b battery life

if the battery is used at a temperature of 15 degrees, there is not a significant difference in the mean battery life for the three plate materials.  
if the battery is used at a temperature of 70 degrees, the mean battery life is significantly lowest for plate material A but, there is not a significant difference between plate material b and c
if the battery is used at a temperature of 125, there is not a significant difference in the mean battery life for the three plate materials. 

13.2c plant growth part 1

Independence: not matched pairs since the plants were randomly assigned to only one of the treatment combinations and there was random assignment

Constant variance: since BF p-value = 0.2440 > 0.1 the constant  variance condition is reasonable.

normality: The normal quantile plot of residuals is approximatley linear indicating the normality condition is plausible. 

13.2d plant growth part 2

test for equal means
h0: mean height is the same for all six combination of feeding frequency and variety of food
Ha: the mean height is different for at least two treatment combinations 

F: 10.4593 p-value: < 0.0001 

reject h0, there is enough evidence to conclude that the mean height is different for at least two combinations of feeding frequency and variety of food.

test for interaction

h0: feeding frequency and variety of food do not interact to affect the mean height
ha: feeding frequency and variety of food do interact to affect the mean height

F= 9.333 p-value= 0.0004

reject h0 there is enough evidence to conclude that the feeding frequency and variety of food do interact to affect the mean height.

13.2e plant growth part 3

compare the treatment combinations

the mean height is significantly lowest when using variety of food type c and 2 feedings

the remaining 5 treatment combinations do not differ significantly with respect to mean height

13.2e plant growth part 3

independence: not matched pairs; the cacti should have been randomly assigned to the 10 treatment combinations. 

constant variance: since BF p-value=0.3740 > 0.1 which indicates the constant variance condition is plausible 

normality: the normal quantile plot of residuals adequetly follows a linear pattern indicating the normality condition is plausible.

13.2g golden torch cacti part 2

test for equal means

h0: the mean weight gain of the cacti is the same for all 10 combinations of irrigation and polymers
ha: the mean weight gain of the cacti is different for at least 2 treatment combinations

f=12.4208 p-value: < 0.0001

reject H0 there is enough evidence to conclude that the mean weight gain of the cacti is different for at least 2 combinations of polymer and irrigation. 

test for interaction 

H0: polymer and irrigation do not interact to affect mean weight gain
ha: polymer and irrigation do interact to affect mean weight gain

f=0.3871 p-value: 0.8161

There is not enough evidence to conclude polymer and irrigation interact to affect mean weight gain of cacti

13.2h golden torch cacti part 3

analyze the main effects

polymer 
h0 the mean weight gain is the same whether there is a polymer used or not
ha the mean weight gain is different when a polymer is used vs when it is not used

f=1.8452 p-value= 0.1845

fail to reject h0 there is not enough evidence to conclude that the mean weight gain of the cacti is different whether the hydorphylic polymer is used or not

irrigation

h0 the mean weight gain is the same for all 5 irrigation regimes
ha the mean weight gain is different for at least two irrigation regimes

f= 27.0985 p-value= <0.0001

reject h0 there is enough evidence to conclude that the mean weight gain of the cacti is different for at least two irrigation regimes

The mean weight gain is significantly lowest when there is no irrigation. 
The xheavy irrigation resulted in a significantly higher mean weight gain than the medium and light irrigation. 
The heavy irrigation resulted in a significantly higher mean weight gain than light irrigation. 
There is not a significant difference in the mean weight gain of cacti for medium versus light irrigation. 











### gg-catalog


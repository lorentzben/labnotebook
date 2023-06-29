---
title: 'Module 5 Finish'
date: 2023-06-29T13:50:41Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat6315"
description: "Description for the page"
---

### Todos for Today

- STAT 6315
  - Review Exam 1 and markup my copy
  - lectures for homework 5
  - lectures for homework 6
  - lectures for homework 7
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Implications of the networks generated
  - How does KEGG work?
  - Show Aggrey the charts and ask him what he thinks
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
  - Some kind of machine learning classifier to determine major players in a phenotypic outcome.
  
### Stat 6315

#### Review Exam 1

Be more explicit with any information you provide and make sure that you are only providing what's needed. 

When checking assumptions use the hypothesis proportion and then state sampling distribution is approx normal.

#### Homework 5

I looked over the homework one more time and added some language about the sampling distribution being approximately normal. I think we are good to go.

#### Module 6

6.1a lying about age part 1

p != 0.5

independent
normal

What's the number of sucesses? .49 * 799 = 391.51 ~= 392/799

Hypotest for one proportion

p = 0.5956

It is plausable that p could be 0.5

b) 

could it be these other values?

There are other plausable values, can we find limits that we are 95% confident in within 2 standard deviations. 

distribution is centered at phat or p really, can phat line up with the limits? 


push distribution to right until phat is lined up then the center is the limit


6.1b lying about age pt 2

standard normal mean 0 stdev 1

.98 between -z* and z*, what are these values that capture 98% 

central probabilities put in how confident you want to be, then get the locations that 

sqrt(phat (1-phat)/n)

margin of error to lower limit phat margin of error to the upper limit

find 95% CI for phat of 0.49 

95% conf z*=1.96

SE = sqrt(phat*(1-phat)/n) 

margin of error 1.96*0.0177 = 0.0347 

0.49-0.0347= 0.4555 phat 0.49+0.0347= 0.5247 ] -> a range of plausable values for p

we can be 95% confident the proportion of all teens that have misrepresented their age online to gain access to websites and online services is between 0.4553 and 0.5247  

CI is sometimes more useful than hypothesis testing

6.1c aggressive driving pt1

indepencence: random sampling
normality: no n*p, use phat 990/1100 = 0.9 990, 110 since both values are at least 15 the sampling distribution of phat is approximately normal

97% = 2.1701

SE = sqrt((phat * 1-phat)/n) = 0.009045

ME = z* * SE = 2.1701 * 0.009 = 

0.9-0.0195 phat 0.9+0.0195

0.8805 0.9195

we can be 97% confidant the proportion of all drivers that would admit to aggresive driving during the previous 6 months is between these two values

JMP will of course do it for you too

6.1d aggressive driving pt 2

use JMP to determine width is n is larger but phat is the same. 

increase confidence increase width

increasing n narrows the width

large or small margin of error better? width = 2ME, small margin of error is better since you can better estimate p 

the best approach is to increse the sample size as possible, we do not want low confidence 90~95%

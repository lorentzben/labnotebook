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

the best approach is to increase the sample size as possible, we do not want low confidence 90~95%

6.2a NHANES height

phat +/- z* sqrt(phat *1-phat)/n

xbar +/- t* s/sqrt(n)

point estimate and standard error

assumptions:

- independent, randomly sampled or randomly assigned
- nearly normally distributed either population or the sample are normal otherwise n >= 30

random sample of 35, point estimate and get CI and intperate

xbar is a point estimate for mu, (35 out of the whole population)

a point estimate for mean height of all participants (mu) is xbar = 169.37

CI for mu 

make sure it is a t interval since we don't have the population stdev only the sample

(165.46 173.27) we can be 94% confident the mean height of all participants is between 164.46 and 173.27 cm

- Two types of estimation: point estimates like phat or xbar and there are interval estimates
- it is very unlikely the point estimate xbar will be equal to mu
- the point estimate does not account for:
  - the sampling variation of xbar (s/sqrt(n))
  - the sampling distribution of xbar (t*) (we're saying normally distributed)
interval is always better

- independence: the 35 observations were obtained by random sampling
- normality of xbar since n>=30 the sampling distribtion of xbar would be approximatly normal

6.2b parents

- mean>>> median, the distribution is probably skewed right

- the sample was obtained in such a way that it is considered representative of the population, therefore the sample and the population would have similar shapes, they are both skewed right. 

- The reason is since n>=30 (1086) the sampling distribution of xbar will be approximatly normal
 
 
s= 5.2 xbar 5.6 go back two standard deviations, negative hours of volunteering which does not make sense.

t*= 2.3298 

xbar +/- t* s/sqrt(n)

5.6 +/- 2.3298 5.2/(1086)

(5.23,5.97) We can be 98% confident, the mean time spent volunteering at their child's school for *all parents* falls between 5.23 and 5.97 hours *per month*.

6.2c understanding the level of confidence

!true there is not at 90% chance a given confidence interval contains mu

it is there or not, one interval out of many intervals 

- if we repeatedly obtained 90% confidence intervals from a population about 90% of the confidence intervals are expected to contain the true population mean (mu). 

6.2d additional questions

width = 2*ME

xbar +/- t*s/sqrt(n)

width = t* s/sqrt(n)

level of confidence increases width

increase sample side decrease width <- best option to narrow CI 

standard deviation increase width

sample mean does not affect width

given 18 observations, t* critical value is 1.637, what is the corresponding level of confidence?

0.8800 or 88% confidence

6.2e surgery wait times

A)

90% CI 1

98% CI 2 

B)

20.005-\frac{\left(2.01\right)}{2} = 19

19.710-\frac{\left(1.42\right)}{2} = 19

C) 

2*ME = 1.42 ME=0.71


6.2f point estimate versus interval estimate

unlikely that point estimate is equal to the paramter
- point estimate does not take into account the sampling distribution normality of the statistic 
point estimate does not account for the variability of the statistic s/sqrt(n) or sqrt(phat*1-phat)/n 

6.3a domestic cars part 1

n=40 
p =.60

- the variable is wheter or not a car in the athens area was manufactured in the US, it is categorical  

- the parameter of interest is p or the proportion  of all cars in the athens area that were manufactured in the united states

- n*phat = 40x.6 = 24
n*(1-phat)= 40x.4 = 16 
the sampling distribution *of phat* is approximately normally distributed because nxphat and nx(1-phat) are both greater than 15. Independence is also confirmed because a random select was used to collect phat

95% CI

.6 +/- 1.9600 * \sqrt{\frac{.6\times.4}{40}}

(0.4482,0.7518)
ME = 0.1518

6.3b domestic cars part 2

5 percentage points, margin of erro 0.05 

increase n smaller margin of error

me = z* sqrt(phat *1-phat)/n

0.05 = 1.96 \times \sqrt{\frac{0.6 \times 0.4}{n}}

at least 369 cars need to be sampled 

6.3c domestic cars part 3

phat = x/n number of sucesses over n 

need n to find phat and need phat to find n 

no pilot study?

phat*(1-phat) as large as possible, therefore the required sample size large and the sample size will fit the margin of error regarless of the actual sample proprtion

if I know phat use that

if I dont know phat use phat = 0.5, anywhere else will require a smaller sample size

n = (1.96/0.05)^2 \times 0.5(1-0.5) = 384.16 at least 385 cars need to be sampled

6.3c domestic cars part 3

A)
- the variable is whether or not health care professionals believe in astrology, it is categorical, they do or they do not.

B)

- 93% confident within 4% of the true proportion 
phat = 0.5 

me= 0.04

n = (1.8119/0.04)^2 \times 0.5x(1-0.5) = 512.9 or *at least* 513 health care professionals must be surveyed in order to be 93% confident the sample proportion is within 4% of the true proportion he got 514 cause of rounding

C)

phat = .35 93% confident within 4%

n = (1.8119/0.04)^2 \times 0.35x(1-0.35) = 466.7 or *at least* 467 health care professionals must be surveyed in order to be 93% confident the sample proportion is within 4% of the true proportion

6.3e textbook cost part 1

A)

The variable is the amount that a student spent on textbooks this semester, it is quantitative

B)

the parameter of interest is mu the average amount that all students spent on textbooks this semester, an estimate of the parameter of interest is xbar

a point estimate for mu is xbar

xbar = $284.92

C) 

it is plausable that the sampling distribution of xbar is normally distributed because the quantile plot follows an approximately linear pattern suggesting that the sample could have come from a normally distributed population

Shapiro-Wilk of 0.7757 we fail to reject H0 and do not have sufficient evidence to state that the sampling distribution of xbar is not normally distributed. 

D)

98% CI 

(209.541,360.292)

We can be 98% confident that the true mean cost of textbooks this semester for all students in the university is between \$209.54 and \$360.29


6.3f textbook cost part 2

E) 

NOT THIS 

t* = 2.7181
ME = 10


10 =  2.7181 96.06/sqrt(n)

at least 682 students need to be surveyed to be 98% confident the sample mean is within $10 of the mean cost for all students

n = ((z* \times s )/(ME))^2

n = ((2.326 \times 96.06)/10)^2 = 499.23 at least 500 students need to be sampled.

proportion has to be between 0 and 1, means do not have the same restriction

6.3g county land area

A)

The mean in much larger than the median, therefore the sampling distribution is skewed right

B)

xbar - 2s = -2068.9 but you cannot have a negative area in square miles, this disqualifies a normal distribution for the distribution of the sample is likely not normal

C)

Independence is met since they were randomly selected 

It is reasonable to use t confidence intervals because there are 50 samples which is greater than 30 so the sampling distribution of xbar is going to be approximately normally distributed

D)

xbar = 1132.80
s = 1600.85
CI = 94% 

(696.912,1568.69)

E)

CI 94%
ME = 250 
counties?
z* = 1.8808

n = ((1.8808 * 1600.85)/(250))^2 = 145.04 or at least 146 counties need to be sampled to be 94% confident of the average land area within 250 square miles of the true mean of all counties. 

Homework 6

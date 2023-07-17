---
title: 'Exam 3 Material'
date: 2023-07-17T12:39:47Z
draft: false
meta_img: "images/image.png"
tags:
  - "stat6315"
  - "microbiome-review"
description: "Description for the page"
---

### Todos for Today

- Make up TAP forms for Dr. Aggrey to sign
- Read papers about microbiome analysis
- STAT 6315
  - Watch all module 9 videos:
    - correlation and simple linear regression
    - simple linear regression
  - Submit homework #9 before 11:59 PM Eastern Time on July 19
  - Watch all module 10 videos:
    - multiple regression 
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

9.1a types of association, correlation coefficient

- Two Quantitative Variables -> make scatterplot to compare them 
Form, Linear, quadratic, exponentail
Direction, positiv negative, up down

Positive Association
no association

Correlation is a statistic that is used to quantify the variability and its linearity

r positive positive linear relationship
r negative negative linear relationship
Have to be careful with the correlation coeffecient, measures the strenght of the linear relationship

1. get to scatterplot first
2. then get correlation coeffecient

- may be a relationship just not linear

9.1b education and crime rate part 1

Explanitory Variable -> X
Response Variable -> Y

negative linear association

r will be negative because the scatterplot shows a negative association

no it is not a perfect relationship 

it is a weak negative linear relationship

9.1c education and crime rate part 2

Get equation

slope is equal to change in one unit

this is an average amount the crime rate will change

slope= change in y / change in x  

for every 1 percentage point increase in those with a high school diploma, crime rate is predicted to decrease by 170.58 on the average. 

9.1d Florida Election Recount

Palm Beach county

positive linear association

9.1e residuals

Sum of residuals is 0
Sum of the squared residuals is as small as possible. 

9.1f R-squared

reduction in variation measured by 

initial variation and P is the percentage of reduction

inital - P(inital) = r^2

17.12% of the variation of the response has been explained by fitting the model with percent with a HS diploma as the predictor variable 


Variation in y = model + not explained (error)

9.2a inference in regression, simulation

ybar = mean BMI

do the regression lines seem more different than the mean BMI

no the regression lines are somewhat flat and near the mean BMI

yes you will get similar results, no age is not useful, we could remove Age and still calculate the mean BMI (ybar)

Yes they are not flat like the mean BMI 

No we would not, based on the mean BMI we would predict ~30 but using regression we would predict 45 to 75, we would get different predicted BMI 

yes weight is very useful we should use weight instead of just using the  mean BMI

H0 slope is 0 
Ha slope is not 0

if you fail to reject you cant say that the slope is zero but you can say that the predictor varaible is not very useful

9.2b mechanics of hypothesis testing, checking conditions

yhat = b0 + b1 x

b0 and b1 are statistics

beta 0 and beta 1 are parameters

b1 is a point estimate of beta1 

b1 != beta 1

xbar is not mu

pop models

y = beta0 + beta1 x + error

Assumptions:
- distribution of error term at any x value has a mean value of 0
- the standard deviation of e is sigma which does not depend on x
- the dist of e at any x is normal
- random errors are independent

test stat t = b1-0/SE

find p-value using t-model n-2 degrees of freedom

conclude

y = beta0 + beta1 x + e

e = y-(beta 0 + beta1 x)

ehat = y - (b0 + b1x)

ehat = y - yhat = residuals

points are randomly dispersed (no pattern)
symetric around line y=0

vertical deviation is approx constant across range of x vals

---

the points are not randomly dispersed, there is a pattern
not symmetric about the zero line
The mean zero condition is not met

as x increases the vertical deviation of the residuals increases. 

the condition of dependence is not met

9.2d muscle mass part 1

negative linear association between these variables as age increases muscle mass tends to decrease

muscle mass hat = b0 - b1 * age

156.35 - 1.19 * age

conditions:

save residuals

- normal quantile plot of residuals does not have much curvature it has a fairly linear pattern indication the normality condition is plausable
  - cannot argue for large sample size here must use QQ plot
- Mean zero condition
  - there is not a pattern in the residual plot and it is symmetric across the zero line; these characteristics indicate the mean zero condition is met
- constant variance
  - the vertical deviation in the residuals does not depend on age; therefore the constant variance condition is plausible 
  - vertical deviation does not depend on x

9.2e muscle mass part 2

H0 beta1 = 0 
Ha beta1 != 0 

t = b1-o/SE

t= -1.19 - 0/0.09

use a t-distribution with DF = n-2 = 58 

find area in two tails, since !=

reject H0 there is enough evidence to conclude that age is a useful predictor of muscle mass

9.2f muscle mass part 3

b1 +/- t* SE

-1.19 +/- 2.663 (0.09) df=58 99% CI

for every one year increase in age we can be 99% confident muscle mass decreases anywhere from .95 to 1.43 on the average

since -2 is not in the 99% CI for beta1 there is enough evidence to conclude the change in muscle mass for every year decrease in age is not equal to 2

end of module 9










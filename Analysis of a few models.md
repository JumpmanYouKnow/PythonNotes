---
title: "Analysis of a few models"
date: 2019-05-06
---

---------------------
### 1.  OLS
Ordinary Least Squares, the most common estimation method for linear models,
It's good and simple, however, it has lots of assumptions.
1. the regression model is linear in coefficients and the error term
2. random sampling of observations
3. No multi-collinearity (each variable  is independent)
4. Error term is independent and identically distributed
5. all independent variables are uncorrelated with the error term

In brexit referendum data, there are 110 variables, there would be too much computation. and lots of variables are depend on each other, or have influence on others. so obviously the assumptions are not satisfied here. 

### 2. Decision Tree 
Decision tree is a model simple to implement and understand.
It can be easily optimized it using random forest.
It suits our data very well, it requires minimal data pre-processing and is able to handle many data types.
And it's efficiency regards computation.


### 3. GradientBoostingRegressor
It also a good model to use,  it is able to handle all kinds of data type flexibly.
It's a good replacement for OLS when amount of variables is large. 

### 4.  LASSO




> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYxMzM5NzM0NywtNDM1NTM3MTUxLDE4OT
c1OTQ2ODYsLTI5MTM0NjQzOCw4NDE5MzI3OTBdfQ==
-->
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

In brexit referendum data, there are 110 variables, and lots of them are depend on each other, or have influence on others. so obviously the assumptions are not satisfied here. 

### 2. Decision Tree 
Decision tree is a model simple to implement and understand.
You can also easily optimize it using random forest.
It suits our data very well, it requires minimal data pre-processing and is able to handle many data types.


### 3. GradientBoostingRegressor
### 4.  LASSO




> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzY1NjYwNTE4LDE4OTc1OTQ2ODYsLTI5MT
M0NjQzOCw4NDE5MzI3OTBdfQ==
-->
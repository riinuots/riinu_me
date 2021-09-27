---
title: Why does a linear model without an intercept (forced through the origin) have
  a higher R-squared value? [calculated by R]
author: Riinu Ots
date: '2014-08-06'
categories:
  - R
tags:
  - correlation
  - linear regression
slug: why-does-linear-model-without-an-intercept-forced-through-the-origin-have-a-higher-r-squared-value-calculated-by-r
---

_This is a short note based on [this](http://stats.stackexchange.com/questions/26176/removal-of-statistically-significant-intercept-term-boosts-r2-in-linear-model/26205#26205)._

Answer in short: Because different formulas are used to calculate the R-squared of a linear regression, depending on whether it has an intercept or not.

R2 for a linear model that has an intercept:

![CodeCogsEqn](https://riinudata.files.wordpress.com/2014/08/codecogseqn.png),

where _**y**_ is the variable that the linear model is trying to predict (the response variable), _y^_ is the predicted value and _y-_ is the mean value of the response variable.

And the R2 for a linear model that is forced through the origin:

![CodeCogsEqn (2)](https://riinudata.files.wordpress.com/2014/08/codecogseqn-2.png),

basically the mean value of the response variable is removed from the equation, making the denominator bigger (and the result of the division smaller). The reason why the  mean can not be used for this calculation is that it does not make sense any more - forcing the fit through zero kind of means adding an infinite number of (0,0) points into the dataset.

This means that the R-squared values of two different linear models (one with an intercept, one without) can not really be compared, because when the intercept is quite small compared to the residuals (basically the numerator) then the R2 "advantange" that the through-origin regression gets is relatively bigger than the decrease in residuals, when including the intercept.

---
title: Reordering factor levels in R and what could go wrong
author: Riinu Ots
date: '2015-06-11'
categories:
  - R
tags:
  - ggplot2
slug: reordering-factor-levels-in-r-and-what-could-go-wrong
---

I've recently started using [ggplot2](http://docs.ggplot2.org/current/) in addition to lattice (see [this post](https://riinudata.wordpress.com/2014/08/08/r-graphical-devices-plot-margins-and-legend-next-to-the-plot-not-on-it/) that I made a while ago, explaining how I got into using lattice in the first place). Hint: when using ggplot2, you'll need to use of the reshape2 package (also written by the amazing Hadley Wickham) to get your data into a form that ggplot2 works best with. Another thing that you'll want to think about when using ggplo2 is factor levels. This post will show how to (and also how not to) rearrange factor levels in R.

Let's create a quick barplot with strings as x labels.

```r
library(ggplot2)

#create dummy data
a = paste('my', 1:11)
b = 1:11
df = data.frame(a, b)
df
qplot(a, b, data=df, geom='bar', stat='identity') +
  theme(axis.text=element_text(size=16, angle=45))
```

![barplot1](https://riinudata.files.wordpress.com/2015/06/barplot1.png)

As df$a is an array of strings, R sets the factor levels alphabetically: my 1, my 10, my 11, my 2...which is not what we want, so let's rearrange factor levels:

```r
df$a = factor(df$a, levels = paste('my', 1:11))
df$a
qplot(a, b, data=df, geom='bar', stat='identity') +
  theme(axis.text=element_text(size=16, angle=45))
```

![barplot2](https://riinudata.files.wordpress.com/2015/06/barplot2.png)

And finally, the wrong way to rearrange factor levels would be by using the levels() function:

```r
df = data.frame(a, b)
levels(df$a) = paste('my', 1:11)
qplot(a, b, data=df, geom='bar', stat='identity') +
  theme(axis.text=element_text(size=16, angle=45))
```

![barplot3](https://riinudata.files.wordpress.com/2015/06/barplot3.png)

So be careful - if your data is not as obvious as this example and you are a bit new to factors and levels, you might end up plotting wrong results (like on the last example, "my 2" and "my 3" were plotted with the values 10 and 11).

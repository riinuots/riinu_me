---
title: 'R: Replacing NAs in all factors with ''Missing'''
author: Riinu Ots
date: '2017-07-19'
thumbnailImage: /img/thumbnails/forcats.png
categories:
  - R
tags:
 - factors
slug: r-replacing-nas-in-all-factors-with-missing
---

With a simple combination of `mutate_if` and `fct_explicit_na, `you can replace all NAs in all factors with "Missing":

{{< gist riinuots e517c36b1feb480df981721a00e0e24a >}} 


`dplyr` reference: <http://dplyr.tidyverse.org/reference>

`forcats` reference: <http://dplyr.tidyverse.org/reference>

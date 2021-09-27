---
title: How to "increase" array resolution in R (replicate each element both column-wise
  and row-wise)
author: Riinu Ots
date: '2015-09-12'
categories:
  - R
tags:
  - 3D
  - array
  - matrix
  - resolution
slug: how-to-increase-array-resolution-in-r-replicate-each-element-both-column-wise-and-row-wise
---

One picture says more than a thousand words. You have what is one the left, and you want what is on the right.

![resolution_cut](https://riinudata.files.wordpress.com/2015/09/resolution_cut.png)

```r
my_matrix = matrix(c(1, 2, 3, 4, 5, 6, 7, 8, 9), nrow=3)

#matrix is a 2D array, this next row creates a third dimension,
#duplicating the data
my_array = array(my_matrix, dim = c(3,3,2))
```

There are a few different ways to do this, but by far the cleanest and quickest way is to just select the rows and columns multiple times, by replicating row and column numbers (instead of actually replicating each element):

    #2D:
    increased_matrix = my_matrix[rep(1:nrow(my_matrix), each=3), rep(1:ncol(my_matrix, each=3)]

    #3D (same really, just one extra comma for the third dimension):
    increased_array = my_array[rep(1:nrow(my_array), each=3), rep(1:ncol(my_array, each=3), ]

Note that by default, in rep(something, n) the n is **times** so equivalent to rep(something, times=n), but in this case we need to use **each** instead of **times**.

 ---
title: Get data from ggplot()
author: Riinu Ots
date: '2016-12-06'
thumbnailImage: /img/thumbnails/ggplot2.png
categories:
  - R
tags:
 - plot
slug: get-data-from-ggplot
---

**ggplot** includes built in and seamless functionality that summarises your data before plotting it. As shown in the example below, `ggplot_build()` can be used to access the summarised dataset.

![summarised_barplot](https://riinudata.files.wordpress.com/2016/12/summarised_barplot.png)

{{< gist riinuots a6af08ac11f7b5ede69572a7559a704b >}}




    fill         y count prop x PANEL group    ...
    #D7301F 0.2147239    35    1 1     1     4 ...
    #FC8D59 0.6871166    77    1 1     1     3 ...
    #FDCC8A 0.9570552    44    1 1     1     2 ...
    #FEF0D9 1.0000000     7    1 1     1     1 ...
    #D7301F 0.1696429    38    1 2     1     8 ...
    #FC8D59 0.6116071    99    1 2     1     7 ...
    ...

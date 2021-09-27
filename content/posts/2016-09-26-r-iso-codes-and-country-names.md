---
title: 'R: ISO codes and country names'
author: Riinu Ots
date: '2016-09-26'
categories:
  - R
slug: r-iso-codes-and-country-names
---

install.packages(<span style="color:#0b6125;">'maps'</span>)

    iso = maps::iso3166

    > str(iso)
    'data.frame':   269 obs. of  5 variables:
     $ a2         : chr  "AW" ...
     $ a3         : chr  "ABW" ...
     $ ISOname    : chr  "Aruba" ..
     $ mapname    : chr  "Aruba" ...
     $ sovereignty: chr  "Netherlands" ...

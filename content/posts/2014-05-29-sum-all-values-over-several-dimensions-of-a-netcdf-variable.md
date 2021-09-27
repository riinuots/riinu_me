---
title: Sum all values over several dimensions of a netCDF variable
author: Riinu Ots
date: '2014-05-29'
categories:
  - netCDF
tags:
  - ncap2
  - NCO
  - netcdf
slug: sum-all-values-over-several-dimensions-of-a-netcdf-variable
---

[NCO:ncap2](http://nco.sourceforge.net/nco.html#ncap2-netCDF-Arithmetic-Processor) and .total

`ncap2 -s 'summed_variable=variable_to_sum.total($lat,$lon)' in.nc out.nc`

[Make sure to use single quotes.](http://sourceforge.net/p/nco/discussion/9830/thread/e15cbda8)

If your in.nc==out.cnc then adding -A will save you from having to specify "overwrite" ([see this](https://riinudata.wordpress.com/2014/05/29/nconcap2-and-append/)).

`ncap2 -A -s 'summed_variable=variable_to_sum.total($lat,$lon)' in.nc out.nc`

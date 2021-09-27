---
title: Converting R Markdown to Latex
author: Riinu Ots
date: '2015-06-24'
categories:
  - LaTex
  - R
tags:
  - pandoc
  - Rmarkdown
slug: converting-r-markdown-to-latex
---

Install Pandoc: <http://pandoc.org/>

```r
library(knitr)

knit('report.Rmd') #This creates 'report.md'
```

Open the Terminal, Command Prompt (search for cmd) or Windows Powershell, go to the folder and do:

`pandoc -s report.md -o report.tex`

And that's it!

(Read [this](http://proteo.me.uk/2013/06/generating-r-reports-with-vector-images-from-markdown-with-knitr/), if you want vector images.)

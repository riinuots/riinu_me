---
title: Adding space between rows in LaTex tables
author: Riinu Ots
date: '2016-04-11'
categories:
- LaTex
tags:
- latex
slug: adding-space-between-rows-in-latex-tables
---

By default, LaTex tables are very tight:

```
\usepackage{booktabs}

\begin{table}[]
\centering
\caption{My caption}
\label{my-label}
\begin{tabular}{@{}lll@{}}
\toprule
Rows  & Column 1 & Column 2 \\ \midrule
Row 1 & 1234     & 2345     \\
Row 2 & 3456     & 4567     \\
Row 3 & 5678     & 6789     \\
Row 4 & 7890     & 8901     \\
Row 5 & 9012     & 10000    \\ \bottomrule
\end{tabular}
\end{table}
```

![](https://riinudata.files.wordpress.com/2016/04/screen-shot-2016-04-11-at-11-28-54.png)

Adding this to the document preamble will add space between the rows:

```
\renewcommand{\arraystretch}{1.7}
```


![](https://riinudata.files.wordpress.com/2016/04/screen-shot-2016-04-11-at-11-24-26.png)

And this command can be used to add space between rows manually:

```
\vspace{1cm}
```

![](https://riinudata.files.wordpress.com/2016/04/screen-shot-2016-04-11-at-11-25-38.png)
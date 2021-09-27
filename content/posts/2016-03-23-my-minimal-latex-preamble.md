---
title: My minimal LaTex preamble
author: Riinu Ots
date: '2016-03-23'
categories:
- LaTex
tags:
- latex
slug: my-minimal-latex-preamble
---

My minimal example:

```
\documentclass[a4paper]{article}

%%% FIGURES AND TABLES %%%%
\usepackage{graphicx} %gives the \includegraphics[width=0.5\textwidth]{my_image}

%%% PAGE AND TEXT SET-UP %%%%
\usepackage{fullpage} %gets rids of the wide default borders
\renewcommand{\baselinestretch}{1.5} %space between lines

\begin{document}

Hello hello hello

\end{document}

And then one that is not so minimal, but still pretty basic and useful:

\documentclass[a4paper]{article}

%%% FIGURES AND TABLES %%%%
\usepackage{graphicx} %gives the \includegraphics[width=0.5\textwidth]{my_image}
\usepackage{booktabs} %for nicer tables
\usepackage{tabu} %advanced control over tables

\renewcommand{\thetable}{S\arabic{table}} %if this is supplement (this numbers figures as S1, S2...), comment out if main
\renewcommand{\thefigure}{S\arabic{figure}} %if this is supplement, replace S with A if Appendix

%%% SPECIAL CHARACTERS %%%%
\usepackage{amsmath} % amsmath provides extra maths symbols
\newcommand{\degree}{\ensuremath{^\circ}} %for some reason I can not find a degree symbol from other packages or the packages I do find it from clash with some others
\usepackage{times} %these packages will make texttildelow look normal
\usepackage{textcomp}

%%% REFERENCES $$$
\usepackage{natbib} %references as citet (textual) or citep (parenthetical)

%%% PAGE AND TEXT SET-UP %%%%
\usepackage{fullpage} %gets rids of the wide default borders
\usepackage{caption}
\captionsetup[table]{skip=10pt} %this adds space between the table caption and the table itself
\renewcommand{\baselinestretch}{1.5} %space between lines

\begin{document}

Hello hello hello

\bibliographystyle{apalike}
\bibliography{mybibfile.bib}

\end{document}
```

+++ 
date = 2020-11-20
title = "Archetype analysis"
description = "This is the first post of my personal website"
slug = "archetype-analysis"
authors = []
tags = ["archetypes"]
categories = []
externalLink = ""
series = ["Archetypal Analysis"]
+++

Archetypal anlalysis is a branch of statistics whose purpose is to search for extreme cases, called archetypes, in a data set.
Having these extreme patterns facilitates the interpretation of the results thanks to the principle of the opposites.


# Archetype Analysis (AA)

In archetype analysis, each archetype is defined as a convex combination of the observations.
At the same time, each observation is approximated by a convex combination of the archetypes.

## Method

Let $X$ be a $n \times m$ matrix with $n$ observations and $m$ variables.
The goal is to find a matrix $Z$ of $k$ $m$-dimensional archetypes.
For that, AA computes two matrices $\alpha$ and $\beta$ which minimize the residual squares sum

\begin{equation}
\begin{split}
    RSS = &\sum_{i=1}^n\sum_{j=1}^m \left\Arrowvert x_{ij} - \hat{x}_{ij} \right\Arrowvert^2 = \\
    =&\sum_{i=1}^n\sum_{j=1}^m \left\Arrowvert x_{ij} - \sum_{g=1}^k \alpha_{ig} z_{gj} \right\Arrowvert^2 = \\
    =& \sum_{i=1}^n\sum_{j=1}^m \left\Arrowvert x_{ij} - \sum_{g=1}^k \alpha_{ig} \left( \sum_{l=1}^n \beta_{gl} x_{lj}   \right) \right\Arrowvert^2
\end{split}
\end{equation}


under the constraints

1. $\sum_{j=1}^k \alpha_{ij} = 1$ with $\alpha_{ij} \geq 0$ for $i = 1, \ldots, n$.
2. $\sum_{l=1}^n \beta_{jl} = 1$ with $\beta_{jl} \geq 0$ for $j = 1, \ldots, k$.

---
title: "Archetypal Analysis in Python"
summary: "A quick introduction to Archetypal Analysis in Python."
tags: []
---

In progress...

## Archetype Analysis (AA)

Let $X$ be a $n \times m$ matrix with $n$ observations and 
$m$ variables.
The goal is to find a matrix $Z$ of $k$ $m$-dimensional archetypes.
For that, AA computes two matrices $\alpha$ and $\beta$ which minimize the 
residual squares sum

<div>
\begin{aligned}
    RSS = &\sum_{i=1}^n\sum_{j=1}^m \left\lVert x_{ij} - \hat{x}_{ij} \right\rVert^2 \cr
        = &\sum_{i=1}^n\sum_{j=1}^m \left\lVert x_{ij} - \sum_{g=1}^k \alpha_{ig} z_{gj} \right\rVert^2 \cr
        = &\sum_{i=1}^n\sum_{j=1}^m \left\lVert x_{ij} - \sum_{g=1}^k \alpha_{ig} \left( \sum_{l=1}^n \beta_{gl} x_{lj}   \right) \right\rVert^2
\end{aligned}
</div>

under the constraints

1. $\sum_{j=1}^k \alpha_{ij} = 1$ with $\alpha_{ij} \geq 0$
for $i = 1, \ldots, n $.
2. $\sum_{l=1}^n \beta_{jl} = 1$ with $\beta_{jl} \geq 0$
for $j = 1, \ldots, k $.


```Python
import archetypes as arch


aa = arch.AA(n_archetypes=5)
aa.fit(X)

```

## Bi-Archetype Analysis (BiAA)

Let $X$ be a $n \times m$ matrix with $n$ observations and 
$m$ variables.
The goal is to find a matrix $Z$ of $k$ $c$-dimensional archetypes.
For that, BiAA computes four matrices $\alpha$, $\gamma$, $\beta$
and $\theta$ which minimize the 
residual squares sum


<div>
\begin{aligned}
    RSS = &\sum_{i=1}^n\sum_{j=1}^m \left\lVert x_{ij} - \hat{x}_{ij} \right\rVert^2 \cr
        = &\sum_{i=1}^n\sum_{j=1}^m \left\lVert x_{ij} - \sum_{g=1}^k
        \sum_{h=1}^c \alpha_{ig} z_{gh} \gamma_{hj} \right\rVert^2 \cr
        = &\sum_{i=1}^n\sum_{j=1}^m \left\lVert x_{ij} - \sum_{g=1}^k 
        \sum_{h=1}^c \alpha_{ig} \left( \sum_{l=1}^n \sum_{r=1}^m 
        \beta_{gl} x_{lr} \theta_{rh} \right) \gamma_{hj} \right\rVert^2
\end{aligned}
</div>

under the constraints

1. $\sum_{g=1}^k \alpha_{ig} = 1$ with $\alpha_{ig} \geq 0$
for $i = 1, \ldots, n $.
2. $\sum_{h=1}^c \gamma_{hj} = 1$ with $\gamma_{hj} \geq 0$
for $j = 1, \ldots, m $.
3. $\sum_{l=1}^n \beta_{gl} = 1$ with $\beta_{gl} \geq 0$
for $g = 1, \ldots, k $.
4. $\sum_{r=1}^m \theta_{rh} = 1$ with $\theta_{rh} \geq 0$
for $h = 1, \ldots, c $.


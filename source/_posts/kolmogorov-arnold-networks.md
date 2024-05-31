---
title: Discussion of "KAN kolmogorov-arnold-networks"
date: 2024-05-21 19:00:00
tags:
---

This is a discussion of the paper "KAN: kolmogorov-arnold-networks".
<!--more-->

## Preliminaries

### B-splines

#### Definition

Suppose we have $m$ $(m \geqslant 0)$ distinct internal knots, $\xi_1, \ldots, \xi_m$, placed within the boundary knots $a$ and $b$, satisfying $a<\xi_1<\cdots<\xi_m<b$. We can define $t_1=\cdots=t_d=a$, $t_{d+j}=\xi_j$ for $j \in\{1, \ldots, m\}$, and $b=t_{d+m+1}=\cdots=t_{d+p}$, where $k$ and $d=k+1$ represent the polynomial degree and the order of a basis function, respectively, and $p=d+m$ represents the degrees of freedom of a basis function. Given internal knots, $\xi_1, \ldots, \xi_m$, and boundary knots, $L$ and $U$, we denote the simple knot sequence intended for splines of degree $k$ by $\mathbf{T}_k$. Splines of degree $k \in\{1,2, \ldots\}$

For a given $k \in$ $\{1,2, \ldots\}$, the $i$ th B-spline basis of degree $k$ (or order $d=k+1$ ) denoted by $B_{i,k}(x)$ based on the simple knot sequence $\mathbf{T}_k$ can be defined by the following Cox-de Boor recursive formula:
$$
B_{i,k}\left(x \mid \mathbf{T}_k\right)=\left(\frac{x-t_i}{t_{i+k}-t_i}\right) B_{i, k-1}\left(x \mid \mathbf{T}_k\right)+\left(\frac{t_{i+k+1}-x}{t_{i+k+1}-t_{i+1}}\right) B_{i+1, k-1}\left(x \mid \mathbf{T}_k\right),
$$
with
$$
B_{l, 0}\left(x \mid \mathbf{T}_k\right)=\left\{\begin{array}{ll}
1, & t_l \leq x<t_{l+1} \\
0, & \text { otherwise }
\end{array}, l \in\{1, \ldots, d+p-1\}\right.,
$$
where $L \leq x<U, p=m+d$ represents the degrees of freedom, and $i \in\{1, \ldots, p\}$.

![Cubic B-splines Basis with internal knots $(0.3,0.5,0.6)$](/images/kolmogorov-arnold-networks/b-splines.png)

#### Properties

Beginning with a partition of $[a,b]$, let $a=t_0$, where $K_n$ is $O\left(n^\nu\right)$, and $\max _{1 \leq j \leq K_n+1}\left|t_j-t_{j-1}\right|=O\left(n^{-\nu}\right)$ to ensure convergence. Then define $\mathbf{T}_{K_n}$ as the set of partition points, and $S_n^p([a, b])=S_n\left(\mathbf{T}_{K_n}, K_n, p\right)$ as the space of polynomial spline basis of order $p$ as defined in Schumaker (2007). There exist B-spline basis functions $\left\{B_j, 1 \leq j \leq q_n\right\}$, where $q_n=K_n+p$, such that for any $f_{0n} \in S_n^p([a, b])$, it can be expressed as $f_{0n}(t)=\sum_{j=1}^{q_n} \alpha_j B_j(t)$, where $\boldsymbol{\alpha}=\left(\alpha_1, \ldots, \alpha_{q_n}\right)^{\top}$ represents the corresponding coefficients of the spline.

Let $S^p([a, b])$ be the collection of bounded functions $f$ on $[a, b]$ with bounded derivatives $f^{(j)}, j=1, \ldots, k$, where the $k$-th derivative $f^{(k)}$ satisfies the $m$-Hölder continuity condition:
$$
\left|f^{(k)}(s)-f^{(k)}(t)\right| \leq L|s-t|^m \quad \forall s, t \in[a, b],
$$
where $k$ is a positive integer and $m \in(0,1]$ with $p=m+k$, and $L<\infty$ is a constant.

For $f_0 \in S^p([a, b])$, their exists a function $f_{0n} \in S_n^p([a, b])$ such that
$$
\left\|f_0-f_{0 n}\right\|_{\infty}=O\left(n^{-p \nu}\right).
$$

## Understanding

### Expanding the input dimension

### Activate multiple times

### Activate then Multiply

## Future Work

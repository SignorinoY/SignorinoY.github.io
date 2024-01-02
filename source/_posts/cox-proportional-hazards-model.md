---
title: Cox Proportional Hazards Model
date: 2024-01-02 21:34:32
tags: [Survival Analysis]
---

The Cox proportional hazards model is a semi-parametric model commonly used in survival analysis. It is a regression model that aims to model the hazard function of survival time $T$, which represents the probability of an event occurring at time $t$ given that the event has not occurred before time $t$, that is,
$$
\lambda(t)=\lim_{\Delta t\rightarrow 0}\frac{P(t\leq T<t+\Delta t|T\geq t)}{\Delta t}.
$$

<!-- more -->

## Assumptions

The Cox proportional hazards model assumes that the hazard function follows the form:
$$
\lambda(t|X) = \lambda_0(t) \exp(X^T\beta),
$$
where, $\lambda_0(t)$ represents the baseline hazard function, and $\beta$ is the vector of regression coefficients.

## Estimation

The estimation of the Cox proportional hazards model is based on the partial likelihood function. The partial likelihood function is defined as:
$$
L(\beta) = \prod_{i=1}^{n}\left[\frac{\exp(X_i^T\beta)}{\sum_{j\in R(t_i)} \exp(X_j^T\beta)}\right]^{\delta_i},
$$
where, $R(t_i)$ represents the set of individuals at risk at time $t_i$, and $\delta_i$ is an indicator variable that takes the value 1 if the event occurs for individual $i$ and 0 otherwise.

The corresponding log partial likelihood function of $\beta$ is given by:
$$
\ell(\beta)=\sum_{i=1}^{n}\delta_i\left[X_i^T\beta-\log\left(\sum_{j\in R(t_i)}\exp(X_j^T\beta)\right)\right]
$$
and the cumulative baseline hazard function $\Lambda_0(t)$ is given by:
$$
\Lambda_0(t)=\frac{\sum_{i=1}^{n}\exp(X_i^T\beta)I(t_i\leq t)}{\sum_{i=1}^{n} I(t_i\leq t)},
$$
where, $I(t_i\leq t)$ is an indicator variable that takes the value 1 if $t_i\leq t$ and 0 otherwise.

{% note default no-icon Proof %}
The likelihood function is defined as:
$$
L(\beta)=\prod_{i=1}^{n}\lambda(t_i|X_i)^{\delta_i}S(t_i|X_i),
$$
where $S(t_i|X_i)$ represents the survival function.

Assuming the baseline hazard function is a piecewise constant function, i.e., $\lambda_0(t)=\lambda_k$ for $t\in[t_k,t_{k+1})$, the likelihood function can be written as:
$$
L(\beta)=\prod_{i=1}^{n}\lambda_0(t_i)\exp(X_i^T\beta)^{\delta_i}\exp\left(-\int_0^{t_i}\lambda_0(u)\exp(X_i^T\beta)\,\mathrm{d}u\right)
$$
{% endnote %}

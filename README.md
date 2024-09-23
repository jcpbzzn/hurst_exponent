# Hurst Exponent

## Introduction

### Definition

The Hurst-Exponent is a measure of the long-term memory of time series.

It was originally developed in hydrologyst Harold Edwin Hurst to model volatile rain and drought conditions observed over a long horizon, in order to determine optimal dam sizes for the Nile River.

The Hurst exponent measures the relative tendency of a series to regress around its mean or to cluster in a direction. Specifically, it is a single scalar value that indicates if a time series is purely random, trending, or rather mean reverting. 
Thus, it can validate either momentum or mean-reverting strategies. The Hurst exponent uses the variance of a log price series to assess the rate of diffusive behavior.

If a time series follows a random walk, its variance simply increases linearly with time elapsed. If instead variance increases with time to the power of an exponent, then a low (Hurst) exponent would indicate mean reversion and a high exponent trending behavior. 
The Hurst exponent depends on the period used for return calculation.

The Hurst Exponent H is defined in terms of asymptotic behavior of the rescaled range as a function of the time span of the time series:

$$
E\left[\frac{R(n)}{S(n)}\right]=Cn^{H} \text{ as } n \to \infty
$$

Where:
- $\text{R(n)}$  is the range of the first 𝑛 cumulative deviations from the mean
- $\text{S(n)}$ is the series (sum) of the first 𝑛 standard deviations
- $\text{E[x]}$ is the expected value
- $\text{n}$ is the timespan of the observation
- $\text{c}$ is a constant

### Interpretation

The Hurst exponent ranges from 0 to 1:
- Long-term switching between high and low values in adjacent pairs (Mean Reversion)
  - $0 \leq H_q < 0.5$
- Short term memory (White Noise)
  - $H_q = 0.5
- Long-term positive autocorrelation (Trend)
  - $0.5 < H_q \leq 1$

### Estimation

For each time series of length $\text{n}$, $X=X_1, X_2, ..., X_n$ the rescaled range is calculated as follows:

Calculate the mean:

$$
m = \frac{1}{n} \sum_{i=1}^{n} X_i
$$

Center the series by subtracting the mean from each observation:

$$
Y_t = X_t-m \text{ for } t=1,2,...,n
$$

Calculate the cumulative deviate series:

$$
Z_t = \sum_{i=1}^{n} Y_i \text{ for } i=1,2,...,n
$$

Compute the Range $R(n)$:

$$
R(n) = \max{(Z_1,Z_2,...,Z_n)} - \min{(Z_1,Z_2,...,Z_n)}
$$

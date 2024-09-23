# Hurst Exponent

## Introduction

The Hurst-Exponent is a measure of the long-term memory of time series.

It was originally developed in Hydrologyst ___ to model volatile rain and drought conditions observed over a long horizon, in order to determine optimal dam sizes for the Nile River.

The Hurst exponent measures the relative tendency of a series to regress around its mean or to cluster in a direction. Specifically, it is a single scalar value that indicates if a time series is purely random, trending, or rather mean reverting. 
Thus, it can validate either momentum or mean-reverting strategies. The Hurst exponent uses the variance of a log price series to assess the rate of diffusive behavior.

If a time series follows a random walk, its variance simply increases linearly with time elapsed. If instead variance increases with time to the power of an exponent, then a low (Hurst) exponent would indicate mean reversion and a high exponent trending behavior. 
The Hurst exponent depends on the period used for return calculation.

The Hurst Exponent H is defined in terms of asymptotic behavior of the rescaled range as a function of the time span of the time series:

$$
E\left[\frac{R(n)}{S(n)}\right]=Cn^{H} \text{ as } n \to \infty
$$



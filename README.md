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

Compute the Range $R$:

$$
R(n) = \max{(Z_1,Z_2,...,Z_n)} - \min{(Z_1,Z_2,...,Z_n)}
$$

Compute the Standard Deviation $S$:

$$
S(n) = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(x_i-m)^{2}}
$$

Calculate the rescaled range 

$$
\frac{R(n)}{S(n)}
$$

The Hurst exponent is estiated by fitting the power law $E\left[\frac{R(n)}{S(n)}\right]=Cn^{H}$ to the data. To do so, we can plot $\log{\frac{R(n)}{S(n)}}$ as a function of $\log{n}$.
The regression coefficient is our estimate of $H_q$.

## Simulating Time Series

### Mean Reversion

To simulate a mean reverting process we can use the Ornstein-Uhlenbeck process. The model is specified by the following SDE:

$$
dX_t = \theta(\mu - X_t)dt + \sigma dW_t
$$

Where:
- $X_t$ is the process value at time $t$;
- $\theta > 0$ is the rate of mean reversion
- $\mu \in R$ is the long-term mean the process reverts to
- $\sigma > 0$ is the volatility
- $dW_t$ is the increment of a Wiener process

This process is _Gaussian_, _Markovian_ and _Unconditionallly Stationary_.
- _Gaussian_ --> Completely specified by its mean function and covariance function;
- _Markovian_ --> Transitions between discrete states occur with fixed probabilities, and the transition probabilities depend only on the previous state, making it memoryless;
- _Unconditionally Stationary_ --> Unconditional distribution (all moments) is invariant in time.

We can use the Euler-Maruyama method to derive the approximate numerical solution to the above SDE
The above SDE can be approximated using a numerical solution.

Given the following stochastic differential equation:

$$
dX_t = a(X_t,t)dt + b(X_t,t)dW_t
$$

Suppose the initial condition is $X_0 = x_0$, $W_t$ is a Wiener process, and we want to solve over a time interval $\left[0,T\right]$. 
The Euler-Maruyama aproximation to the solution $X$ is the Markov chain $Y$ defined as follows:




## References

- [Ornstein-Uhlembeck Process](https://uregina.ca/~kozdron/Teaching/Regina/441Fall14/Notes/L31-32-Nov19.pdf)
- [Gaussian Process](http://www0.cs.ucl.ac.uk/staff/j.shawe-taylor/courses/ATML-1.pdf)
- [Markovian Process](https://www.sciencedirect.com/topics/chemistry/markovian-process#:~:text=A%20Markovian%20process%20is%20defined,Dynamics%20of%20Single%20Molecules%2C%202019)
- [Euler-Maruyama](https://www.sfu.ca/~pft3/days/m3.pdf)
- [Euler-Maruyama](https://www.youtube.com/watch?v=ePDInJYg714&t=1s)
  

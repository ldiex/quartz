# Poisson Distribution
*Poisson distribution* expresses the probability of a given number of events occurring in a fixed interval of time if these events occur with a known constant mean rate and [[Conditional Probability#Independence of events|independently]] of the time since the last event. The notation is $\mathrm{Pois}(\lambda)$

Under a Poisson distribution with the expectation of $\lambda$ events in a given interval, the probability of $k$ events in the same interval (the [[Random Variables#Probability Mass Function|PMF]]) is
$$
P(X = k) = \dfrac{\lambda^k e^{-\lambda}}{k!}
$$
where the positive real number $\lambda$ is equal to the expected value of $X$ and also to its variance:
$$
\lambda = \mathrm{E}(X) = \mathrm{Var}(X)
$$

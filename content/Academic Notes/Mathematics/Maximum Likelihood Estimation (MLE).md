If we model a set of observations as a random sample from an unknown [[Joint Distributions|joint probability distribution]] which is express in terms of s set of parameters. The goal of *maximum likelihood estimation* is **to determine the parameters for which the observed data have the highest joint probability**.

We write the parameters governing the joint distribution as a vector $\theta = [\theta_1,\theta_2, \ldots ,\theta_k]^T$ so that this distribution falls within a parametric family $\left\{ f(\cdot ; \theta)|\theta\in \Theta \right\}$, where $\Theta$ is called the *parameter space*, a finite-dimensional subset of [[Euclidean Space|Euclidean space]]. Evaluating the joint density at the observed data sample $\boldsymbol y = (y_1,y_2, \ldots ,y_n)$ gives a real-valued function
$$
\mathcal{L}_n(\theta) = \mathcal{L}_n(\theta;\boldsymbol y) = f_n(\boldsymbol y; \theta)
$$
which is called the [[Likelihood Function|likelihood function]]. For [[Random Variables#Independent and Identically Distributed (i.i.d.)|i.i.d.]] random variables, $f_n(\boldsymbol y;\theta)$ will be the product of univariate (that is, only one variable) [[Continuous Random Variables#Probability Density Function|PDF]]:
$$
f_n(\boldsymbol y; \theta) = \prod_{k = 1}^n f_k(y_k;\theta)
$$
The goal of maximum likelihood estimation is to find the values of the model parameters that **maximize the likelihood function over the parameter space**, that is
$$
\hat{\theta} = \underset{\theta\in \Theta}{\arg \max} \ \mathcal{L}_n (\theta; \boldsymbol y)
$$



# Discrete Case
## Joint CDF
The *joint [[Random Variables#Cumulative Distribution Function|CDF]]* of r.v.s $X$ and $Y$ is the function $F_{X,Y}$ given by
$$
F_{X,Y}(x,y) = P(X \leq x, Y \leq y)
$$
The joint CDF of $n$ r.v.s. is defined analogously.

## Joint PMF
The *joint [[Random Variables#Probability Mass Function|PMF]]* of discrete r.v.s $X$ and $Y$ is the function $p_{X,Y}$ given by
$$
p_{X,Y}(x,y) = P(X = x, Y = y)
$$
The joint PMF of $n$ discrete r.v.s is defined analogously.

We require valid joint PMFs to be nonnegative and sum to $1$, where the sum is
$$
\sum_x \sum_y P(X = x, Y = y) = 1
$$
## Marginal PMF
From the joint distribution of $X$ and $Y$, we can get the distribution of $X$ alone by summing over the possible values of $Y$. In the context of joint distributions, we call this the *marginal* or *unconditional* distribution of $X$

For discrete r.v.s $X$ and $Y$, the *marginal PMF* of $X$ is
$$
P(X = x) = \sum_y P(X = x,Y = y)
$$
The marginal PMF of $X$ **is** the PMF of $X$, viewing $X$ individually rather than jointly with $Y$. This operation is known as *marginalizing out* $Y$

## Conditional PMF
For discrete r.v.s. $X$ and $Y$, the *conditional PMF* of $Y$ given $X = x$ is
$$
P(Y = y | X = x) = \dfrac{P(X=x,Y=y)}{P(X = x)}
$$
This is viewed as a function of $y$ for fixed $x$

Using [[Conditional Probability#Law of total probability|LOTP]], we have another way of the marginal PMF
$$
P(X = x) = \sum_y P(X = x | Y = y)P(Y = y)
$$
# Continuous Case
## Joint PDF
If $X$ and $Y$ are continuous with joint CDF $F_{X,Y}$, their *joint PDF* is the [[Differential of Multivariable Functions|derivative]] of the joint CDF with respect to $x$ and $y$
$$
f_{X,Y} = \frac{ \partial^{2} }{ \partial x \partial y}  F_{X,Y}(x,y)
$$
We require valid joint PDFs to be nonnegative and integrate to $1$
$$
\int_{-\infty}^\infty \int_{-\infty}^\infty f_{X,Y}(x,y) \mathrm{d}x \mathrm{d}y = 1
$$
## Marginal PDF
For continuous r.v.s $X$ and $Y$ with joint PDF $f_{X,Y}$, the *marginal PDF* of $X$ is
$$
f_X(x) = \int_{-\infty}^{\infty} f_{X,Y}(x,y)\mathrm{d}y
$$
## Conditional PDF
For continuous r.v.s $X$ and $Y$ with joint PDF $f_{X,Y}$, the *conditional PDF* of $Y$ given $X = x$ is
$$
f_{Y|X} (y | x) = \dfrac{f_{X,Y}(x,y)}{f_X(x)}
$$
for all $x$ with $f_X(x) > 0$.
## Continuous form of Bayes' rule
For continuous r.v.s $X$ and $Y$, we have the following continuous form of [[Bayes' Theorem|Bayes' rule]]:
$$
f_{Y | X}(y | x) = \dfrac{f_{X | Y}(x |y)f_Y(y)}{f_X(x)}
$$

## Independence of continuous r.v.s
Random variables $X$ and $Y$ are independent if for all $x$ and $y$,
$$
F_{X,Y}(x,y) = F_X(x)F_Y(y)
$$
If $X$ and $Y$ are continuous with joint $f_{X,Y}$, this is equivalent to the condition
$$
f_{X,Y}(x,y) = f_X(x)f_Y(y)
$$
for all $x,y$, and it is also equivalent to the condition
$$
f_{Y|X}(y|x) = f_Y(y)
$$
for all $x,y$ such that $f_X(x)>0$
> [!Tip] 
> The marginal PDF of $Y$, $f_Y(y)$, is a function of $y$ only; it cannot depend on $x$ in any way. The conditional PDF $f_{Y|X}(y|x)$ can depend on $x$ in general. Only in the special case of independence is $f_{Y|X}(y|x)$ free of $x$

Suppose that joint PDF $f_{X,Y}$ of $X$ and $Y$ as 
$$
f_{X,Y}(x,y) = g(x)h(y)
$$
for all $x$ and $y$, where $g$ and $h$ are nonnegative functions. Then $X$ and $Y$ are independent. Also, is either $g$ or $h$ is a valid PDF, then the other one is a valid PDF too and $g$ and $h$ are the marginal PDFs $X$ and $Y$, respectively.




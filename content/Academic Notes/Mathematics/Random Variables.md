# Random Variable
Given an experiment with sample space $S$, a *random variable* (r.v.) is function from the sample space $S$ to the real numbers $\mathbb{R}$. It is common, but not required, to denote random variables by capital letters.

Thus, a random variable $X$ assigns a number value $X(s)$ to each possible outcome $s$ of the experiment. **The mapping itself is deterministic**.

For example, consider an experiment where we toss a fair coin twice. The sample space consists of four possible outcomes $S = \left\{ H H, HT, TH, TT \right\}$. Then we can define $X$ be the number of Heads:
$$
X(HH) = 2, X(HT) = X(TH) = 1, X(TT) = 0
$$
## Discrete Random Variable
A random variable $X$ is said to be *discrete* if there is a finite list of values $a_1, \ldots ,a_n$ or an infinite list of values $a_1,a_2, \ldots$ such that $P(X = a_j \text{ for some } j) > 0$. If $X$ is a discrete r.v., then the finite or countable infinite set of values $x$ such that $P(X = x)>0$ is called the *support* of $X$

In contrast, a *continuous* r.v. can take on any real value in an interval (possibly even the entire real line)

> [!Info]
> It is also possible to have an r.v. that is **a hybrid of discrete and continuous**, such as by flipping a coin and then generating a discrete r.v. if the coin lands Heads and generating a continuous r.v. if the coin lands on Tails.

## Indicator Random Variable
The *indicator random variable* of an event $A$ is the r.v. which equals $1$ if $A$ occurs and $0$ otherwise. We will denote the indicator r.v. of $A$ by $I_A$ or $I(A)$
# Probability Mass Function
The *Probability Mass Function* (PMF) of a **discrete** r.v. $X$ is the function $p_X$ given by $p_X(x) = P(X = x)$. Note that this is positive if $x$ is in the support of $X$, and $0$ otherwise

> [!Tip]
> In writing $P(X = x)$, we are using $X = x$ to denote an event, consisting of all outcomes $s$ to which $X$ assigns to the number $x$

Let $X$ be a discrete r.v. with support $x_1,x_2, \ldots$, the PMF $p_X$ of $X$ must satisfy the following two criteria:
- Nonnegative: $p_X(x) > 0$ if $x = x_j$ for some $j$, and $p_X(x) = 0$ otherwise;
- Sums to $1$: $\sum_{j = 1}^{\infty} p_X(x_j) = 1$

# Cumulative Distribution Function
The *cumulative distribution function* (CDF) of an r.v. $X$ is the function $F_X$ given by $F_X(x) = P(X \leq x)$. When there is no risk of ambiguity, we sometimes drop the subscript and just write $F$ for a CDF.

Any CDF $F$ has the following properties:
1. Increasing: $F(x_1) \leq F(x_2) \iff x_1 \leq x_2$
2. Right-continuous: wherever there is a jump, the CDF is continuous from the right. That is, for any $a$, we have
$$
F(a) = \lim_{ x \to a^+ } F(x)
$$
3. Convergence to $0$ and $1$ in the limits:
$$
\lim_{ x \to -\infty } F(x) = 0 \text{ and } \lim_{ x \to \infty } F(x) = 1
$$
> [!Tip]
> We often say the **distribution function of a discrete r.v.** is its PMF, and **the distribution function of a continuous r.v.** is its CDF
# Functions of Random Variables
For an experiment with sample space $S$, an r.v. $X$, and a function $g:\mathbb{R} \to \mathbb{R}$. $g(X)$ is the r.v. that maps $s$ to $g(X(s))$ for all $s\in S$

Let $X$ be a discrete r.v. and $g:\mathbb{R} \to \mathbb{R}$. Then the PMF of $g(X)$ is
$$
P(g(X)=y) = \sum_{x:g(x)=y}P(X=x)
$$
as for the continuous case:
$$
P(g(X)=y) = \int_{\left\{ x:g(x)=y \right\} }P(X=x) \mathrm{d}x
$$

> [!Example]
> For a [[Continuous Random Variables|continuous r.v.]] $X \sim F(x)$ where $F(x)$ is some CDF, then $F(X) \sim U(0,1)$, and $U(\cdot,\cdot)$ represents the [[Uniform Distributions|uniform distribution]]
> We can prove this by converting the CDF of $F(X)$ to the CDF of $X$, that is, $P(F(X) \leq y) = P(X \leq F^{-1}(y)) = F(F^{-1}(y))=y$
> Here $F^{-1}(y)$ exists since $F(x)$ is continuous and strictly increasing (the property of CDF)
> See [[Uniform Distributions#Universality of the Uniform|the universality of the uniform]]
## Formula of transform for monotone functions
Let $X$ be a continuous r.v. with PDF $f_X(X)$. Consider a monotonic function $y=g(x)$ defined on the support of $X$, for which the derivative of $g^{-1}(y)$ exists and is continuous. Then $Y = g(X)$ is a continuous r.v. with PDF given by
$$
f_Y(y) = f_X(g^{-1}(y))\left|\left( g^{-1} \right)'(y) \right|
$$
# Independence of Random Variables
Random variables $X$ and $Y$ are said to be *independent* if 
$$
P(X \leq x,Y\leq y) = P(X \leq x)P(y \leq Y)
$$
for all $x,y\in \mathbb{R}$
In the discrete cases, this is equivalent to the condition
$$
P(X = x, y = y) = P(X = x)P(Y = y)
$$
for all $x, y$ with $x$ in the support of $X$ and $y$ in the support of $Y$

Random variables $X_1, \ldots ,X_n$ are *independent* if
$$
P(X_1\leq x_1, \ldots ,X_n \leq x_n) = P(X \leq x_1) \cdots P(X_n \leq x_n)
$$
for all $x_1, \ldots ,x_n\in \mathbb{R}$. For infinitely many r.v.s, we say that they are independent if every finite subset of the r.b.s is independent.

> [!Tip]
> Note that this criteria is different from that for [[Conditional Probability#Independence of $n$ events|independence]] of $n$ events. But in fact, if $X_1, \ldots ,X_n$ are independent, then they are also pairwise independent, i.e., $X_i$ is independent of $X_j$ for $i \neq j$. The idea behind proving that $X_i$ and $X_j$ are independent is to let all the $x_k$ other than $x_i,x_j$ go to $\infty$ in the definition of independence, since we already know $X_k < \infty$ is true. But pairwise independence does **not** imply independence in general.

If $X$ and $Y$ are independent r.v.s, then any function of $X$ is independent of any function of $Y$

# Independent and Identically Distributed (i.i.d.)
We often work with random variables that are independent and have the same distribution. We call such r.v. *independent and identically distributed*, or *i.i.d.* for short.

If some r.v.s. are i.i.d., they provide no information about each other and have the same [[Random Variables#Probability Mass Function|PMF]] and [[Random Variables#Cumulative Distribution Function|CDF]]





# Definition
Suppose $T \in \mathcal{L}(V)$ has an [[Eigenvectors and Characteristic Polynomial#特征值|eigenvalue]] $\lambda$. Its *generalized eigenspace* is
$$
K_\lambda \coloneqq \left\{ \boldsymbol x \in V:(T-\lambda E)^k(\boldsymbol x) = 0 \text{ for some } k \in \mathbb{N}\right\} 
$$
and a *generalized eigenvector* is any non-zero $\boldsymbol v \in K_\lambda$

# Relation with characteristic polynomial
Suppose that the [[Characteristic Polynomial|characteristic polynomial]] of $T\in \mathcal{L}(V)$  splits over $F$:
$$
\chi(t) = (\lambda_1-t)^{m_1}\cdots(\lambda _k - t)^{m_k}
$$
where the $\lambda_j$ are the distinct eigenvalues of $T$ with [[Eigenvectors and Characteristic Polynomial#维数和重数|algebraic multiplicities]] $m_j$. Then:
1. For each eigenvalue;
	- $K_\lambda = \ker(T-\lambda E)^m$
	- $\dim K_\lambda = m$
2. $V = K_{\lambda_1} \oplus\cdots\oplus K_{\lambda_k}$, that is, there exists a basis of $V$ consisting generalized eigenvectors

# Properties
Let $\lambda$ be an eigenvalue of $T\in \mathcal{L}(V)$. Then
1. The eigenspace $V_\lambda$ is a [[Linear Space#子空间|subspace]] of $K_\lambda$
2. $K_\lambda$ is $T$-[[Invariant Subspace|invariant]]
3. Suppose $K_\lambda$ is finite-dimensional and $t \neq \lambda$. Then
	- $K_\lambda$ is $(T-kE)$-invariant and the restriction of $T-kE$ to $K_\lambda$ is an [[Linear Isomorphism|isomorphism]]
	- If $t$ is another eigenvalue, then $K_\lambda\cap K_t=\left\{ \boldsymbol 0 \right\}$. 

# Basis of a Jordan block
A *cycle of generalized eigenvectors* for a linear operator $T$ is a set
$$
\beta_{\boldsymbol x} = \left\{ (T-\lambda E)^{k-1}(\boldsymbol x), \ldots,(T-\lambda E)(\boldsymbol x), \boldsymbol x \right\} 
$$
where the *generator* $\boldsymbol x\in K_\lambda$ is non-zero and $k$ is minimal such that $(T-\lambda E)^k(\boldsymbol x) = \boldsymbol 0$

Then,
1. $\beta_{\boldsymbol x}$ is linearly independent and thus a basis of $\left< \beta_{\boldsymbol x} \right>$
2. $\left< \beta_{\boldsymbol x} \right>$ is $T$-invariant. With respect to $\beta_{\boldsymbol x}$, the matrix of the restriction of $T$ is the $k\times k$ [[Jordan Canonical Form#Jordan块|Jordan block]], that is
$$
\left[ T_{\left< \beta_{\boldsymbol x} \right> } \right]_{\beta_{\boldsymbol x}}  = J_k(\lambda)
$$


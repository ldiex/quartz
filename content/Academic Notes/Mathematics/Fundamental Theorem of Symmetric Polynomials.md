# 基本对称多项式
$$
\begin{aligned}
\sigma_1 &= \sum_{1 \le i \le n} x_i \\
\sigma_2 &= \sum_{1 \le i < j\le n} x_i x_j \\
\sigma_3 &= \sum_{1 \le i < j < k\le n} x_i x_j x_k \\
\cdots &= \cdots
\end{aligned}
$$
*基本对称多项式（Elementary Symmetric Polynomial）* 之所以重要，是因为由代数基本定理可以得到任意一个域$F$上的$n$阶多项式（不妨设首项系数为$1$, 化成[[Multivariate Polynomial Ring#首一多项式| 首一多项式]]）都有$n$个零点，故可以分解为
$$
f(x) = (x - x_1)(x - x_2) \cdots (x - x_n)
$$
展开后可以得到
$$
f(x) = x^n - \sigma_1 x^{n - 1} + \sigma_2 x^{n - 2} + \cdots + (-1)^k \sigma_k x^{n - k} + \cdots + (-1)^n\sigma_n
$$
由此可以直接给出*韦达定理*

# 对称多项式基本定理
对于$\forall f \in F[x_1, \cdots, x_n]$是对称多项式, $\exists g \in F[x_1, \cdots, x_n] \text{ s.t. } f = g(\sigma_1, \cdots, \sigma_n)$
也就是说**任意对称多项式都可以由基本对称多项式的多项式表示出**

# Newton 恒等式
设
$$
s_k = x_1^k +x_2^k + \cdots x_n^k,\quad k = 0, 1, 2,\cdots
$$
则有
$$
k\sigma_k = \sum_{i = 1}^k(-1)^{i -1}\sigma_{k -i}s_i
$$





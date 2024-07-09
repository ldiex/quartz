# 正项级数不能通过单调减$+$极限为$0$来判断收敛
这个是判断[[Polynomial Series#交错级数]]的条件

# Dirichlet 和
$$
\frac{1}{2} + \sum_{k = 1}^n \cos kx = \dfrac{\sin \left(n + \dfrac{1}{2}\right)x}{2\sin \dfrac{x}{2}}
$$
# 比较判别法只对正项级数有效

# 一个本质
$$
\left(\sum_{n = 0}^{\infty} \dfrac{a^n}{n!}\right) \left(\sum_{n = 0}^{\infty} \dfrac{b^n}{n!}\right) = \sum_{n = 0}^{\infty} \dfrac{(a+b)^n}{n!} \iff e^a \times e^b = e^{a+b}
$$
# 关于$\sup$的计算
$$
f(x) = 1 -x^n, \quad x \in [0,1) \implies \sup_{x \in[0, 1)} f(x) = 0
$$
# 连续性
若$f_n(x)$在$[a, b]$上连续，则有
$$
\forall x \in [a,b), \left|{f_n(x)-f_m(x)}\right| < \varepsilon \implies \lim_{x \to b^-}\left|{f_n(x)-f_m(x)}\right| \le \varepsilon
$$
如果没有连续性保证，右边的极限可能不存在

**所有开区间上的问题，都需要考虑在端点是否连续的问题（如果在端点处间断了？）**


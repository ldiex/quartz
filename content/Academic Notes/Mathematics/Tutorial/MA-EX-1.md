# 级数结合律只有在绝对收敛时成立
$$
(\frac{1}{2} + \frac{1}{3}) + (\frac{1}{2^2} + \frac{1}{3^2}) + \cdots \neq \frac{1}{2} + \frac{1}{3} + \frac{1}{2^2} + \frac{1}{3^2} + \cdots
$$
正确的解法是
因为$\sum \dfrac{1}{2^n}$和$\sum \dfrac{1}{3^n}$收敛，故利用级数的线性有$\sum (\dfrac{1}{2^n} + \dfrac{1}{3^n}) = \sum \dfrac{1}{2^n} + \sum \dfrac{1}{3^n}$
或者计算有限和$\sum_{k = 1}^n  (\dfrac{1}{2^k} + \dfrac{1}{3^k})$,在有限和中可以使用交换律和结合律，最后再取极限
# 交换律也一般不成立

设$S_n = \sum_{k = 1}^n u_k, T_n = \sum_{k = 1}^n v_n$, 那么不能通过$\{S_n + T_n\}$发散推出级数$\sum (u_n + v_n)$发散

# 抽象问题用Cauchy，具体问题具体分析
证明：正项级数$\sum u_n, \sum v_n$发散$\implies \sum (u_n+ v_n)$发散
对于抽象的级数，一般采用[[Polynomial Series#级数收敛的Cauchy准则| Cauchy准则]]判断，计算$S_n$的极限一般只用于具体的级数。具体证明略

# 利用积分判别法的条件是$f$为$[1, +\infty)$上的减函数

另，$\sum u_n$收敛可以推出$\displaystyle \lim_{n \to \infty} u_n = 0$但是$\displaystyle \int_0^\infty f(x) \mathrm{d} x$收敛不能推出$\displaystyle \lim_{n \to \infty} f(x) = 0$，因为这个极限可能不存在


例：对于级数$\sum \dfrac{n}{n^2 + 1}$, 其数列在$[1, \infty)$上单调减. 考虑反常积分$\displaystyle \int_1^\infty \frac{x}{x^2 + 1} \mathrm{d} x$有$\dfrac{x}{x^2 + 1} \sim \dfrac{1}{x} \quad (x \to \infty)$  故该积分发散，原级数发散








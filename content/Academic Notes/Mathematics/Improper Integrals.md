## 无穷积分
### 比较原则
考虑到函数$f(x) = \dfrac{1}{x^p}$，当$p = 1$时它在$(0, a], [a, +\infty)$上都是发散的，当$p > 1$时它在$[a, +\infty)$上收敛，当$p < 1$时在$(0, a]$上收敛
**Cauchy判据:** 设$f$是定义于$[a, +\infty)(a >0)$上的函数，且在任何有限区间$[a, u]$上可积，则有:
1. 当$0 \le f(x) \le \dfrac{1}{x^p},\; p > 1$时，$\displaystyle \int_a^{+\infty} f(x) \mathrm{d}x$收敛;
2. 当$f(x) \ge \dfrac{1}{x^p},\; p \le 1$时，$\displaystyle \int_a^{+\infty} f(x) \mathrm{d}x$发散;
**推论:** 设$f$是定义于$[a,+\infty)$上的非负函数，在任何有限区间$[a,u]$上可积，且
$$
	\lim_{x\to + \infty} x^p f(x) = \lambda
$$
则有
1. 当$p > 1, 0 \le \lambda < +\infty$时，$\displaystyle \int_a^{+\infty} f(x)\mathrm{d}x$收敛
2. 当$p \le 1, 0 < \lambda \le +\infty$时，$\displaystyle \int_a^{+\infty} f(x)\mathrm{d}x$发散
**注意上面能否取到$0$和$+\infty$的条件不同**
### A-D 判别法
1. 若$\displaystyle \int_a^{+\infty} f(x) \mathrm{d} x$收敛，$g(x)$在$[a,\infty)$上单调有界，则$\displaystyle \int_a^{+\infty} f(x)g(x) \mathrm{d} x$收敛
2. 若$\displaystyle \int_a^{+\infty} f(x) \mathrm{d} x$在$[a, \infty)$上有界，$g(x)$在$[a,\infty)$上当$x\to +\infty$时单调趋于$0$，则$\displaystyle \int_a^{+\infty} f(x)g(x) \mathrm{d} x$收敛
## 瑕积分
**例子:**$\displaystyle \int_0^1 \ln x \mathrm{d}x$收敛，可以由其原函数的极限直接得到
### Cauchy 准则
瑕积分$\displaystyle \int_a^b f(x) \mathrm{d} x$（瑕点为$a$）收敛的充要条件是: 任给$\varepsilon > 0$，存在$\delta > 0$，只要$u_1,u_2 \in (a, a + \delta)$，总有
$$
	\left|\int_{u_1}^{b} f(x)\mathrm{d}x - \int_{u_2}^{b} f(x)\mathrm{d}x\right| = \left|\int_{u_1}^{u_2} f(x) \mathrm{d}x\right| < \varepsilon
$$
### 比较原则
选用$\displaystyle \int_a^b \frac{\mathrm{d}x}{(x-a)^p}$为比较对象，有如下推论（**Cauchy判据**）
1. 当$\displaystyle 0 \le f(x) \le \frac{1}{(x-a)^p},\; 0 < p < 1$时，$\displaystyle \int_a^b f(x) \mathrm{d} x$收敛;
2. 当$\displaystyle f(x) \ge \frac{1}{(x - a)^p},\; p \ge 1$时，$\displaystyle \int_a^b f(x) \mathrm{d} x$发散

**推论:** 设$f$是定义于$(a, b]$上的非负函数，在任何$[u, b] \subset (a, b]$上可积，且
$$
	\lim_{x\to a^+} (x-a)^p f(x) = \lambda
$$
则有
1. 当$0 < p < 1, 0 \le \lambda < +\infty$时，$\displaystyle \int_a^{b} f(x)\mathrm{d}x$收敛
2. 当$p \ge 1, 0 < \lambda \le +\infty$时，$\displaystyle \int_a^{b} f(x)\mathrm{d}x$发散

## 总结：反常积分的判定方法
1. 直接积分判断极限是否存在
2. 比较原则-$Cauchy$判据
3. $A-D$判别法
4. $Cauchy$准则


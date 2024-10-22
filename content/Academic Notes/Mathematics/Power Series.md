*幂级数*是由幂函数序列$\{a_n(x-x_0)^n\}$所产生的[[Function Series | 函数项级数]]
通过坐标平移, 我们着重讨论$x_0 = 0$的情况, 即
$$
\sum_{n = 0}^\infty a_n x^n = a_0 + a_1 x + \cdots + a_n x^n + \cdots
$$
# 幂级数的收敛区间
## Abel 定理
- 若幂级数在$x = \bar x \neq 0$处收敛, 则对满足不等式$|x| < |\bar x|$的任何$x$, 该幂级数收敛且绝对收敛
- 若幂级数在$x = \bar x$处发散, 则对满足不等式$|x| > |\bar x|$的任何$x$, 该幂级数发散

由此定理可知, 幂级数的收敛域是**以原点为中心的区间**. 若以$2R$表示这个区间的长度, 则称$R$为幂级数的*收敛半径* , 也就是**使得幂级数收敛的那些收敛点绝对值的上确界**, 我们称这个区间$(-R, R)$为该级数的*收敛区间*

当$0 < R < \infty$时, 幂级数在$(-R, R)$上收敛, 在$(-\infty, -R) \cup (R, +\infty)$上发散, 在$R, -R$上**既有可能收敛也有可能发散**

## 收敛区间的计算
设
$$
\rho = \lim_{n \to \infty} \sqrt[n]{\left|{a_n}\right|} \tag{$\ast$}
$$
则
$$
R = 
\begin{cases}
\dfrac{1}{\rho}, &0 < \rho < + \infty \\
+\infty, &\rho = 0 \\
0, & \rho = + \infty
\end{cases}
$$
又在[[Polynomial Series#正项级数]]中的根式判别法比比式判别法更强, 也有
$$
\lim_{n \to \infty} \dfrac{a_{n + 1}}{a_n} = \rho \implies \lim_{n \to \infty} \sqrt[n]{\left|{a_n}\right|} = \rho
$$
故也可通过计算比式的极限来计算收敛半径
计算收敛区间时, 要注意考虑$x = \pm R$时的特殊状况

# 幂级数的性质
## 一致收敛性
幂级数在其收敛域内的任何闭自区间上都一致收敛

若幂级数在$x = R(x = -R)$时收敛, 则其在$[0, R] \left([-R, 0]\right)$上一致收敛

## 和函数的连续性
幂级数的和函数是$(-R, R)$上的连续函数

**若幂级数在收敛区间的左（右）端点上收敛, 则其和函数也在这一端上左（右）连续**

## 逐项求导、求积
一个幂级数逐项求导、求积后得到的新幂级数的收敛区间和原幂级数相同

因此设幂级数在$(-R, R)$上的和函数$f$, 对$\forall x \in (-R, R)$
- $f$在点$x$上可导且
$$
f'(x) = \sum_{n = 0}^\infty na_nx^{n - 1}
$$
- $f$在$[0, x]$上可积, 且
$$
\int_0^x f(t) \mathrm{d} t = \sum_{n = 0}^\infty \dfrac{a_n}{n + 1}x^{n + 1}
$$
上述推论可以推广到任意高阶导数, 且我们可以通过$f$的高阶导数（只需要在$x = 0$的某邻域内有定义）反推出幂级数的各项系数
$$
a_0 = f(0), \quad a_n = \dfrac{f^{(n)}(0)}{n!} \; (n =1, 2, \cdots)
$$
# 幂级数的运算
## 幂级数相等
- 若两个幂级数在$x = 0$的某个邻域内有相同的和函数, 则称这两个幂级数在该邻域内*相等*
- 若两个幂级数在$x = 0$的某个邻域内相等, 则它们**同次幂项的系数相等**
## 幂级数运算
$$
\begin{aligned}
\lambda \sum_{n = 0}^\infty a_n x^n &= \sum_{n = 0}^\infty \lambda a_n x^n \\
\sum_{n = 0}^\infty a_n x^n \pm \sum_{n = 0}^\infty b_n x^n &= \sum_{n = 0}^\infty (a_n \pm b_n)x^n \\
\left(\sum_{n = 0}^\infty a_n x^n\right)\left(\sum_{n = 0}^\infty b_n x^n\right) &= \sum_{n = 0}^\infty c_n x^n, \quad c_n = \sum_{k = 0}^n a_k b_{n - k}
\end{aligned}
$$
上述等式在涉及幂级数的收敛区间中的最小的那个区间内成立
## 和函数的计算
- **首先计算幂级数的收敛区间**
- 如$\displaystyle \sum_{n = 0}^\infty \dfrac{(-1)^{n}}{n + 1} x^n$采用逐项积分
- 如$\displaystyle \sum_{n = 1}^\infty (-1)^{n - 1} n^2 x^n$恰当地把$x$提出和号、多次逐项积分 （具体规律参考有限微积分中的下降阶乘幂）
- 如$\displaystyle \sum_{n = 1}^\infty \dfrac{n}{2^n}$可以构造某个幂级数最后令$x = 1$得到
- (总是想办法把上面的幂级数化成基本几何级数的形式)

# 函数的幂级数展开
## Taylor 级数
如果函数$f$在$x_0$处存在任意阶的导数, 则称级数
$$
f(x_0) + f'(x_0)(x - x_0) + \cdots + \dfrac{f^{(n)}(x_0)}{n!}(x - x_0)^n + \cdots
$$
为$f$在$x_0$处的*Taylor级数*,  但是这个级数在$x_0$附近的和函数不一定就是$f$, 如以下典型反例
$$
f(x) = \begin{cases} e^{-1/x^2}, & x \neq 0 \\ 0, & x = 0\end{cases}
$$
它在$0$处的任意阶导数都是$0$, 所以它的Taylor级数的核函数在$0$附近应恒为$0$, 故$f(x) \neq S(x)$

### 判定标准
设函数$f$在$x_0$处具有任意阶导数, 那么$f$在区间$(x_0 - r, x_0 + r)$上等于它的Taylor级数的和函数的充要条件是: 对一切满足不等式$|x - x_0|<r$的$x$, 有
$$
\lim_{n \to \infty} R_n(x) = 0
$$
这里$R_n(x)$是$f$在$x_0$处的Taylor余项, 注意这三种余项形式
- 积分型余项
$$
R_n(x) = \dfrac{1}{n!} \int_0^x f^{(n + 1)} (t) (x - t)^n \mathrm{d} t
$$
- Lagrange 余项
$$
R_n(x) = \dfrac{1}{(n + 1)!} f^{(n + 1)}(\xi)x^{n + 1}, \quad 0 < \xi < x
$$
- Cauchy 余项
$$
R_n(x) = \dfrac{1}{n!} f^{(n + 1)} (\theta x)(1 - \theta)^n x^{n + 1}, \quad 0 < \theta < 1
$$
# 初等函数的幂级数展开式
## 多项式函数
$k$次多项式函数的幂级数展开式就是它本身
## $f(x) = e^x$
由于
$$
\lim_{n \to \infty} R_n(x) = \lim_{n \to \infty} \dfrac{e^{\theta x}}{(n + 1)!}x^{n + 1} = 0, \quad \forall x \in \mathbb R
$$
故
$$
e^x = \sum_{k = 0}^\infty \dfrac{x^k}{k!}, \quad \forall x \in \mathbb R
$$
## $f(x) = \sin x, f(x) = \cos x$
也在$\forall x \in \mathbb R$上都存在

## $f(x) = \ln (1 + x)$

$$
\begin{aligned}
&f(x) = \ln(1 + x) \\
& f^{(n)}(x) = (-1)^{n - 1} \dfrac{(n - 1)!}{(1 + x)^n} \\
\end{aligned}
$$
故有Taylor级数
$$
x - \dfrac{x^2}{2} + \dfrac{x^3}{3}-\dfrac{x^4}{4} + \cdots + (-1)^{n - 1} \dfrac{x^n}{n} + \cdots
$$
利用比值判别法得到该级数的收敛半径为$1$, 收敛区间为$(-1, 1]$
- 当$0 \le x \le 1$时用Lagrange余项
$$
\abs {R_n} = \left|{\dfrac{1}{(n + 1)!}(-1)^n \dfrac{n!}{(1 + \xi)^{n + 1}}x^{n + 1}}\right| = \left|{\dfrac{(-1)^n}{n + 1}\left(\dfrac{x}{1 + \xi}\right)^{n + 1}}\right| \le \dfrac{1}{n + 1} \to 0
$$
- 当$-1 < x < 0$时用Cauchy余项
$$
\begin{aligned}
\left|{R_n}\right| &= \left|{\dfrac{1}{n!}(-1)^n \dfrac{n!}{(1 + \theta x)^{n+1}} (1-\theta)^n x^{n + 1}}\right| \\
&= \dfrac{1}{1 + \theta x} \left(\dfrac{1 - \theta}{1 + \theta x}\right)^n |x|^{n + 1}
\end{aligned}
$$
$-1 < x < 0 \implies 1 - \theta \le 1 + \theta x \implies 0 \le \dfrac{1 - \theta}{1 + \theta x} \le 1$
$$
\left|{R_n(x)}\right| \le \dfrac{|x|^{n + 1}}{1 - |x|} \to 0
$$
故在$(-1, 1]$上成立
## $f(x) = (1 + x)^\alpha$
$$
1 + \alpha x + \dfrac{\alpha(\alpha - 1)}{2!}x^2 + \cdots + \dfrac{\alpha(\alpha - 1)\cdots(\alpha - n + 1)}{n!} + \cdots
$$
**其收敛区间**
- $(-1, 1), \quad \alpha \le -1$
- $(-1,1], \quad -1 < \alpha < 0$
- $[-1, 1] \quad \alpha > 0$

### 两个特殊情况
- 令$\alpha = -1$并令$x^2 \to x$
$$
\dfrac{1}{1 + x^2} = 1 -x^2 + x^4 + \cdots + (-1)^n x^{2n} + \cdots, \quad x \in (-1, 1)
$$
- 令$\alpha = -1/2$并令$x^2 \to x$
$$
\dfrac{1}{\sqrt{1 + x^2}} = 1 + \dfrac{1}{2}x^2 + \dfrac{1 \cdot 3}{2 \cdot 4} x^4 + \dfrac{1 \cdot 3 \cdot 5}{2 \cdot 4 \cdot 6} x^6 + \cdots, \quad x \in (-1, 1)
$$
通过积分即可得到$\arctan x, \arcsin x$的幂级数展开式







# 二元极限练习
$$
\lim_{ (x, y) \to (0,0) } \dfrac{xy}{\sqrt{ x + y + 1 } - 1} 
$$
$$
\begin{align}
0 &\le \left|{\lim_{ (x, y) \to (0,0) } \dfrac{xy}{\sqrt{ x + y + 1 } - 1}}\right|  \le \lim_{ (x, y) \to (0,0) } \dfrac{(x + y)^2}{\left|{\sqrt{ x + y + 1 } - 1}\right|}  \\
&= \lim_{ t \to 0 } \dfrac{t^2}{\left|{\sqrt{ t + 1 } - 1}\right|} = \lim_{ t \to 0 } \dfrac{t^2}{\left|{\frac{1}{2}t}\right|}  = 0 \\
&\implies \lim_{ (x, y) \to (0,0) } \dfrac{xy}{\sqrt{ x + y + 1 } - 1} = 0
\end{align} 
$$
**这个做法是错误的**
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{xy^3}{x^2 + y^6}
$$
取路径$1: x = y$, 有
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{x^4}{x^2 + x^6} = +\infty
$$
取路径$2:x = y^3$, 有
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{x^6}{x^6 + x^6} = \dfrac{1}{2}
$$
故极限不存在（或者直接取$x = ky^3$）

$$
\lim_{ (x, y) \to (0, 0) } \dfrac{x^6y^8}{(x^2+y^4)^5}
$$
取路径$1$: $x = y$, 有
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{x^{14}}{(x^2 + x^4)^5} = \lim_{ (x, y) \to (0, 0) } \dfrac{x^{14}}{x^{20} + o(x^{20})} = + \infty
$$
取路径$2: x = y^2$，有
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{y^{20}}{2^5 y^{20} } = \dfrac{1}{2^5}
$$
故极限不存在（或者直接取$x = ky^2$）
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{e^x - e^y}{\sin xy}
$$
由Taylor展开
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{e^x - e^y}{\sin xy} =  \lim_{ (x, y) \to (0, 0) } \dfrac{x - y}{xy}
$$
取两条路径$x = y, x = -y$即可知极限不存在

# 习题
## T1
$\{na_n\}$收敛，$\sum_{n = 2}^\infty n(a_n - a_{n - 1})$收敛，证明$\sum_{n = 1}^\infty a_n$收敛

计算
$$
\begin{aligned}
\sum_{n=2}^mn(a_n-a_{n-1}) = na_n-\sum_{n = 2}^{m-1}a_n - 2a_1
\end{aligned}
$$
两边取极限有
$$
\sum_{n = 2}^\infty n(a_n - a_{n-1}) = \lim_{n \to \infty} n a_n - \sum_{n=2}^\infty a_n-2a_1
$$
所以有
$$
\sum_{n = 1}^\infty a_n = -a_1+\lim_{n\to \infty} na_n - \sum_{n = 2}^\infty n(a_n-a_{n-1})
$$
右边是有限的，故左边收敛

## T2
连续函数$f_n(x)$一致收敛于$f(x)$, $f(x)$在$[a, b]$无零点，证明在$n$充分大时$f(x)$在$[a,b]$无零点，且$\dfrac{1}{f_n(x)}$一致收敛于$\dfrac{1}{f(x)}$


不妨设无零点连续函数$f(x) > 0$，在闭区间$[a, b]$上必有最小值$m$
$$
\forall \varepsilon > 0, \exists \delta > 0, \text{s.t. } n > \delta \implies 0 < f(x) - \varepsilon < f_n(x) < f(x) + \varepsilon
$$
取$\varepsilon = m$即可

第二小问只需注意到
$$
\left|{\dfrac{1}{f_n(x)} -\dfrac{1}{f(x)}}\right| = \dfrac{\left|{f_n(x) - f(x)}\right|}{\left|{f_n(x)f(x)}\right|} \le \dfrac{\left|{f_n(x) - f(x)}\right|}{mM} \le \dfrac{\varepsilon}{mM}
$$

## T3
已知
$$
\begin{cases}
x = -u^2 + v + z  \\
y = u + vz
\end{cases}
$$
求$\displaystyle \dfrac{\partial {u}}{\partial {x}}, \dfrac{\partial {v}}{\partial {x}}, \dfrac{\partial {u}}{\partial {z}}$

$$
\begin{cases}
\mathrm{d} x= -2u \mathrm{d} u + \mathrm{d} v + \mathrm{d} z  \implies z\mathrm{d} x = - 2uz \mathrm{d} u + z \mathrm{d} v + z \mathrm{d} z\\
\mathrm{d} y = \mathrm{d} u + z \mathrm{d} v + v \mathrm{d} z
\end{cases}
$$
于是
$$
z \mathrm{d} x - \mathrm{d} y = -(2uz + 1) \mathrm{d} u + (z - v) \mathrm{d} z
$$
故
$$
\mathrm{d} u = -\dfrac{1}{2uz + 1} \left(z \mathrm{d} x - \mathrm{d} y + (v - z) \mathrm{d} z\right)
$$
于是有
$$
\dfrac{\partial {u}}{\partial {x}} = -\dfrac{z}{2uz + 1}; \; \dfrac{\partial {u}}{\partial {z}} = \dfrac{z-v}{2uz + 1}
$$
同理可给出$\displaystyle \dfrac{\partial {v}}{\partial {x}}$

若$f(x)$在$[-\pi, +\pi]$上可积，则有
$$
\dfrac{a_0^2}{2} + \sum_{n = 1}^\infty (a_n^2 + b_n^2) \le \dfrac{1}{\pi}\int_{-\pi}^\pi f^2(x) \mathrm{d} x
$$
其中$a_n, b_n$为$f$的[[Fourier Series#以$2 pi$为周期的函数的Fourier级数 | Fourier 系数]]
注意这里可积直接蕴含了平方可积

在实函数空间$R^R$中，对$f \in R[a, b]$定义模长
$$
\left|{f(x)}\right| = \sqrt{(f,f)} = \sqrt{\int_a^b f^2(x)\mathrm{d} x}
$$
考虑勾股定理，若向量$\alpha_1, \cdots, \alpha_n$两两正交，则
$$
\left|{\sum_{i = 1}^n \alpha_i}\right|^2 = \sum_{i = 1}^n \left|{a_i}\right|^2
$$
在无穷维空间中，上述定理退化为不等式
$$
\left|{\sum_{i = 1}^\infty \alpha_i}\right|^2 \ge \sum_{i = 1}^\infty \left|{a_i}\right|^2
$$
如此，要证明Bessel不等式，只需要证明
$$
\pi\left(\dfrac{a_0^2}{2} + \sum_{n = 1}^\infty (a_n^2 + b_n^2)\right) \le \left|{f(x)}\right|^2
$$
注意到
$$
\begin{aligned}
\int_{-\pi}^\pi 1\mathrm{d} x = 2\pi &\implies |1(x)|^2 = 2\pi \\
\int_{-\pi}^\pi \cos^2 n x \mathrm{d} x = \pi &\implies |\cos(nx)|^2 = \pi \\
\int_{-\pi}^\pi \sin^2 n x \mathrm{d} x = \pi &\implies |\sin(nx)|^2 = \pi
\end{aligned}
$$
故有
$$
\begin{aligned}
|f(x)|^2 &\sim \left|{\dfrac{a_0}{2} + \sum_{n = 1}^\infty(a_n\cos nx + b_n \sin nx)}\right|^2 \\ &\ge \left|{\dfrac{a_0}{2}(x)}\right|^2 + \sum_{n = 1}^\infty |a_n\cos nx|^2 + \sum_{n = 1}^\infty |b_n \sin nx|^2 \\
&= \dfrac{a_0^2}{2}\pi^2 + \pi\sum_{n = 1}^\infty(a_n^2 + b_n^2)
\end{aligned}
$$
故Bessel不等式得证

若$f$的Fourier级数在$[-\pi, \pi]$上一致收敛于$f$, 则
$$
\dfrac{a_0^2}{2} + \sum_{n = 1}^\infty (a_n^2 + b_n^2) = \dfrac{1}{\pi}\int_{-\pi}^\pi f^2(x) \mathrm{d} x
$$
这就是*Parseval等式*

# 推论: Riemann-Lebesgue 定理
若$f \in \mathbb R[-\pi,\pi]$则
$$
\begin{aligned}
\lim_{n \to \infty} \int_{-\pi}^\pi f(x) \cos nx \mathrm{d} x = 0 \\
\lim_{n \to \infty} \int_{-\pi}^\pi f(x) \sin nx \mathrm{d} x = 0
\end{aligned}
$$
证明

当$n \to \infty$时，Bessel不等式左边级数应当收敛，有必要条件知$a_n^2 + b_n^2 \to 0$, 即$a_n \to 0$且$b_n \to 0$，由Fourier系数的定义，命题得证


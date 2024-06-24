# Fourier 级数
具体参见[[Fourier Series]]，我们直接给出其形式:
函数$f$的Fourier级数展开式是
$$
f(x) \sim \dfrac{a_0}{2} + \sum_{n = 1}^{\infty} \left(a_n \cos \dfrac{n\pi x}{l} + b_n \sin \dfrac{n\pi x}{l}\right)
$$
其中
$$
\begin{aligned}
a_n &= \dfrac{1}{l}\int_{-l}^l f(x) \cos \dfrac{n\pi x}{l} \mathrm{d} x, \quad n = 0, 1, 2, \cdots \\
b_n &= \dfrac{1}{l}\int_{-l}^l f(x) \sin \dfrac{n\pi x}{l} \mathrm{d} x, \quad n = 1, 2, \cdots
\end{aligned}
$$
# Fourier 级数的复数形式
由[[Euler's Formula|Euler公式]]我们可推出
$$
\cos \theta = \dfrac{\mathrm{e}^{\mathrm{i}\theta}+\mathrm{e}^{-\mathrm{i}\theta}}{2}, \quad \sin \theta = -\mathrm{i}\left( \dfrac{\mathrm{e}^{\mathrm{i}\theta}-\mathrm{e}^{-\mathrm{i}\theta}}{2} \right) 
$$
讲其代入上面的级数表达式中，假设级数收敛，设$\omega = \dfrac{2\pi}{T} = \dfrac{2\pi}{2l} = \dfrac{\pi}{l}$即有
$$
\begin{aligned}
f(x) & = \dfrac{a_0}{2} + \sum_{n = 1}^\infty \left( a_n \dfrac{\mathrm{e}^{\mathrm{i}n\omega_0x}+\mathrm{e}^{-\mathrm{i}n\omega_0x}}{2}-\mathrm{{i}}b_n\dfrac{\mathrm{e}^{\mathrm{i}n\omega_0x}-\mathrm{e}^{-\mathrm{i}n\omega_0x}}{2}\right) \\
 & =\dfrac{a_0}{2} + \sum_{n = 1}^\infty \dfrac{1}{2}(a_n - \mathrm{i}b_n) \mathrm{e}^{\mathrm{i}n\omega_0x} + \sum_{n = 1}^\infty \dfrac{1}{2}(a_n + \mathrm{i}b_n)\mathrm{e}^{\mathrm{i}n\omega_0x} \\
 & =\dfrac{a_0}{2} + \sum_{n = 1}^\infty \dfrac{1}{2}(a_n - \mathrm{i}b_n) \mathrm{e}^{\mathrm{i}n\omega_0x} + \sum_{n = -\infty}^{-1} \dfrac{1}{2}(a_{-n} + \mathrm{i}b_{-n})\mathrm{e}^{\mathrm{i}n\omega_0x} \\
 & = \sum_{-\infty}^\infty d_n \mathrm{e}^{\mathrm{i}n\omega_0x}
\end{aligned}
$$
其中
$$
d_n = \begin{cases}
\dfrac{1}{2}(a_n - \mathrm{i}b_{-n}),  & n>0 \\
\dfrac{1}{2}a_0,  & n = 0 \\
\dfrac{1}{2}(a_{-n}-\mathrm{i} b_{-n}), & n < 0
\end{cases}
$$
可以验证，无论$n$取什么值，$d_n$都可以表示为
$$
d_n = \dfrac{1}{2l}\int_0^{2l}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x = \dfrac{1}{T}\int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x
$$
其中$\omega_0=\dfrac{2\pi}{T}$被称为*基频率*，由此我们得到复指数形式Fourier级数展开的完整表达式
$$
f(x) = \sum_{n =-\infty}^{+\infty} \left[ \dfrac{1}{T} \int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x\right] \mathrm{e}^{\mathrm{i}n\omega_0x}
$$
# Fourier变换
傅里叶级数展开是针对**周期函数**的，但是在现实中大多数信号都是非周期的。非周期函数可以看作是周期$T\to +\infty$的周期函数，当$T = +\infty$时，基频率$\omega_0$就变成了微分$\mathrm{d} \omega$，就需要把求和转化成积分
$$
\begin{aligned}
f(x) & = \sum_{n =-\infty}^{+\infty} \left[ \dfrac{1}{T} \int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x\right] \mathrm{e}^{\mathrm{i}n\omega_0x} \\
 & =  \sum_{n =-\infty}^{+\infty} \left[ \dfrac{\omega_0}{2\pi} \int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x\right] \mathrm{e}^{\mathrm{i}n\omega_0x} \\
 & = \sum_{n =-\infty}^{+\infty} \left[ \omega \int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x\right] \mathrm{e}^{\mathrm{i}n\omega_0x} 
\end{aligned}
$$
这里取了$\omega = \dfrac{\omega_0}{2\pi}$，令$\omega = \mathrm{d} \omega\to 0$则有
$$
f(x)=\frac1{2\pi}\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}e^{-i2\pi\omega x}\cdot f(x)\mathrm{~}\mathrm{d} x\cdot e^{i2\pi\omega x}\mathrm{~}\mathrm{d} \omega 
$$
其中
$$
F(\omega) = \int_{-\infty}^{+\infty}e^{-i2\pi\omega x}\cdot f(x)\mathrm{~}\mathrm{d} x
$$
被称为*Fourier变换*，而
$$
f(x)=\frac1{2\pi}\int_{-\infty}^{+\infty}F(\omega)\cdot e^{i2\pi\omega x}\mathrm{~}\mathrm{d} \omega 
$$
则被称为*Fourier逆变换*

# Fourier变换的应用
[[Fourier Transformation in Optics|Fourier变换在光学中的应用]]
[[Fourier Optics|Fourier光学]]

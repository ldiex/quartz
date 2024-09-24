# Fourier级数
## 三角级数
考虑无穷个简谐运动的叠加
$$
A_0 + \sum_{n = 1}^{\infty} A_n \sin(n\omega x +\varphi_n)
$$
由于$x$是任意取的，所以讨论$\omega = 1$的情况，此时有
$$
\begin{aligned}
A_0 + \sum_{n = 1}^{\infty} A_n \sin(n x +\varphi_n)
&=A_0 + \sum_{n = 1}^\infty (A_n\sin\varphi_n \cos nx + A_n\cos\varphi_n \sin nx) \\
&= \dfrac{a_0}{2} + \sum_{n = 1}^\infty (a_n\cos nx + b_n \sin nx) 
\end{aligned}
$$
其中有
$$
A_0 = \dfrac{a_0}{2}, \; A_n \sin \varphi_n = a_n, \; A_n \cos \varphi_n = b_b, \; n = 1, 2, \cdots
$$
它是由*三角函数列* （*三角函数系*）
$$
1, \cos x, \sin x, \cos 2x, \sin 2x , \cdots, \cos nx, \sin nx, \cdots
$$
所产生的一般形式的*三角级数*

### 三角级数的收敛性
若级数
$$
\dfrac{|a_0|}{2} + \sum_{n = 1}^\infty (|a_n| + |b_n|)
$$
收敛，则由[[Function Series#Werierstrass 判别法]]可知上述一般的三角级数也收敛

### 三角函数系的正交性
1. 三角函数系中的函数具有共同周期$2\pi$
2. 三角函数系中每个函数在$[-\pi, \pi]$上的积分都为$0$
3. 在三角函数系中仍以两个不同的函数的乘积在$[-\pi, \pi]$上的积分都为$0$
$$
\int_{-\pi}^{\pi} \cos(mx + \dfrac{k\pi}{2}) \cos(nx) \mathrm{d} x = 0, \quad \cos(mx+ \dfrac{k\pi}{2})\neq \cos(nx)
$$
$$
\int_{-\pi}^\pi \cos^2(nx + \dfrac{k\pi}{2}) = \pi
$$
其中3.说明三角函数系在$[-\pi, \pi]$上具有*正交性*，它是*正交函数系*

## 以$2\pi$为周期的函数的Fourier级数
若在整个数轴上有
$$
f(x) = \dfrac{a_0}{2} + \sum_{n = 1}^\infty (a_n\cos nx + b_n \sin nx) 
$$
且等式右边级数[[Function Series#具体讨论：什么是一致收敛 | 一致收敛]] , 则其系数可由$f$唯一表示
$$
\begin{aligned}
a_n &= \dfrac{1}{\pi}\int_{-\pi}^\pi f(x) \cos nx \mathrm{d} x, \quad n = 0, 1, 2, \cdots \\
b_n &= \dfrac{1}{\pi}\int_{-\pi}^\pi f(x) \sin nx \mathrm{d} x, \quad n = 1, 2, \cdots
\end{aligned}
$$
这利用了[[Fourier Series#三角函数系的正交性| 三角函数系的正交性]] , 之所以取$A_0 = \dfrac{a_0}{2}$正是为了方便这点

一般来说，若$f$是以$2\pi$为周期且在$[-\pi, \pi]$上可积的函数，则由此算出的$a_n, b_n$称为函数$f$的*Fourier系数*，以$f$的Fourier系数为系数的三角级数称为$f$的*Fourier级数*，记作
$$
f(x) \sim \dfrac{a_0}{2} + \sum_{n = 1}^\infty (a_n\cos nx + b_n \sin nx)
$$
如果右边的Fourier级数
1. 一致收敛
2. 收敛于$f$本身
则可将$\sim$改为$=$

## 收敛定理
### 收敛定理
设$f(x)$是周期为$2\pi$的函数，如果它满足：
1. $f$在一个周期内连续，或只有有限个*第一类间断点*
2. $f$在一个周期内最多只有有限个极值点
那么则称$f(x)$的Fourier级数收敛，并且
- 当$x$是$f(x)$的连续点时，级数收敛于$f(x)$
- 当$x$是$f(x)$的间断点时，级数收敛于$\dfrac{1}{2}[f(x^-) + f(x^+)]$
该定理就是 *Fourier级数的收敛定理* ，或称为 *Dirichlet–Jordan充分条件* 

如果把条件加强为$f$具有二阶连续的导函数，那么它的Fourier级数在$(-\infty, +\infty)$上 [[Function Series#一致收敛性 | 一致收敛]]
### 周期延拓
在具体讨论函数的Fourier级数展开式时，常常只给出函数$f$在$(-\pi,\pi]$或$[-\pi, \pi)$上的解析表达式，但应当理解为它是定义在整个数轴上以$2\pi$为周期的函数. 即在$(-\pi, \pi]$以外的部分按照周期性作*周期延拓*

### 计算程序
1. 计算$a_0$
2. 计算$a_n,b_n$, 通常利用分部积分，可以利用[[Table Method for Integration by Parts | 表格积分法]]
3. 计算在端点 和 不连续点上，级数收敛至哪个值

#### 注意
- Fourier级数的第一项是$\dfrac{a_0}{2}$
- 由于周期性，端点的收敛值等于趋近于区间两侧的极限的平均值，两个端点的收敛值应当是一样的
- 积分上下界不一定是关于原点对称的，应该按照定义域来

# 以$2l$为周期的函数的展开式
设$f$是以$2l$为周期的函数，通过变量置换
$$
\dfrac{\pi x}{l} = t
$$
则可以把$f$变换成以$2\pi$为周期的$t$的$F(t) = f\left(\dfrac{lt}{\pi}\right)$. 若$f$在$[-l, l]$上可积，则$F$在$[-\pi, \pi]$ 上也可积，这时函数$f$的Fourier级数展开式就是
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

# 偶函数与奇函数的Fourier级数
若$f$是定义在$[-l,l]$上的偶函数，则有
$$
f(x) \sim \dfrac{a_0}{2} + \sum_{n = 1}^{\infty} a_n \cos \dfrac{n\pi x}{l}
$$
右边的级数称为*余弦级数*

若$f$是定义在$[-l,l]$上的奇函数，则有
$$
f(x) \sim \dfrac{a_0}{2} + \sum_{n = 1}^{\infty} b_n \sin \dfrac{n\pi x}{l}
$$
右边的级数称为*正弦级数*

在实际应用中，有时候需要把定义在$[0, l]$上的函数展开成余弦级数或正弦级数. 所以，我们可以先把定义在$[0,l]$上的函数作*偶式延拓*和*奇式延拓*，使它在$[-l, l]$上成为一个偶函数/奇函数. 然后在求其的Fourier展开式

# 收敛定理的证明
## 预备定理
### [[Bessel Inequality | Bessel 不等式]]

### Fejer和
若$f(x)$是以$2\pi$为周期的函数，且在$[-\pi,+\pi]$上可积，则它的Fourier级数的部分和$S_n(x)$可写成
$$
S_n (x) = \dfrac{1}{\pi}\int_{-\pi}^\pi f(x+ t) \dfrac{\sin\left(n + \dfrac{1}{2}\right)}{2\sin \dfrac{t}{2}} \mathrm{d} t
$$
当$t = 0$时，被积函数中的不定式由极限
$$
\lim_{t = 0} \dfrac{\sin\left(n + \dfrac{1}{2}\right)}{2\sin \dfrac{t}{2}} = n + \dfrac{1}{2}
$$
来确定

# Fourier级数的复数形式
参见[[Fourier Transform#Fourier 级数的复数形式|Fourier级数的复数形式]]



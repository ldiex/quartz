# 重要提醒
## 1. 不定积分加$C$了吗!
## 2. 积分求面积的时候不要忘记加绝对值!

# 考前需背
$$
\begin{aligned}
\int \frac{\mathrm{d} x}{a^2 + x^2} &= \frac{1}{a}\arctan \frac{x}{a} +C\\
\int \frac{\mathrm{d} x}{a^2 - x^2} &= \frac{1}{2a}\ln \frac{a+x}{a-x} + C \\
\int \frac{\mathrm{d} x}{x^2 - a^2} &= \frac{1}{2a}\ln \frac{a-x}{a+x} + C \\
\int \frac{\mathrm{d} x}{\sqrt{a^2 + x^2}} &= \ln |x + \sqrt{a^2 + x^2}| + C \\
\int \frac{\mathrm{d} x}{\sqrt{a^2 - x^2}} &= \arcsin \frac{x}{a} +C \\
\int \frac{\mathrm{d} x}{\sqrt{x^2 - a^2}} &= \ln |x + \sqrt{x^2 - a^2}| + C

\end{aligned}
$$


## Riemann可积的充要条件
### 定义
$$
\forall \varepsilon > 0, \; \exists \delta > 0 \text{ s.t. } ||\mathcal{T}|| < \delta \implies |\sum_{i = 1}^n f(\xi_i) \Delta x_i - I| < \varepsilon
$$
### 判据
函数$f$在$[a,b]$上Riemann可积的充要条件是: 任给$\varepsilon > 0$，总存在相应的某一分割$\mathcal{T}$使得
$$
\sum_{\mathcal{T}} \omega_i \Delta x_i < \varepsilon
$$
其中**振幅**$\omega_i$被定义为
$$
\omega_i = \sup_{x \in \Delta_i} f(x) - \inf_{x \in \Delta_i} f(x)
$$
### 可以利用的定理
1. 有界 + 有限个间断点
2. 单调
### 处理常见的可数个不连续点的方法
思路：把含有无穷个不连续点的区间长度压得尽可能小$<\varepsilon$，通过有界性得到振幅的有界性$\to$振幅长度和为小量$\to$可积，而对于另一部分区间只有有限个不连续点，必然是可积的

## Wallis 积分
$$
n \in \mathbb{N} \implies \int_0^{\pi/2} \sin^n x \mathrm{d} x= \begin{cases}
\dfrac{(n - 1)!!}{n!!} \cdot \dfrac{\pi}{2} &, \text{$n$为偶数} \\
\dfrac{(n - 1)!!}{n!!} &, \text{$n$为奇数}
\end{cases}
$$
## Stolz 公式

### $\dfrac{\ast}{\infty}$ 型

若数列${a_n}$是严格单调递增的无穷大量，则有

$$\lim_{n \to \infty} \dfrac{b_{n+1}-b_n}{a_{n+1}-a_n} = l \implies \lim_{n \to \infty} \dfrac{b_n}{a_n} = l$$

### $\dfrac{0}{0}$型

若数列${a_n}$是严格单调递减的无穷大量，${b_n}$是无穷小量，则有

$$\lim_{n \to \infty} \dfrac{b_{n+1}-b_n}{a_{n+1}-a_n} = l \implies \lim_{n \to \infty} \dfrac{b_n}{a_n} = l$$

**注意:** 和L'Hôpital法则一样，差分之比（导数之比）的极限不存在不能说明原来的数列之比（函数之比）不存在. 

## 定积分的性质

### 积分第一中值定理

若$f$在$[a, b]$上连续，$g$在$[a, b]$上可积且**不变号**，则至少存在一点$\xi \in [a, b]$，使得
$$\int_a^b f(x)g(x) \mathrm{d} x = f(\xi) \int_{a}^{b} g(x) \mathrm{d} x$$

### 积分第二中值定理

若$f$在$[a, b]$上**单调** ，$g$在$[a, b]$上可积，则至少存在一点$\xi \in [a, b]$，使得
$$\int_{a}^{b} f(x)g(x) = f(a) \int_{a}^{\xi} g(x) \mathrm{d} x + f(b) \int_{\xi}^{b} g(x) \mathrm{d} x$$

## 变积分上限函数
$$
	\dfrac{\mathrm{d}}{\mathrm{d} {x}} \int_{g(x)}^{h(x)} f(t)\mathrm{d} t = f(h(x))h'(x) - f(g(x))g'(x)
$$

## 定积分的应用
### 面积
考虑参数方程
$$
x = \varphi(t), y = \psi(t)
$$
有
$$
\mathrm{d} S = |y \mathrm{d} x| = |\psi(t) \varphi'(t)| \mathrm{d} t
$$
**不要忘记绝对值**

### 弧长
考虑参数方程
$$
x = \varphi(t), y = \psi(t)
$$
有
$$
\mathrm{d} s = \sqrt{\mathrm{d} x^2 + \mathrm{d} y^2} = \sqrt{[\varphi'(t)]^2 + [\psi'(t)]^2} \mathrm{d} t
$$
### 曲率
考虑参数方程
$$
x = \varphi(t), y = \psi(t)
$$
有
$$
K = \frac{|\varphi'\psi'' - \varphi'' \psi '|}{|\varphi'^{2} + \psi'^{2}|^{\frac{3}{2}}}
$$
曲率半径
$$
\rho = \frac{1}{K}
$$
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
# 一些题目
## 不定积分技巧
### 换元消根号
#### 题一
$$
\int \frac{\sqrt[3]{1+\sqrt[4]{x}}}{\sqrt{x}} \mathrm{d} x
$$
令$u = \sqrt[3]{1+\sqrt[4]{x}}$，则原积分化为
$$
12 \int (u^6 - u^3) \mathrm{d} u 
$$
#### 题二
$$
\int \frac{\sqrt{x}}{1-\sqrt[3]{x}} \mathrm{d} x
$$
令$x = u^6$，然后化成关于变量$u$的有理函数积分
### 换元改次数
#### 题一
$$
\int x(1-2x)^{99} \mathrm{d} x
$$
令$t = (1 - 2x)$，则原积分化为
$$
-\frac{1}{2} \int\frac{1-t}{2}t^{99} \mathrm{d} t
$$
## 积分中值定理
设$f(x) \in C[a, b]$，若对于任意满足$\displaystyle \int_a^b g(x) \mathrm{d} x = 0$的连续函数$g(x)$，均有$\displaystyle \int_a^b f(x) g(x) \mathrm{d} x = 0$. 证明$f(x)$恒为常数
**证明:** 由积分中值定理，$\displaystyle \exists \xi \in [a,b] \text{ s.t. } f(\xi) (b - a) = \int_a^b f(x) \mathrm{d} x$ ，于是有$\displaystyle \int_a^b (f(x) - f(\xi)) \mathrm{d} x = 0$，故由题意，$\displaystyle \int_a^b f(x)(f(x) - f(\xi)) = 0$，以及显然有$\displaystyle \int_a^b f(\xi)(f(x) - f(\xi)) = 0$. 上述两式相减就可以得到
$$
\int_a^b (f(x) - f(\xi))^2 = 0 \implies f(x) - f(\xi) \equiv 0 \implies f(x) = \text{constant}
$$
![](https://pic1.zhimg.com/80/v2-44321e9513ed99137d7d4a0716135be4_1440w.webp)
直接洛必达太麻烦了，可以利用积分中值定理简化计算


## 定积分计算
### 题一
计算
$$
\int_0^\pi \frac{x\mathrm{d} x}{1 + \cos^2 x}
$$
**解**
$$
\begin{aligned}
\int_0^\pi \frac{x \mathrm{d} x}{1 + \cos^2 x} &= \int_0^\frac{\pi}{2} \frac{x \mathrm{d} x}{1 + \cos^2 x} + \int_\frac{\pi}{2}^\pi \frac{x \mathrm{d} x}{1 + \cos^2 x} \\
&= \int_0^\frac{\pi}{2} \frac{x \mathrm{d} x}{1 + \cos^2 x} + \int_{\frac{\pi}{2}}^0 \frac{(\pi - x) \mathrm{d}(\pi - x)}{1 + \cos^2 (\pi-x)} \\
&= \int_0^\frac{\pi}{2} \frac{x \mathrm{d} x}{1 + \cos^2 x} + \int_0^\frac{\pi}{2}\frac{(\pi -x)\mathrm{d} x}{1 + \cos^2 x} \\
&= \int_0^\frac{\pi}{2} \frac{\pi \mathrm{d} x}{1 + \cos^2 x} \\
\end{aligned}
$$
计算
$$
\int \frac{\mathrm{d} x}{1 + \cos^2 x} = \int \frac{\sec^2 x \mathrm{d} x}{1 + \sec^2 x} = \int \frac{\mathrm{d} (\tan x)}{2 + \tan^2 x} = \frac{1}{\sqrt2}\arctan\frac{\tan x}{\sqrt{2}} + C
$$
故
$$
\int_0^\frac{\pi}{2} \frac{\pi \mathrm{d} x}{1 + \cos^2 x} = \frac{\pi}{\sqrt{2}} (\frac{\pi}{2} - 0) = \frac{\pi ^2}{2\sqrt{2}}
$$
### 题二
设$f(x)$是在$[0, \frac{\pi}{2}]$上非负单调递增的连续函数，求证:
$$
x \int_0^x f(t)\sin t \mathrm{d} t \ge (1-\cos x) \int_0^x f(t) \mathrm{d} t
$$
**证明**
待证命题等价于
$$
\begin{aligned}
x \int_0^x f(t) 2\sin \frac{t}{2}\cos\frac{t}{2} \mathrm{d} x &\ge 2\sin^2\frac{x}{2} \int_0^x f(t) \mathrm{d} t \\
\iff  x\int_0^x f(t) 4 \sin \frac{t}{2} \mathrm{d} (\sin \frac{t}{2}) &\ge 2\sin^2\frac{x}{2} \int_0^x f(t) \mathrm{d} t \\
\iff x \int_0^x f(t) 2 \mathrm{d} (\sin^2 \frac{t}{2}) &\ge 2\sin^2\frac{x}{2} \int_0^x f(t) \mathrm{d} t \\
\iff \int_0^x f(t) \mathrm{d}(\frac{\sin^2 \dfrac{t}{2}}{\sin^2 \dfrac{x}{2}}) &\ge \int_0^x f(t) \mathrm{d}(\frac{t}{x}) 
\end{aligned}
$$
令
$$
u = g(t) = \frac{\sin^2 \dfrac{t}{2}}{\sin^2 \dfrac{x}{2}},\; v = h(t) =\frac{t}{x} \implies t = g^{-1}(u) = h^{-1}(v)
$$
于是待证命题等价于
$$
\int_0^1 f(g^{-1}(u)) \mathrm{d} u \ge \int_0^1 f(h^{-1}(v))\mathrm{d} v
$$
注意到$\displaystyle g''(t) = \frac{\cos t}{\sin^2 \dfrac{x}{2}} \ge 0$，故而$g(t)$是凸函数，$g(t) \le h(t)$，故有$g^{-1}(t) \ge h^{-1}(t)$，再结合$f(x)$单调性，$f(g^{-1}(t)) \ge f(h^{-1}(t))$，故而原命题得证.

## 积分极限
计算
$$
\lim_{n \to +\infty} \int_0^\frac{\pi}{2} \sin^n x \mathrm{d} x
$$
**解**
由
$$
\int_0^\frac{\pi}{2} \sin^n x \mathrm{d} x = \frac{n - 1}{n} \int_0^\frac{\pi}{2} \sin^{n-2} x \mathrm{d} x
$$
若$n$为偶数，考虑
$$
s_k  = \frac{1}{2} \cdot \frac{3}{4} \cdot \frac{5}{6} \cdots \frac{2k-1}{2k} < \frac{2}{3} \cdot \frac{4}{5} \cdot \frac{6}{7} \cdots \frac{2k}{2k + 1} = \frac{1}{s_k} \cdot \frac{1}{2k+1}
$$
于是
$$
s_k < \frac{1}{\sqrt{2k + 1}} \implies  \lim_{k \to +\infty} s_k = 0 \implies \lim_{n \to +\infty} \int_0^\frac{\pi}{2} \sin^n x \mathrm{d} x = 0
$$
$n$是奇数的情况也是类似的
## Taylor 展开
在$x_0 = 0$处展开$\sqrt[3]{2 -\cos x}$到$x^4$项
**解**
由
$$
\begin{aligned}
 \sqrt[3]{2-\cos x} = (1 + (1-\cos x))^{\frac{1}{3}} = 1 + \frac{1}{3}(1 -\cos x) -\frac{1}{9}(1 -\cos x)^2 + o((1 -\cos x)^2)
\end{aligned}
$$
利用
$$
\cos = 1-\frac{x^2}{2} + \frac{x^4}{24} +o(x^4)
$$
知
$$
\begin{aligned}
\sqrt[3]{2-\cos x} &= 1 + \frac{1}{3} (\frac{x^2}{2} - \frac{x^4}{24}) - \frac{1}{9}(\frac{x^2}{2})^2 + o(x^4) \\
&= 1 + \frac{x^2}{6} - \frac{x^4}{24} + o(x^4)
\end{aligned}
$$
![](https://pic4.zhimg.com/v2-e66e462a360826357a9d7e9b740544b3_r.jpg)

## 敛散性判断
![v2-005556dcd67a6cc6aaa9d35b52d01fce_1440w.webp (1440×3629) (zhimg.com)](https://pic3.zhimg.com/80/v2-005556dcd67a6cc6aaa9d35b52d01fce_1440w.webp)
这里主要运用了两个技巧
### 积分的收敛性$\to$积分上限函数的有界性$\to$离散数列的有界性
第一个转化利用了积分函数$f(x) > 0$，故积分上限函数是单调的
第二个转化利用了如下定理
设$f(x)$在$U^{\circ}(x_0, \delta_0)$上有界
$$
\varlimsup_{x\to x_0} f(x) = \sup\{\varlimsup_{n \to \infty} f(x_n): x_n \in U^{\circ}(x_0, \delta_0), \lim_{x\to \infty} x_n = x_0\}
$$
当$x_0$取$+\infty$时也是成立的
### Jordan 不等式
$$
\frac{2}{\pi} x \le \sin x \le x, \;x \in [0, \frac{\pi}{2}]
$$
在通过第一个技巧+周期分割 限定$x$范围后，可以利用此不等式实现$\sin x \to x$的转化




> [!tip] Idea
> 含参量积分本质上就是一种*偏积分*，一个二元函数的含参量积分就是把一个变量看作常数，然后对另一个变量积分
# 含参量正常积分
设$f(x)$为定义在[[Planar Point Set#区域|区域]]$G = \left\{ (x,y) \mid c(x) \le y \le d(x)\right\}$上的二元函数，其中$c(x),d(x)$是定义在$[a,b]$上的[[Continuous Function|连续函数]]，若对于$[a,b]$上的每一个点$x$，$f(x,y)$作为$y$的函数在$[c(x),d(x)]$上可积，则其积分值可表示为
$$
F(x) = \int_{c(x)}^{d(x)} f(x,y)\mathrm{d} y,\quad x \in [a,b]
$$
这个$F(x)$被称为在$[a,b]$上*含参量$x$的（正常）积分*

## 连续性
若二元函数在矩形区域$R = [a,b]\times[c,d]$上[[Limit of Multivariable Functions#二元函数的连续性|连续]]，则函数
$$
\phi(x) = \int_c^d f(x,y)\mathrm{d} y
$$
在$[a,b]$上连续

或者更一般地，如果二元函数在上面给出的区域$G$上连续，则有
$$
F(x) = \int_{c(x)}^{d(x)} f(x,y)\mathrm{d} y
$$
在$[a,b]$上连续

## 可微性
设$f(x,y),\;f_x(x,y)$在$R = [a,b]\times[p,q]$上连续，而$c(x),d(x)$为定义在$[a,b]$上且其值含于$[p,q]$内的可微函数，则函数
$$
F(x) = \int_{c(x)}^{d(x)} f(x,y)\mathrm{d} y
$$
在$[a,b]$上可微。特别地，我们可以给出$F(x)$的微分（因为是单元函数，所以也就是导数）
$$
\begin{aligned}
F(x) &= H(x,c,d) = \int_{c(x)}^{d(x)} f(x,y) \mathrm{d}y \\
\implies F'(x) &= \frac{ \partial H }{ \partial x }  + \frac{ \partial H }{ \partial c } \frac{ \mathrm{d} c }{ \mathrm{d} x }  + \frac{ \partial H }{ \partial d } \frac{ \mathrm{d} d }{ \mathrm{d} x }  \\
\end{aligned}
$$
其中第一项中由于$x$不是积分变量，所以可以直接求导
$$
\frac{ \partial H }{ \partial x } = \int_{c(x)}^{d(x)} f_x(x,y) \mathrm{d}y
$$
对于第二项和第三项，我们回忆变上限积分函数的导数
$$
\frac{ \mathrm{d}  }{ \mathrm{d} x }  \left( \int_{u(x)}^{v(x)} f(t) \mathrm{d}t \right)  = \frac{ \mathrm{d}  }{ \mathrm{d} x } \left( \mathcal F(v) - \mathcal F(u) \right) = \frac{ \mathrm{d} \mathcal F }{ \mathrm{d} v }  \frac{ \mathrm{d} v }{ \mathrm{d} x } -\frac{ \mathrm{d} \mathcal F }{ \mathrm{d} u } \frac{ \mathrm{d} u }{ \mathrm{d} x } = f(v)v'(x) - f(u)u'(x)
$$
其中$\mathcal F$是$f$的原函数，于是我们有
$$
\begin{aligned}
\frac{ \partial H }{ \partial c }  &= f(x,d(x))\cdot 0 - f(x,c(x))\cdot1 = -f(x,c(x)) \\
\frac{ \partial H }{ \partial d }  &= f(x,d(x))\cdot 1 - f(x,c(x))\cdot0 = f(x,d(x)) \\
\end{aligned}
$$
故有
$$
F'(x) = \int_{c(x)}^{d(x)}f_x(x,y) \mathrm{d}x -f(x,c(x))c'(x) + f(x,d(x))d'(x)
$$
## 可积性
若$f(x,y)$在矩形区域$R=[a,b]\times[c,d]$上连续，则$\varphi(x),\psi(y)$分别在$[a,b],[c,d]$上可积。也就是说，在连续性假设下，同时存在两个求积顺序不同的积分
$$
\int_a^b\left[ \int_c^df(x,y)\mathrm{d} y \right] \mathrm{d} x,\quad\int_c^d\left[ \int_a^bf(x,y)\mathrm{d} x \right]  \mathrm{d} y
$$
*这两个积分的值相同*，统一写成
$$
\int_c^d\int_a^b f(x,y) \mathrm{d} x \mathrm{d} y
$$


# 含参量反常积分
复习[[Improper Integrals|反常积分]]
若对$\forall x \in I$，反常积分
$$
\Phi(x) = \int_c^\infty f(x,y) \mathrm{d} y
$$
都收敛，我们就称$\Phi(x)$为*含参量$x$的反常积分*

若对任给的$\varepsilon >0$, 总存在一个与$x$无关的实数$N>c$使得当$M>N$时，对一切$x\in I$都有
$$
\left|{\int_c^Mf(x,y)\mathrm{d} y - \Phi(x)}\right| < \varepsilon
$$
即
$$
\left|{\int_M^\infty f(x,y) \mathrm{d} y}\right| < \varepsilon
$$
则称这个含参量反常积分在$I$上*一致收敛*于$\Phi(x)$

## 一致收敛的Cauchy准则
含参量反常积分在$I$上一致收敛的充要条件是：对任给的$\varepsilon>0$，总存在某一实数$M>c$使得当$A_1,A_2>M$时，对一切$x\in I$都有
$$
\left| \int_{A_1}^{A_2} f(x,y) \mathrm{d} y \right| <\varepsilon
$$
同样地，也有等价条件
$$
\lim_{A\to \infty} \sup_{x\in I}\left|\Phi(\infty) - \Phi(A)\right| =\lim_{A\to \infty}\sup_{x\in I}\left| \int_{A}^{\infty} f(x,y)\mathrm{d} y \right| = 0 
$$
Cauchy准则的**否定**是，存在$\varepsilon_0>0$，对任意实数$M>c$，总能找到$A_1,A_2>M$和某个数$x^*$满足
$$
\left| \int_{A_1}^{A_2} f(x^*,y) \mathrm{d} y \right| \ge \varepsilon_0 
$$
若对任意$[a,b]\subset I$，含参量反常积分在$[a,b]$上一致收敛，则称该含参量反常积分在$I$上*内闭一致收敛*。

一个不一致收敛但是内闭一致收敛的例子是在$(0,+\infty)$上的含参量反常积分
$$
\int_0^\infty \dfrac{\sin xy}{y} \mathrm{d} y
$$
这是因为在$x^*$靠近$0$的时候，有
$$
\int_{A_1}^{A_2} \dfrac{\sin x^*y}{y} \mathrm{d} y = x^*\int_{A_1}^{A_2} \dfrac{\mathrm{d} y}{y} = x^*\ln \dfrac{A_2}{A_1} 
$$
可以取到大于$0$的数
## 一致收敛的函数项级数判定
含参量反常积分在$I$上一致收敛的充要条件是，对任一趋近$+\infty$的递增数列$\left\{ A_n \right\}$（其中$A_1=c$），函数项级数
$$
\sum_{n = 1}^\infty \int_{A_n}^{A_{n+1}} f(x,y)\mathrm{d} y = \sum_{n = 1}^\infty u_n(x)
$$
在$I$上一致收敛

由此，可利用[[Function Series#函数项级数一致收敛的其他判别法|函数项级数一致收敛的判别法]]来判定含参反常积分的一致收敛性质
### 大$M$判别法
设有函数$g(y)$使得
$$
\left| f(x,y) \right| \le g(y),\; (x,y) \in I\times[c,+\infty) 
$$
则若$\displaystyle \int_c^\infty g(y)\mathrm{d} y$收敛，那么$\displaystyle \int_c^\infty f(x,y) \mathrm{d} y$在$I$上一致收敛

### Dirichlet 判别法
1. 对一切实数$N>c$，含参量正常积分$\displaystyle \int_c^Nf(x,y)\mathrm{d} y$，对参量$x$在$I$上*一致有界*，也就是说存在正数$M$使得对一切$N>c,x\in I$都有
$$
\left| \int_c^Nf(x,y) \mathrm{d} y \right|<M 
$$
2. 对于每一个$x\in I$，函数$g(x,y)$作为$y$的单调函数，且当$y\to +\infty$时，对参量$x$一致收敛于$0$

则含参量反常积分
$$
\int_c^{+\infty} f(x,y)g(x,y) \mathrm{d} y
$$
在$I$上一致收敛
### Abel 判别法
1. $\displaystyle \int_c^\infty f(x,y)\mathrm{d} y$在$I$上一致收敛
2. 对每一个$x\in I$，函数$g(x,y)$是$y$的单调函数，且对参量$x$在$I$上一致有界
则含参量反常积分
$$
\int_c^{+\infty} f(x,y)g(x,y) \mathrm{d} y
$$
在$I$上一致收敛

## 含参量反常积分的性质
### 连续性
**如果$\Phi(x)$在$I$上一致收敛**，则$f(x,y)$连续可以推出$\Phi(x)$连续

### 可微性
若
1. $f(x,y),f_x(x,y)$在区域$I\times[c,+\infty]$上连续
2. $\displaystyle \Phi(x) = \int_c^{+\infty} f(x,y)\mathrm{d} y$在$I$上收敛
3. $\displaystyle \int_c^{+\infty} f_x(x,y)\mathrm{d} y$在$I$上一致收敛
则$\Phi(x)$在$I$上可微，且
$$
\Phi'(x) = \int_c^{+\infty} f_x(x,y) \mathrm{d} y
$$
### 可积性
若
1. $f(x,y)$在$[a,b]\times[c,+\infty)$上连续
2. $\displaystyle \Phi(x) = \int_c^{+\infty} f(x,y)\mathrm{d} y$在$[a,b]$上一致收敛
则$\Phi(x)$在$[a,b]$上可积，且
$$
\int_a^b \Phi(x) = \int_c^{+\infty} \int_a^b f(x,y)\mathrm{d} x \mathrm{d} y
$$
# 例题
## 利用保持可微性来简化计算
要求$\displaystyle \lim_{ \alpha \to 0 } \int_{\alpha}^{1-\alpha} \dfrac{\mathrm{d}x}{1 + x^{2}+\alpha^{2}}$，由于被积分函数连续，所以
$$
\text{原式}  =\int_0^1 \dfrac{\mathrm{d}x}{1 + x^{2}} = \dfrac{\pi}{4}
$$
## 利用含参量积分可交换性来计算积分
求$\displaystyle I = \int_0^1 \dfrac{x^b - x^a}{\ln x} \mathrm{d}x$，我们需要观察到被积函数$\displaystyle \dfrac{x^b-x^a}{\ln x} = \int_a^b x^y \mathrm{d}y$，从而
$$
I = \int_0^1 \int_a^b x^y \mathrm{d}y \mathrm{d}x= \int_a^b \int_0^1 x^y \mathrm{d}x \mathrm{d}y = \int_a^b \dfrac{\mathrm{d}y}{y + 1} = \ln \dfrac{1 + b}{1+ a}
$$
## 引入参量来计算积分
求$\displaystyle I = \int_0^1 \dfrac{\ln(1+x)}{1+x^{2}} \mathrm{d}x$，则考虑含参量积分$\displaystyle \phi(\alpha) = \int_0^1 \dfrac{\ln (1+\alpha x)}{1+x^{2}}\mathrm{d}x$，则有
$$
\phi'(\alpha) = \int_0^1 \dfrac{x}{(1+x^{2})(1+\alpha x)} \mathrm{d}x
$$
这是一个有理函数积分，我们通过待定系数法或者直接观察可以得到
$$
\dfrac{x}{(1+x^{2})(1+\alpha x)} = \dfrac{1}{1+\alpha^{2}}\left( \dfrac{x}{1+x^{2}} + \dfrac{\alpha}{1+x^{2}} - \dfrac{\alpha}{1+\alpha x} \right) 
$$
其中
$$
\begin{gather}
\int_0^1 \dfrac{x}{1+x^{2}} \mathrm{d}x = \dfrac{1}{2} \int_0^1 \dfrac{\mathrm{d}(1+x^{2})}{1+x^{2}} = \dfrac{1}{2} \ln 2 \\
\int_0^1 \dfrac{\alpha}{1+x^{2}} \mathrm{d}x  = \alpha \left( \arctan 1 - \arctan 0 \right)  = \dfrac{\alpha \pi}{4} \\
\int_0^1 \dfrac{\alpha}{1+\alpha x} \mathrm{d}x= \ln(1 +\alpha)
\end{gather}
$$
故有
$$
\phi'(x) = \dfrac{1}{1+\alpha^{2}} \left[ \dfrac{1}{2}\ln 2 + \dfrac{\alpha \pi}{4}  - \ln(1+\alpha)\right] 
$$
其中第三项的积分正是我们需要的，所以计算
$$
\int_0^1 \phi'(\alpha) \mathrm{d}\alpha = \dfrac{\pi}{8}\ln 2 + \dfrac{\pi}{8}\ln 2 - \phi(1)
$$
且$\displaystyle \int_0^1 \phi'(\alpha) \mathrm{d}\alpha = \phi(1) - \phi(0)  =\phi(1)$，故有$I = \phi(1) = \dfrac{\pi}{8} \ln 2$

这里的主要思想是引入参数$\to$微分$\to$积分$\to$再积分：
1. 因为$\ln(\cdot)$这样的函数积分教我困难，所以我们希望在其变量中**引入参量**，方面我们之后微分后把它转化为有理函数积分
2. 在给被积函数引入参量后，我们对其**求导(微分)**，把它变成形式更简单的有理函数；虽然实质上如果整个有理函数再积回去和原先的函数的积分难度是相当的，但我们利用有理函数的性质我们可以方便地把原函数中容易积分的部分拆分出来，使原函数的积分问题得到简化
3. 之后对这些拆出来的部分分别积分，简单的部分可以直接求出，困难的部分可以化成和原函数有关的形式
4. 最后我们对这些参量再次积分，结合参量的边界条件，就可以给出最后的答案

这种方法被称为*Feynman积分法*
另一个经典的题目是求$\displaystyle I = \int_0^{\pi/2} \ln (a^{2}\cos ^{2}x + b^{2} \sin ^{2}x) \mathrm{d}x$，这里面已经有两个参量，我们把其中的$\alpha$当作参量，然后求导有
$$
\begin{aligned}
I'(a) &= \int_0^{\pi/2} \dfrac{2a\cos ^{2}x}{a^{2}\cos ^{2}x + b^{2}\sin ^{2}x} \mathrm{d}x \\
&= 2a \int_0^{\pi/2} \dfrac{\mathrm{d}(\tan x)}{(a^{2} + b^{2}\tan ^{2} x)(1 + \tan ^{2} x)} \\
\end{aligned}
$$
这又是一个关于$\tan x$的有理函数积分，其积分结果为$I'(a) = \dfrac{\pi}{a+b}$，我们再次积分
$$
I(a) - I(C) = \int_C^a \dfrac{\pi \mathrm{d}a}{a+ b} = \pi \ln \dfrac{a+b}{C+b}
$$
这里我们发现$C= b$时原积分$\displaystyle I(b) = \int_0^{\pi/2} \ln(b^{2}) \mathrm{d}x = \pi \ln b$，此时就有
$$
I = \pi \ln \dfrac{a+b}{b + b} + \pi \ln b = \pi \ln \dfrac{a+b}{2}
$$
## 含参量反常积分的计算
要求$J=\displaystyle \int_0^{+\infty} \exp(-px)\dfrac{\sin bx - \sin ax}{x}\mathrm{d}x \quad(p>0,b>a)$，首先注意到
$$
\dfrac{{\sin bx - \sin ax}}{x} = \int_a^b \cos xy \mathrm{d}y
$$
故$\displaystyle J = \int_0^{+\infty} \exp(-px) \left( \int_a^ b \cos xy \mathrm{d}y \right) \mathrm{d}x = \int_0^{+\infty} \mathrm{d}x \int_a^b \exp(-px)\cos xy \mathrm{d}y$，这里我们希望调换积分顺序，首先需要证明该反常积分一致收敛，注意到$\left|\exp(-px)\cos xy\right| \leq \exp (-px)$且反常积分$\displaystyle \int_0^{+\infty} \exp(-px) \mathrm{d}x$是收敛的，故由大M判别法整个反常积分收敛，于是$\displaystyle J = \int_a^b \mathrm{d}y \int_0^{+\infty}\exp(-px)\cos xy \mathrm{d}x = \arctan \dfrac{b}{p}-\arctan \dfrac{a}{p}$

要计算$\displaystyle \int_0^{+\infty} \dfrac{\sin ax}{x} \mathrm{d}x$，也可以引入参量$b=0$使得
$$
\int_0^{+\infty} \dfrac{ \sin ax}{x} \mathrm{d}x = \int_0^{+\infty} \dfrac{\sin ax - \sin bx}{x} \mathrm{d}x =\int_0^{+\infty} \left( \int_b^a \cos xy \mathrm{d}y \right)  \mathrm{d}x
$$
我们发现这里$\displaystyle \int_0^{+\infty} \cos xy \mathrm{d}y$不收敛，没法积分换序，所以必须得参照上一问的方式引入函数$\exp(-px)$，在上题中令$b = 0$，则有
$$
\int_0^{+\infty} \exp(-px) \dfrac{\sin ax}{x} \mathrm{d}x = \arctan \dfrac{a}{p} \quad (p>0)
$$
其中$\displaystyle \int_0^{+\infty} \exp(-px) \sin ax \mathrm{d}x \leq \int_0^{+\infty} \exp(-px) \mathrm{d}x$一致收敛且$\dfrac{1}{x}$单调趋于$0$，所以整个积分一致收敛，含参反常积分具有连续性，且
$$
\begin{aligned}
\int_0^{+\infty} \dfrac{\sin ax}{x} \mathrm{d}x &= \int_0^{+\infty} \left( \lim_{ p \to 0 } \exp(-px) \dfrac{ \sin ax}{x}  \right)  \mathrm{d}x= \lim_{ p \to 0 }  \left( \int_0^{+\infty} \exp(-px) \dfrac{ \sin ax}{x}\mathrm{d}x \right) \\
&= \lim_{ p \to 0 } \left( \arctan \dfrac{a}{p} \right) \quad(p>0) = \dfrac{\pi}{2}\mathrm{sgn}(a)
\end{aligned} 
$$

计算$\displaystyle \phi(r) = \int_0^{+\infty} \exp(-x^{2})\cos(rx) \mathrm{d}x$，由于$\exp(-x^{2})\cos (rx) \leq \exp(-x^{2})$且$\displaystyle \int_0^{+\infty} \exp(-x^{2})\mathrm{d}x = \dfrac{\sqrt{ \pi }}{2}$一致收敛，故可以采用Feynman判别法，对参量求导
$$
\phi'(r) = \int_0^{+\infty} -x\exp(-x^{2}) \sin (rx) \mathrm{d}x
$$
由于
$$
\begin{matrix}
\sin(rx) &\to& r\cos(rx) \\
-x\exp(-x^{2}) &\to& \dfrac{1}{2}\exp(-x^{2})
\end{matrix}
$$
故可以展开为分部积分
$$
\begin{aligned}
\phi'(r) &= 1\cdot\dfrac{1}{2}\sin(rx)\exp(-x^{2}) {\bigg|}_0^{+\infty} + (-1)\cdot\int_0^{+\infty} \dfrac{r}{2}\cos(rx) \exp(-x^{2}) \mathrm{d}x \\
&= -\dfrac{r}{2}\phi(r)
\end{aligned}
$$
于是$\displaystyle \dfrac{\mathrm{d}\phi}{\phi} = -\dfrac{r}{2} \mathrm{d}r \implies \phi(r) = C\exp(-\dfrac{r^{2}}{4})$，又注意到$\displaystyle C=\phi(0) =\int_0^{+\infty} \exp(-x^{2}) \mathrm{d}x = \dfrac{\sqrt{ \pi }}{2}$，于是$\displaystyle \phi(r) = \dfrac{\sqrt{ \pi }}{2} \exp(-\dfrac{r^{2}}{4})$

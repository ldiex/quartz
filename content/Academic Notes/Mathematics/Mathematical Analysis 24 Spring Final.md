# 含参量积分
## 含参量正常积分
含参量积分本质上就是一种*偏积分*, 一个二元函数的含参量积分就是把一个变量看作常数, 然后对另一个变量积分

设$f(x)$为定义在[[Planar Point Set#区域|区域]]$G = \left\{ (x,y) \mid c(x) \le y \le d(x)\right\}$上的二元函数, 其中$c(x),d(x)$是定义在$[a,b]$上的[[Continuous Function|连续函数]], 若对于$[a,b]$上的每一个点$x$, $f(x,y)$作为$y$的函数在$[c(x),d(x)]$上可积, 则其积分值可表示为
$$
F(x) = \int_{c(x)}^{d(x)} f(x,y)\mathrm{d} y,\quad x \in [a,b]
$$
这个$F(x)$被称为在$[a,b]$上*含参量$x$的（正常）积分*

含参量积分**保持连续性**, 也就是说如果上面的被积分函数$f(x,y)$连续, 那么其*偏积分*$F(x)$也是连续的

含参量积分**保持可微性**, 也就是说如果上面的被积分函数$f(x,y)$可微, 那么其*偏积分*$F(x)$也是可微的, 特别地, 我们可以给出$F(x)$的微分（因为是单元函数, 所以也就是导数）
$$
\begin{aligned}
F(x) &= H(x,c,d) = \int_{c(x)}^{d(x)} f(x,y) \mathrm{d}y \\
\implies F'(x) &= \frac{ \partial H }{ \partial x }  + \frac{ \partial H }{ \partial c } \frac{ \mathrm{d} c }{ \mathrm{d} x }  + \frac{ \partial H }{ \partial d } \frac{ \mathrm{d} d }{ \mathrm{d} x }  \\
\end{aligned}
$$
其中第一项中由于$x$不是积分变量, 所以可以直接求导
$$
\frac{ \partial H }{ \partial x } = \int_{c(x)}^{d(x)} f_x(x,y) \mathrm{d}y
$$
对于第二项和第三项, 我们回忆变上限积分函数的导数
$$
\frac{ \mathrm{d}  }{ \mathrm{d} x }  \left( \int_{u(x)}^{v(x)} f(t) \mathrm{d}t \right)  = \frac{ \mathrm{d}  }{ \mathrm{d} x } \left( \mathcal F(v) - \mathcal F(u) \right) = \frac{ \mathrm{d} \mathcal F }{ \mathrm{d} v }  \frac{ \mathrm{d} v }{ \mathrm{d} x } -\frac{ \mathrm{d} \mathcal F }{ \mathrm{d} u } \frac{ \mathrm{d} u }{ \mathrm{d} x } = f(v)v'(x) - f(u)u'(x)
$$
其中$\mathcal F$是$f$的原函数, 于是我们有
$$
\begin{aligned}
\frac{ \partial H }{ \partial c }  &= f(x,d(x))\cdot 0 - f(x,c(x))\cdot1 = -f(x,c(x)) \\
\frac{ \partial H }{ \partial d }  &= f(x,d(x))\cdot 1 - f(x,c(x))\cdot0 = f(x,d(x)) \\
\end{aligned}
$$
故有
$$
F'(x) = \int_{c(x)}^{d(x)}f_x(x,y) \mathrm{d}y -f(x,c(x))c'(x) + f(x,d(x))d'(x)
$$

含参量积分也**保持可积性**, 且对于连续函数有
$$
\int_a^b\left[ \int_c^df(x,y)\mathrm{d} y \right] \mathrm{d} x=\int_c^d\left[ \int_a^bf(x,y)\mathrm{d} x \right]  \mathrm{d} y
$$
所以我们可以将其统一写成
$$
\int_c^d\int_a^b f(x,y) \mathrm{d} x \mathrm{d} y
$$
这是计算二重积分的基础
## 利用保持可微性来简化计算
要求$\displaystyle \lim_{ \alpha \to 0 } \int_{\alpha}^{1-\alpha} \dfrac{\mathrm{d}x}{1 + x^{2}+\alpha^{2}}$, 由于被积分函数连续, 所以
$$
\text{原式}  =\int_0^1 \dfrac{\mathrm{d}x}{1 + x^{2}} = \dfrac{\pi}{4}
$$
## 利用含参量积分可交换性来计算积分
求$\displaystyle I = \int_0^1 \dfrac{x^b - x^a}{\ln x} \mathrm{d}x$, 我们需要观察到被积函数$\displaystyle \dfrac{x^b-x^a}{\ln x} = \int_a^b x^y \mathrm{d}y$, 从而
$$
I = \int_0^1 \int_a^b x^y \mathrm{d}y \mathrm{d}x= \int_a^b \int_0^1 x^y \mathrm{d}x \mathrm{d}y = \int_a^b \dfrac{\mathrm{d}y}{y + 1} = \ln \dfrac{1 + b}{1+ a}
$$
## 引入参量来计算积分
求$\displaystyle I = \int_0^1 \dfrac{\ln(1+x)}{1+x^{2}} \mathrm{d}x$, 则考虑含参量积分$\displaystyle \phi(\alpha) = \int_0^1 \dfrac{\ln (1+\alpha x)}{1+x^{2}}\mathrm{d}x$, 则有
$$
\phi'(\alpha) = \int_0^1 \dfrac{x}{(1+x^{2})(1+\alpha x)} \mathrm{d}x
$$
这是一个有理函数积分, 我们通过待定系数法或者直接观察可以得到
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
其中第三项的积分正是我们需要的, 所以计算
$$
\int_0^1 \phi'(\alpha) \mathrm{d}\alpha = \dfrac{\pi}{8}\ln 2 + \dfrac{\pi}{8}\ln 2 - \phi(1)
$$
且$\displaystyle \int_0^1 \phi'(\alpha) \mathrm{d}\alpha = \phi(1) - \phi(0)  =\phi(1)$, 故有$I = \phi(1) = \dfrac{\pi}{8} \ln 2$

这里的主要思想是引入参数$\to$微分$\to$积分$\to$再积分: 
1. 因为$\ln(\cdot)$这样的函数积分教我困难, 所以我们希望在其变量中**引入参量**, 方面我们之后微分后把它转化为有理函数积分
2. 在给被积函数引入参量后, 我们对其**求导(微分)**, 把它变成形式更简单的有理函数；虽然实质上如果整个有理函数再积回去和原先的函数的积分难度是相当的, 但我们利用有理函数的性质我们可以方便地把原函数中容易积分的部分拆分出来, 使原函数的积分问题得到简化
3. 之后对这些拆出来的部分分别积分, 简单的部分可以直接求出, 困难的部分可以化成和原函数有关的形式
4. 最后我们对这些参量再次积分, 结合参量的边界条件, 就可以给出最后的答案

这种方法被称为*Feynman积分法*
另一个经典的题目是求$\displaystyle I = \int_0^{\pi/2} \ln (a^{2}\cos ^{2}x + b^{2} \sin ^{2}x) \mathrm{d}x$, 这里面已经有两个参量, 我们把其中的$\alpha$当作参量, 然后求导有
$$
\begin{aligned}
I'(a) &= \int_0^{\pi/2} \dfrac{2a\cos ^{2}x}{a^{2}\cos ^{2}x + b^{2}\sin ^{2}x} \mathrm{d}x \\
&= 2a \int_0^{\pi/2} \dfrac{\mathrm{d}(\tan x)}{(a^{2} + b^{2}\tan ^{2} x)(1 + \tan ^{2} x)} \\
\end{aligned}
$$
这又是一个关于$\tan x$的有理函数积分, 其积分结果为$I'(a) = \dfrac{\pi}{a+b}$, 我们再次积分
$$
I(a) - I(C) = \int_C^a \dfrac{\pi \mathrm{d}a}{a+ b} = \pi \ln \dfrac{a+b}{C+b}
$$
这里我们发现$C= b$时原积分$\displaystyle I(b) = \int_0^{\pi/2} \ln(b^{2}) \mathrm{d}x = \pi \ln b$, 此时就有
$$
I = \pi \ln \dfrac{a+b}{b + b} + \pi \ln b = \pi \ln \dfrac{a+b}{2}
$$
## 含参量反常积分
若对$\forall x \in I$, 反常积分
$$
\Phi(x) = \int_c^\infty f(x,y) \mathrm{d} y
$$
都收敛, 我们就称$\Phi(x)$为*含参量$x$的反常积分*

若对任给的$\varepsilon >0$, 总存在一个与$x$无关的实数$N>c$使得当$M>N$时, 对一切$x\in I$都有
$$
\left|{\int_c^Mf(x,y)\mathrm{d} y - \Phi(x)}\right| < \varepsilon
$$
即
$$
\left|{\int_M^\infty f(x,y) \mathrm{d} y}\right| < \varepsilon
$$
则称这个含参量反常积分在$I$上*一致收敛*于$\Phi(x)$

这就是把参量类比为函数项级数的自变量$x$, 积分上限类比为函数项级数的项数$n$, 其实就是把离散求和转化成了积分

由此, 我们也可以给出一致收敛的Cauchy准则
对任给的$\varepsilon>0$, 总存在某一实数$M>c$使得当$A_1,A_2>M$时, 对一切$x\in I$都有
$$
\left| \int_{A_1}^{A_2} f(x,y) \mathrm{d} y \right| <\varepsilon
$$
同样地, 也有等价条件
$$
\lim_{A\to \infty} \sup_{x\in I}\left|\Phi(\infty) - \Phi(A)\right| =\lim_{A\to \infty}\sup_{x\in I}\left| \int_{A}^{\infty} f(x,y)\mathrm{d} y \right| = 0 
$$
Cauchy准则的**否定**是, 存在$\varepsilon_0>0$, 对任意实数$M>c$, 总能找到$A_1,A_2>M$和某个数$x^*$满足
$$
\left| \int_{A_1}^{A_2} f(x^*,y) \mathrm{d} y \right| \ge \varepsilon_0 
$$
若对任意$[a,b]\subset I$, 含参量反常积分在$[a,b]$上一致收敛, 则称该含参量反常积分在$I$上*内闭一致收敛*. 

一个不一致收敛但是内闭一致收敛的例子是在$(0,+\infty)$上的含参量反常积分
$$
\int_0^\infty \dfrac{\sin xy}{y} \mathrm{d} y
$$
这是因为在$x^*$靠近$0$的时候, 有
$$
\int_{A_1}^{A_2} \dfrac{\sin x^*y}{y} \mathrm{d} y = x^*\int_{A_1}^{A_2} \dfrac{\mathrm{d} y}{y} = x^*\ln \dfrac{A_2}{A_1} 
$$
可以取到大于$0$的数

### 大$M$判别法
设有函数$g(y)$使得
$$
\left| f(x,y) \right| \le g(y),\; (x,y) \in I\times[c,+\infty) 
$$
则若$\displaystyle \int_c^\infty g(y)\mathrm{d} y$收敛, 那么$\displaystyle \int_c^\infty f(x,y) \mathrm{d} y$在$I$上一致收敛

### Dirichlet 判别法
1. 对一切实数$N>c$, 含参量正常积分$\displaystyle \int_c^Nf(x,y)\mathrm{d} y$, 对参量$x$在$I$上*一致有界*, 也就是说存在正数$M$使得对一切$N>c,x\in I$都有
$$
\left| \int_c^Nf(x,y) \mathrm{d} y \right|<M 
$$
2. 对于每一个$x\in I$, 函数$g(x,y)$作为$y$的单调函数, 且当$y\to +\infty$时, 对参量$x$一致收敛于$0$

则含参量反常积分
$$
\int_c^{+\infty} f(x,y)g(x,y) \mathrm{d} y
$$
在$I$上一致收敛
### Abel 判别法
1. $\displaystyle \int_c^\infty f(x,y)\mathrm{d} y$在$I$上一致收敛
2. 对每一个$x\in I$, 函数$g(x,y)$是$y$的单调函数, 且对参量$x$在$I$上一致有界
则含参量反常积分
$$
\int_c^{+\infty} f(x,y)g(x,y) \mathrm{d} y
$$
在$I$上一致收敛

总结
- 大M: 通过放缩把参量$x$干掉
- Abel: 一致收敛+单调一致有界
- Dirichlet: 一致有界 + 单调且在非参量趋于正无穷时一致收敛至$0$
## 含参量反常积分的判定实例
积分$\displaystyle \int_0^{+\infty} \dfrac{\cos xy}{1+x^{2}}\mathrm{d}x$在$\mathbb{R}$上一致收敛, 这是因为
$$
\int_0^{+\infty} \dfrac{\cos xy}{1+x^{2}} \mathrm{d}x \leq \int_0^{+\infty} \dfrac{\mathrm{d}x}{1 + x^{2}} = \dfrac{\pi}{2}
$$

积分$\displaystyle \int_0^{+\infty} \exp(-xy) \dfrac{\sin x}{x} \mathrm{d}x$在$[0, + \infty)$上一致收敛, 这是因为反常积分$\displaystyle \int_0^{+\infty} \dfrac{\sin x}{x} \mathrm{d}x$一致收敛（由Dirichlet判别法, $\sin x$是有界的且$\dfrac{1}{x}$单调趋于$0$）, 且$\exp(-xy)$在$y \t\oplus \infty$对$\forall x\in [0,+\infty)$单调收敛至$0$, 故根据Abel判别法得证

注意这里不能通过$\displaystyle \int_0^{+\infty} \exp(-xy) \sin x \mathrm{d}x\leq \int_0^{+\infty} \exp(-xy) \mathrm{d}x$一致有界且$\dfrac{1}{x}$单调趋于$0$来证明, 这是因为当$y = 0$时$\displaystyle \int_0^{+\infty} \exp(-xy) \mathrm{d}x$是无界的

积分$\displaystyle \int_1^{+\infty} \dfrac{y \sin xy}{1+y^{2}} \mathrm{d}y$在$\mathbb{R}^+$上**内闭**一致收敛, 这是因为考虑任意区间$[a,b] \subset (0,+\infty)$, 对$\forall x\in[a,b]$, 有
$$
\left|\int_a^b \sin xy \mathrm{d}y \right| = \left| -\dfrac{\cos xy}{x}\right| {\bigg|}_{a}^b \leq \dfrac{2}{a}
$$
故$\displaystyle \int_1^{+\infty} \sin xy \mathrm{d}y$一致有界. 而$\displaystyle \dfrac{y}{1+y^{2}}$在$y \to +\infty$时单调趋于$0$, 故得证

同样的, 如果$x$能取到$0$, 这个含参量反常积分就不能一致收敛
## 含参量反常积分的计算
要求$J=\displaystyle \int_0^{+\infty} \exp(-px)\dfrac{\sin bx - \sin ax}{x}\mathrm{d}x \quad(p>0,b>a)$, 首先注意到
$$
\dfrac{{\sin bx - \sin ax}}{x} = \int_a^b \cos xy \mathrm{d}y
$$
故$\displaystyle J = \int_0^{+\infty} \exp(-px) \left( \int_a^ b \cos xy \mathrm{d}y \right) \mathrm{d}x = \int_0^{+\infty} \mathrm{d}x \int_a^b \exp(-px)\cos xy \mathrm{d}y$, 这里我们希望调换积分顺序, 首先需要证明该反常积分一致收敛, 注意到$\left|\exp(-px)\cos xy\right| \leq \exp (-px)$且反常积分$\displaystyle \int_0^{+\infty} \exp(-px) \mathrm{d}x$是收敛的, 故由大M判别法整个反常积分收敛, 于是$\displaystyle J = \int_a^b \mathrm{d}y \int_0^{+\infty}\exp(-px)\cos xy \mathrm{d}x = \arctan \dfrac{b}{p}-\arctan \dfrac{a}{p}$

要计算$\displaystyle \int_0^{+\infty} \dfrac{\sin ax}{x} \mathrm{d}x$, 也可以引入参量$b=0$使得
$$
\int_0^{+\infty} \dfrac{ \sin ax}{x} \mathrm{d}x = \int_0^{+\infty} \dfrac{\sin ax - \sin bx}{x} \mathrm{d}x =\int_0^{+\infty} \left( \int_b^a \cos xy \mathrm{d}y \right)  \mathrm{d}x
$$
我们发现这里$\displaystyle \int_0^{+\infty} \cos xy \mathrm{d}y$不收敛, 没法积分换序, 所以必须得参照上一问的方式引入函数$\exp(-px)$, 在上题中令$b = 0$, 则有
$$
\int_0^{+\infty} \exp(-px) \dfrac{\sin ax}{x} \mathrm{d}x = \arctan \dfrac{a}{p} \quad (p>0)
$$
其中$\displaystyle \int_0^{+\infty} \exp(-px) \sin ax \mathrm{d}x \leq \int_0^{+\infty} \exp(-px) \mathrm{d}x$一致收敛且$\dfrac{1}{x}$单调趋于$0$, 所以整个积分一致收敛, 含参反常积分具有连续性, 且
$$
\begin{aligned}
\int_0^{+\infty} \dfrac{\sin ax}{x} \mathrm{d}x &= \int_0^{+\infty} \left( \lim_{ p \to 0 } \exp(-px) \dfrac{ \sin ax}{x}  \right)  \mathrm{d}x= \lim_{ p \to 0 }  \left( \int_0^{+\infty} \exp(-px) \dfrac{ \sin ax}{x}\mathrm{d}x \right) \\
&= \lim_{ p \to 0 } \left( \arctan \dfrac{a}{p} \right) \quad(p>0) = \dfrac{\pi}{2}\mathrm{sgn}(a)
\end{aligned} 
$$

计算$\displaystyle \phi(r) = \int_0^{+\infty} \exp(-x^{2})\cos(rx) \mathrm{d}x$, 由于$\exp(-x^{2})\cos (rx) \leq \exp(-x^{2})$且$\displaystyle \int_0^{+\infty} \exp(-x^{2})\mathrm{d}x = \dfrac{\sqrt{ \pi }}{2}$一致收敛, 故可以采用Feynman判别法, 对参量求导
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
于是$\displaystyle \dfrac{\mathrm{d}\phi}{\phi} = -\dfrac{r}{2} \mathrm{d}r \implies \phi(r) = C\exp(-\dfrac{r^{2}}{4})$, 又注意到$\displaystyle C=\phi(0) =\int_0^{+\infty} \exp(-x^{2}) \mathrm{d}x = \dfrac{\sqrt{ \pi }}{2}$, 于是$\displaystyle \phi(r) = \dfrac{\sqrt{ \pi }}{2} \exp(-\dfrac{r^{2}}{4})$

## 欧拉积分
定义$\Gamma$函数
$$
\Gamma(s) = \int_0^{+\infty} x^{s-1}e^{-x}\mathrm{d} x
$$
$\Gamma(s)$在$\mathbb{R}^+$上收敛, 规定其定义域为$s>0$

1. $\Gamma(s)$在$(0,+\infty)$上连续可导
$$
\begin{aligned}
\Gamma'(s)  & = \int_0^{+\infty} x^{s-1}e^{-x}\ln x \mathrm{d} x \\
\Gamma^{(n)}(s)   & =\int_0^{+\infty} x^{s-1} (\ln x)^n\mathrm{d} x \\
\end{aligned}
$$
2. 满足递推公式
$$
\Gamma(s+1) = s\Gamma(s)
$$
特别地, 当$s = n \in \mathbb{N}^*$时, 有$\Gamma(n + 1) = n!$

定义$B$函数
$$
B(p,q) = \int_0^1x^{p-1}(1-x)^{q-1}\mathrm{d} x
$$
同样由函数的收敛性, 规定定义域为$p,q>0$

常见的其他形式
令$x = \cos^2 \phi$, 就有
$$
B(p,q) = 2\int_0^{\pi/2} \sin^{2q-1}\phi \cos^{2p-1}\phi\mathrm{d} \phi
$$
令$x = \dfrac{y}{1+y}$, 就有
$$
B(p,q) = \int_0^{+\infty} \dfrac{y^{p-1}}{(1+y)^{p+q}} \mathrm{d} y
$$
利用两个函数之间的关系
$$
B(p,q) = \dfrac{\Gamma(p)\Gamma(q)}{\Gamma(p+q)}
$$
容易得到
1. $B(p,q)$在$\mathbb{R}^+ \times \mathbb{R}^+$上连续
2. 对称性$B(p,q) = B(q,p)$
3. 递推公式
$$
\begin{aligned}
B(p,q)  & = \dfrac{q-1}{p+q-1}B(p,q-1) \\
B(p,q)  & =\dfrac{p-1}{p+q-1}B(p-1,q) \\
\implies   B(p,q) &=\dfrac{(p-1)(q-1)}{(p+q-1)(p+q-2)}
\end{aligned}
$$
计算$\Gamma(1/2)$, 考虑
$$
B(a,1-a) = \dfrac{\Gamma(a)\Gamma(1-a)}{\Gamma(1)} = \Gamma(a)\Gamma(1-a)
$$
即
$$
\int_0^{+\infty} \dfrac{y^{a-1}}{1+y} \mathrm{d} y = \Gamma(a)\Gamma(1-a)
$$
取$a =\dfrac{1}{2}$就有
$$
\Gamma(\dfrac{1}{2}) = \sqrt{ \int_0^{+\infty} \dfrac{x^{-1/2}}{1+x}\mathrm{d} x } = \sqrt{ \int_0^{+\infty} \dfrac{2\mathrm{d} t}{(1+t^2)} } = \sqrt{ \pi }
$$
又因为
$$
\Gamma(s) = \int_0^{+\infty} x^{s-1}e^{-x}\mathrm{d} x = 2\int_0^{+\infty} t^{2s-1}e^{-t^2} \mathrm{d} t
$$
取$s = \dfrac{1}{2}$就有
$$
\boxed{\int_0^{+\infty} e^{-x^2}\mathrm{d} x = \dfrac{\sqrt{ \pi }}{2}}
$$

计算Wallis积分, 回忆[[Mathematical Analysis 23 Fall Final#Wallis 积分|Wallis积分]]
$$
\int_0^{\pi/2} \sin^n x \mathrm{d} x= \begin{cases}
\dfrac{(n - 1)!!}{n!!} \cdot \dfrac{\pi}{2} &, \text{$n$为偶数} \\
\dfrac{(n - 1)!!}{n!!} &, \text{$n$为奇数}
\end{cases}
$$
考虑
$$
\begin{aligned}
\int_0^{\pi/2} \sin^{2n+1}x\mathrm{d} x  & = \int_0^{\pi/2} \sin^{2(n+1)-1}\phi\cos^{2(1/2)-1}\phi\mathrm{d} \phi \\
 & =\dfrac{1}{2 }B(n+1, \dfrac{1}{2}) = \dfrac{1}{2}\dfrac{\Gamma(n+1)\Gamma(\dfrac{1}{2})}{\Gamma(n+\dfrac{3}{2})} \\
 & = \dfrac{1}{2} \dfrac{n!\sqrt{ \pi }}{(n+\dfrac{1}{2})\Gamma(n+\dfrac{1}{2})} \\
 & = \dfrac{1}{2} \dfrac{n!\sqrt{ \pi }}{(n+\dfrac{1}{2})(n-\dfrac{1}{2})(n-\dfrac{3}{2})\cdots(\dfrac{1}{2})\sqrt{ \pi }} \\
 & =\dfrac{1}{2}\dfrac{n!\cdot 2^{n+1}}{(2n+1)!!} = \dfrac{(2n)!!}{(2n+1)!!}
\end{aligned}
$$
得到奇数的情况, 同理也可以计算出偶数的情况
# 曲线积分
## 第一型曲线积分
标量值函数$f(x,y)$在曲线$\ell$上的路径积分
$$
\int_\ell f(x,y) \mathrm{d} s
$$
设光滑曲线$\ell$的参数方程为
$$
\ell:\begin{cases}
x = \phi(t) \\
y = \psi(t)
\end{cases}
\quad t\in [\alpha,\beta]
$$
且$f(x,y)$为定义在$\ell$上连续函数, 则有
$$
\int_\ell f(x,y)\mathrm{d} s = \int_\alpha^\beta f(\phi(t),\psi(t))  \sqrt{ \phi'^2(t) + \psi'^2(t) } \mathrm{d} t
$$
当曲线$\ell$可以用$y = \psi(x),\quad x\in[a,b]$来表示且$\psi(t)$存在连续的导函数时, 上式简化为
$$
\int_\ell f(x,y)\mathrm{d} s = \int_a^b f(x,\psi(x)) \sqrt{ 1+\psi'^2(x) } \mathrm{d} x
$$
## 第二型曲线积分
即定义在有向曲线上的向量的积分
$$
\int_{\ell} \boldsymbol F \cdot \mathrm{d} {\boldsymbol s} = \int_{\ell} F_x(x,y)\mathrm{d} x + F_y(x,y)\mathrm{d} y
$$
可以通过点乘的定义来转化成第一型曲线积分

设光滑曲线$\ell$的参数方程为
$$
\ell:\begin{cases}
x = \phi(t) \\
y = \psi(t)
\end{cases}
\quad t\in [\alpha,\beta]
$$
且$\boldsymbol F(x,y)$为定义在$\ell$上的连续向量函数, 则有
$$
\int_\ell \boldsymbol F(x,y)\mathrm{d} {\boldsymbol s} = \int_\alpha^\beta F_x(\phi(t),\psi(t)) \phi'(t)\mathrm{d} t + F_y(\phi(t),\psi(t)) \psi'(t)\mathrm{d} t
$$

## 利用对称性简化计算
计算$\displaystyle \int_\ell x^{2} \mathrm{d}s$, 其中$\ell$为球面$x^{2}+y^{2}+z^{2}=a^{2}$被平面$x+y+z=0$所截得的圆周, 由对称性我们可知$\displaystyle \int_\ell x^{2} \mathrm{d}s = \int_\ell y^{2} \mathrm{d}s = \int_\ell z^{2} \mathrm{d}s$, 且
$$
\int_\ell (x^{2}+y^{2}+z^{2})\mathrm{d}s = \int_\ell a^{2}\mathrm{d}s = a^{2}\cdot2\pi a = 2\pi a^3
$$
故$\displaystyle \int_\ell x^{2} \mathrm{d}s = \dfrac{2}{3}\pi a^3$

## 利用Stokes定理
计算$I = \displaystyle \oint_\ell y \mathrm{d}x+ z \mathrm{d}y + x \mathrm{d}z$, 其中$\ell$为$x^{2}+y^{2}+z^{2}=1$和$x+y+z = 1$的交线, 设$\boldsymbol u = (y,z,x)$, 则
$$
\nabla \times \boldsymbol u = \begin{vmatrix}
\boldsymbol{\hat{x}} & \boldsymbol{\hat{y}} & \boldsymbol{\hat{z}} \\
\partial_x & \partial_y & \partial_z \\
y & z & x
\end{vmatrix} = -\boldsymbol {\hat{x}} - \boldsymbol{\hat{y}}-\boldsymbol{\hat{z}}
$$
由Stokes定理, 有
$$
\iint_S (\nabla  \times \boldsymbol u)\cdot \mathrm{d}\boldsymbol S = \oint_\ell \boldsymbol u\cdot \mathrm{d}\boldsymbol s
$$
其中$\mathrm{d} \boldsymbol S = \dfrac{(1,1,1)}{\sqrt{ 3 }} \mathrm{d}S$, 故$\displaystyle I = \iint_S -\sqrt{ 3 }\mathrm{d}S = -\sqrt{ 3 } \pi \left( \sqrt{ \dfrac{2}{3} } \right)^{2} =-\dfrac{2\sqrt{ 3 }}{3}\pi$
# 重积分
## 二重积分
### 中值定理
若$f(x,y)$在有界闭区域$D$上**连续**, 则存在$(\xi,\eta)\in D$使得
$$
\iint_D f(x,y) \mathrm{d} \sigma = f(\xi,\eta) S_D
$$
这里$S_D$是区域$D$的面积

### 计算例题
计算二重积分$\displaystyle \iint_D \mathrm{d}\sigma$, 其中$D$为由直线$y = 2x, \  x = 2y, \ x+y=3$围成的三角形区域
可以解得三角形的三个顶点坐标为$(0,0),\ (2,1),\ (1,2)$, 则可以直接计算得到面积$S = \dfrac{1}{2}\left|(2,1) \times (1,2)\right| =\dfrac{3}{2}$

## Green公式
若函数$P(x,y),\;Q(x,y)$在闭区域$D$上连续, 且有连续的一阶偏导数, 则有
$$
\iint_D\left( \frac{ \partial Q }{ \partial x } -\frac{ \partial P }{ \partial y }  \right) \mathrm{d}\sigma = \oint_LP \mathrm{d}x + Q \mathrm{d}y
$$
设$\boldsymbol f(x,y)= P(x,y) \boldsymbol {\hat x} + Q(x,y) \boldsymbol{\hat y}$, $\mathrm{d} \boldsymbol s = \boldsymbol{\hat x} \mathrm{d}x + \boldsymbol{\hat y} \mathrm{d}y$, $\nabla = \frac{ \partial}{ \partial x }\boldsymbol{\hat x} + \frac{ \partial  }{ \partial y }\boldsymbol{\hat y}$,则有
$$
\iint_D (\nabla \times \boldsymbol f) \mathrm{d}\sigma = \oint_L \boldsymbol f \cdot \mathrm{d}\boldsymbol {s}
$$
称此为*Green公式*

### 四个等价条件
设$D$是单连通闭区域, 若函数$P(x,y),Q(x,y)$在$D$内连续, 且具有一阶连续偏导数, 则以下四个条件等价
1. 沿$D$内任一按段光滑封闭曲线$L$, 有
$$
\oint_L P \mathrm{d}x+ Q \mathrm{d}y = 0
$$
2. 对$D$中任一按段光滑曲线$L$, 曲线积分
$$
\int_L P \mathrm{d}x+ Q \mathrm{d}y
$$
与路线无关, 只与$L$的起点和终点有关
3. $P\mathrm{d}x+ Q \mathrm{d}y$是$D$内某一函数$u(x,y)$的[[Differential of Multivariable Functions#全微分|全微分]], 即在$D$内有
$$
\mathrm{d}u = P \mathrm{d}x+Q \mathrm{d}y
$$
4. 在$D$内处处成立
$$
\frac{ \partial P }{ \partial y } = \frac{ \partial Q }{ \partial x } 
$$
总结一下, 就是
$$
\boxed{\text{环路积分为0} \iff \text{积分和路径无关} \iff \text{每一点的旋度为0} \iff \boldsymbol f\cdot \mathrm{d}\boldsymbol s\text{是全微分}}
$$
### 用来求原函数
如果$P,Q$满足上述四个条件中的任意一个（一般判定满足$\displaystyle \frac{ \partial P }{ \partial y }= \frac{ \partial Q }{ \partial x }$最为方便）, 则说明了二元函数在以固定的$A(x_0,y_0)$为起点, 可变的$B(x,y)$为终点的曲线$L$上有
$$
\begin{aligned}
u(x,y) &= \int_{L} P \mathrm{d}x + Q \mathrm{d}y = \int_{A(x_0,y_0)}^{B(x,y)} P(s,t) \mathrm{d}s+ Q(s,t) \mathrm{d}t \\
& = \int_{x_0}^xP(s,y_0) \mathrm{d}s + \int_{y_0}^yQ(s,t) \mathrm{d}t\quad (x_0,y_0) \to (x,y_0) \to(x,y) \\
& = \int_{x_0}^xP(s,t) \mathrm{d}s + \int_{y_0}^yQ(x_0,t) \mathrm{d}t\quad (x_0,y_0) \to (x_0,y) \to(x,y) 
\end{aligned}
$$
两条不同的路径给出了不同的积分方式, 但是最终的积分结果总是具有性质
$$
\mathrm{d}u = P \mathrm{d}x + Q \mathrm{d}y
$$
也就是说, 我们利用上面的积分找到$P\mathrm{d}x + Q \mathrm{d}y$的一个*原函数*
### 计算例题
计算$\displaystyle \int_{\ell} x \mathrm{d}y$, 其中$\ell$为半径为$r$的圆在第一象限的部分, 方向为顺时针. 我们考虑三段路径
$$
L_1 :\text{线段} (r,0) \to(0,0),\quad L_2:\text{线段}(0,0) \to(0,r),\quad L_3:\ell
$$
和函数$\boldsymbol f = (0,x)$, 故由Green公式有（上面的顺时针路径导致了左边的负号）
$$
-\iint_D \mathrm{d}S = 0 + 0  + \int_\ell x \mathrm{d}y \implies \int_\ell x \mathrm{d}y = - \dfrac{1}{4}\pi r^{2}
$$
或者我们可以直接换元
$$
x = r\cos \theta,\; y=r \sin \theta,\;(0 \leq \theta \leq \dfrac{\pi}{2})
$$
于是有 
$$
\int_\ell x \mathrm{d}y = \int_{\pi/2}^0 r\cos \theta \cdot r \cos \theta \mathrm{d}\theta = \dfrac{r^{2}}{2}\int_{\pi/2}^0 (1+\cos2\theta) \mathrm{d}\theta = -\dfrac{1}{4}\pi r^{2}
$$
> [!tip]
> 使用Green公式时先画个图把路径的方向标出来（顺时针还是逆时针）, 然后根据方向来确定积分的**上下限**

计算$\displaystyle I = \oint_\ell \dfrac{x \mathrm{d}y - y \mathrm{d}x}{x^{2}+y^{2}}$ , 其中$\ell$是不包含原点的任意封闭曲线. 设$\boldsymbol f = \left( -\dfrac{y}{x^{2}+y^{2}}, \dfrac{x}{x^{2}+y^{2}} \right)$, 则
$$
\begin{aligned}
\nabla \times \boldsymbol f &= \frac{ \partial  }{ \partial x } \left( \dfrac{x}{x^{2}+y^{2}} \right) - \frac{ \partial  }{ \partial y } \left( -\dfrac{y}{x^{2}+y^{2}} \right) \\
&= \dfrac{(x^{2}+y^{2})-x\cdot2x +x^{2}+y^{2}-y\cdot 2y}{(x^{2}+y^{2})^{2}} = 0
\end{aligned} 
$$
故$I = 0$. 也可以利用换元法, 设$x = r\cos \theta, y = r \sin \theta$, 则有
$$
I = \oint_{\ell'} \dfrac{r\cos \theta \cdot r\cos \theta \mathrm{d}\theta-r\sin \theta(-r\sin \theta)\mathrm{d}\theta}{r^{2}} = \oint_{\ell'} \mathrm{d}\theta = 0
$$

计算抛物线$(x+y)^{2} = ax \; (a>0)$与$x$轴所围的面积, 则我们希望求$\displaystyle \iint_D1 \cdot \mathrm{d}S$, 需要找到一个函数$\boldsymbol f$使得$\displaystyle \nabla \times \boldsymbol f = 1 \iff \frac{ \partial f_y }{ \partial x } -\frac{ \partial f_x }{ \partial y } = 1$, 故可令$\boldsymbol f =(y, 0)$, 则此时有
$$
\iint_D \mathrm{d}S = \oint_{\delta D} y \mathrm{d}x= 0 + \int_a^0 (x -\sqrt{ ax }) \mathrm{d}x = \left(\dfrac{x^{2}}{2}- \dfrac{2}{3}\sqrt{ a }x^{3/2}\right) {\bigg|}_a^0 = \dfrac{1}{6}a^{2}
$$

用曲线积分求$\displaystyle (2x+\sin y) \mathrm{d}x + (x\cos y)\mathrm{d}y$的一个原函数, 考虑到
$$
\frac{ \partial  }{ \partial x } \left( x\cos y \right) -\frac{ \partial  }{ \partial y } \left( 2x+\sin y \right) = \cos y - \cos y = 0
$$
故我们使用积分, 选取参考点为$(0,0)$, 采取路径$(0,0)\to(0,y) \to(x,y)$
$$
\begin{aligned}
u(x,y) &= \int_0^y 0\cdot\cos y \mathrm{d}y + \int_0^x (2x+\sin y) \mathrm{d}x = x^{2} + x\sin y
\end{aligned}
$$
> [!tip]
> 路径积分求原函数, 先判断旋度是否为零, 再确定参考点, 最后确定积分路径
## 二重积分的变量代换
### 一般形式
利用[[Implicit Function#隐映射定理|Jacobian行列式]]
$$
\iint_D f(x,y) \mathrm{d}x \mathrm{d}y = \iint_\Delta f(x(u,v),\;y(u,v)) \left|J(u,v)\right| \mathrm{d}u \mathrm{d}v
$$
其中
$$
J(u,v) = \frac{ \partial (x,y) }{ \partial (u,v) } = \det \begin{pmatrix}
\dfrac{ \partial x }{ \partial u }  & \dfrac{ \partial x }{ \partial v } \\
\dfrac{ \partial y }{ \partial u }  & \dfrac{ \partial y }{ \partial v }  
\end{pmatrix} \neq 0
$$
这里从$\mathrm{d}x\mathrm{d}y \to \left|J(u,v)\right| \mathrm{d}u \mathrm{d}v$实际上代表着对应面积大小的拉伸量, 而由于二重积分不像曲线积分那样和路径的方向有关, 面积始终应当是正值, 所以这里的Jacobian行列式**必须要加上绝对值**

例如要求积分$\displaystyle \iint_D\exp(\dfrac{x-y}{x+y}) \mathrm{d}x \mathrm{d}y$, 其中$D$是$x=0,y=0,x+y=1$围成的区域, 那么我们可以作变换
$$
T:(x,y) = \left[ \dfrac{1}{2}(u+v), \;\dfrac{1}{2}(v-u) \right] 
$$
则有
$$
J(u,v) = \begin{vmatrix}
\dfrac{1}{2} & \dfrac{1}{2}  \\
-\dfrac{1}{2} & \dfrac{1}{2}
\end{vmatrix} = \dfrac{1}{2} \neq 0
$$
而新的区域由$y = 1,\;y = x,\;y = -x$围成, 有
$$
\begin{aligned}
\iint_D \exp(\dfrac{x-y}{x+y}) \mathrm{d}x \mathrm{d} y  & = \iint_\Delta \exp(\dfrac{u}{v}) \dfrac{1}{2}\mathrm{d}u \mathrm{d}v = \dfrac{1}{2} \int_0^1 \mathrm{d}v \int_{-v}^v \exp(\dfrac{u}{v}) \mathrm{d}u \\
& = \dfrac{1}{2} \int_0^1 v(e-\dfrac{1}{e}) = \dfrac{1}{4}\left( 1-\dfrac{1}{e} \right) 
\end{aligned}
$$
又例如求抛物线$y^{2}=mx,\;y^{2} = nx$和直线$y = \alpha x,\;y = \beta x$所围区域$D$的面积, 其中$0<m<n,$$\;0<\alpha<\beta$, 则可以作变换
$$
x = \dfrac{u}{v^{2}},\quad y = \dfrac{u}{v}
$$
则有在$uv$平面上$\Delta = [m,n]\times[\alpha,\beta]$, 且
$$
J(u,v) = \begin{vmatrix}
\dfrac{1}{v^{2}} & - \dfrac{2u}{v^3} \\
\dfrac{1}{v}
 & - \dfrac{u}{v^{2}}\end{vmatrix} = \dfrac{u}{v^4} >0
$$
所以
$$
\begin{aligned}
\mu(D) &= \iint_D \mathrm{d}\sigma = \iint_\Delta  \dfrac{u}{v^4} \mathrm{d}u \mathrm{d}v  \\
&= \int_\alpha^\beta  \dfrac{\mathrm{d}v}{v^4} \cdot \int_m^n u \mathrm{d}u = \dfrac{(n^{2}-m^{2})(\beta^3-\alpha^3)}{6\alpha^3\beta^3}
\end{aligned}
$$
### 极坐标形式
当积分区域是圆域或圆域的一部分时, 或者被积函数的形式为$f(x^{2}+y^{2})$时, 则我们一般采用极坐标变换
$$
T : (x,y) = (r\cos \theta,\;r\sin \theta)
$$
其对应的函数行列式为
$$
J(r,\theta) = \begin{vmatrix}
\cos \theta & -r\sin \theta \\
\sin \theta  & r\cos \theta
\end{vmatrix} = r
$$
对应的积分变换就是
$$
\iint_D f(x,y) \mathrm{d}x \mathrm{d}y = \iint_\Delta f(r\cos \theta, r \sin \theta) r \mathrm{d}r \mathrm{d}\theta
$$
但是对于极坐标（包括三维情况下的球坐标）, 我们可以直观地写出三个正交方向上的距离微元
$$
\mathrm{d}\ell_r = \mathrm{d} r,\; \mathrm{d}\ell_\theta = r \mathrm{d}\theta \implies \mathrm{d}x \mathrm{d}y = \mathrm{d}S = r \mathrm{d}r \mathrm{d}\theta
$$
这就直接给出了积分变换的形式, 这里的变换也可以推广到
$$
T :(x,y) = (ar\cos \theta,\;br\sin \theta)
$$
这相当于做了一个仿射变换, 也就有
$$
\mathrm{d}x \mathrm{d}y = \mathrm{d}S = abr \mathrm{d}r \mathrm{d}\theta
$$

例如计算$\displaystyle I = \iint_D \dfrac{\mathrm{d}S}{\sqrt{ 1-x^{2}-y^{2} }}$, 其中$D:x^{2}+y^{2}\leq1$, 则设$x = r\cos \theta,\;y=r\sin \theta$, 于是有
$$
I = \iint_{D'} \dfrac{r \mathrm{d}r \mathrm{d}\theta}{\sqrt{ 1-r^{2} }} = 2\pi \int_{1-0^{2}}^{1-1^{2}} \left( -\dfrac{1}{2} \right)  \dfrac{\mathrm{d}\left( 1-r^{2} \right) }{\sqrt{ 1-r^{2} }} = 2\pi
$$

再例如求球体$x^{2}+y^{2}+z^{2} \leq R^{2}$被圆柱面$x^{2}+y^{2} = Rx$所割下部分的体积$V$, 这里我们有两种换元选择
1. $x = r\cos \theta,\; y = r \sin \theta$, 好处是对$z\mathrm{d}S = 2\sqrt{ R^{2}-r^{2} }\cdot r\mathrm{d}r \mathrm{d}\theta$积分较为方便, 坏处是处理积分限比较麻烦
2. $x = \dfrac{R}{2}+\dfrac{r}{2}\cos \theta,\;y = \dfrac{r}{2} \sin \theta$, 好处是容易处理边界, 坏处是$z\mathrm{d}S$长得非常难看
这里我们选取第一种方式, 考虑边界条件$x^{2} + y^{2} \leq Rx \implies r \leq R\cos \theta$, 我们设置积分限$-\dfrac{\pi}{2} \leq \theta \leq \dfrac{\pi}{2},\;0 \leq r \leq R\cos \theta$, 这时候就有
$$
\begin{aligned}
V &= \iint_{D'} 2\sqrt{ R^{2}-r^{2} } \cdot r \mathrm{d}r \mathrm{d}\theta = \int_{-\pi/2}^{\pi/2} \int_0^{R\cos \theta}\sqrt{ R^{2}-r^{2}} \cdot 2r\mathrm{d}r \mathrm{d}\theta \\
&= -2 \int_0^{\pi/2} \int_{R^{2}}^{R^{2}\sin ^{2}\theta} \sqrt{ R^{2}-r^{2} } \mathrm{d}\left( R^{2}-r^{2} \right)  \mathrm{d}\theta \\
&= -\dfrac{4}{3} \int_0^{\pi/2} (R^3\sin^3\theta-R^3)\mathrm{d}\theta = \dfrac{2}{3}\pi R^{3} - \dfrac{4}{3}R^3\int_0^{\pi/2} \sin^3 \theta \mathrm{d}\theta \\
&= \dfrac{2}{3}\pi R^3 - \dfrac{4}{3}R^{2} \cdot \dfrac{2}{3\times1} = \dfrac{4}{3}R^3\left( \dfrac{\pi}{2} - \dfrac{2}{3}\right) 
\end{aligned}
$$
最后利用了Wallis积分
$$
n \in \mathbb{N} \implies \int_0^{\pi/2} \sin^n x \mathrm{d} x= \begin{cases}
\dfrac{(n - 1)!!}{n!!} \cdot \dfrac{\pi}{2} &, \text{$n$为偶数} \\
\dfrac{(n - 1)!!}{n!!} &, \text{$n$为奇数}
\end{cases}
$$

再如计算$\displaystyle I = \iint_D \exp(-x^{2}-y^{2})\mathrm{d}S$, 其中$D: x^{2}+y^{2} \leq R^{2}$, 采用极坐标变换, 则有
$$
\begin{aligned}
I &= \int_0^{2\pi} \int_0^R \exp(-r^{2}) r \mathrm{d}r \mathrm{d}\theta  \\
&=  2\pi\cdot \left( -\dfrac{1}{2} \right) \int_0^{-R^{2}} \exp(-r^{2}) \mathrm{d}(-r^{2}) = \pi\left[ 1-\exp(-R^{2}) \right] 
\end{aligned}
$$
> [!Tip]
> 先写出合适的换元公式, 确定面积元的变换, 再确定**积分的边界**即积分变量的范围（注意要保证如$r$需要取到正值, 如果$\theta$和被积函数有关则尽可能一开始利用对称性将其转化为$[0, \dfrac{\pi}{2}]$, 否则之后的每一步都有可能需要讨论$\sin \theta, \cos \theta$的正负）, 最后再积分. 含有三角函数的积分常用到Wallis积分结果
## 三重积分
只需要注意三种积分常见的变量替换有两种
### 柱坐标变换
考虑变换
$$
T : \begin{cases}
x = r\cos \theta, & 0 \leq r < +\infty \\
y = r\sin \theta, & 0 \leq \theta \leq 2\pi \\
z =z, & -\infty<z<+\infty
\end{cases}
$$
其对应的函数行列式
$$
J(r,\theta,z) = \begin{vmatrix}
\cos \theta & -r\sin \theta & 0 \\
\sin \theta & r\cos \theta & 0 \\
0 & 0 & 1
\end{vmatrix} = r
$$
故有换元公式
$$
\iiint_Vf(x,y,z) \mathrm{d}x \mathrm{d}y \mathrm{d}z = \iiint_{V'} f(r\cos \theta, r\sin \theta,z)r \mathrm{d}r \mathrm{d}\theta \mathrm{d}z
$$
### 球坐标变换
考虑变换
$$
T : \begin{cases}
x = r\sin \phi \cos \theta, & 0 \leq r < +\infty \\
y = r\sin \phi \sin \theta, & 0 \leq \phi \leq \pi \\
z = r \cos \phi, & 0 \leq \theta \leq 2\pi
\end{cases}
$$
也就有
$$
J(r,\phi,\theta) = \begin{vmatrix}
\sin \phi \cos \theta & r\cos \phi \cos\theta &-r\sin \phi \sin \theta \\
\sin \phi \sin \theta & r\cos \phi \sin \theta & r\sin \phi \cos \theta \\
\cos \phi & -r\sin \phi  & 0
\end{vmatrix} = r^{2}\sin \phi
$$
即有
$$
\iiint_Vf(x,y,z) \mathrm{d}x \mathrm{d}y \mathrm{d}z = \iiint_{V'}f(r\sin \phi \cos \theta,r\sin \phi \sin \theta,r\cos \phi)r^{2}\sin \phi \mathrm{d}r \mathrm{d}\phi \mathrm{d}\theta
$$
也可以拓展至广义球坐标变换
$$
T : \begin{cases}
x = ar\sin \phi \cos \theta, & 0 \leq r < +\infty \\
y = br\sin \phi \sin \theta, & 0 \leq \phi \leq \pi \\
z = cr \cos \phi, & 0 \leq \theta \leq 2\pi
\end{cases}
$$
相应地有
$$
J(r,\phi,\theta) = abcr^{2}\sin \phi
$$
> [!Tip] 
> 需要注意球坐标变换中引入了新变量$\phi$, 其取值范围为$0 \leq \phi \leq \pi$, 故$\sin \phi \geq 0$, $r^{2}\sin \phi$一般不需要加上绝对值

计算$I= \displaystyle \iiint_V (x^{2}+y^{2}+z) \mathrm{d}x \mathrm{d}y \mathrm{d}z$, 其中$V$是由$\displaystyle \begin{cases}z = y \\ x = 0\end{cases}$绕$z$轴旋转而成的曲面与$z = 1$围成的区域
我们首先确定积分限, 积分区域是一个圆锥体区域, $x,y$的范围是$x^{2}+y^{2} \leq 1$, 每一个$x-y$平面上的点对应的$z$的积分限为$\sqrt{ x^{2}+y^{2} } \leq z \leq 1$, 我们采用柱坐标换元
$$
\begin{aligned}
I &= \int_{0}^{2\pi} \int_{0}^1 \int_{\sqrt{ x^{2}+y^{2} }=r}^1 (r^{2} + z) \mathrm{d}z\cdot r\mathrm{d}r \mathrm{d}\theta \\
&= 2\pi \int_0^1 \left[ r^{2}(1-r)+\dfrac{1}{2}(1-r^{2}) \right]  r \mathrm{d}r \\
&=2\pi \int_0^1 \left( -r^4+\dfrac{1}{2}r^3 + \dfrac{1}{2}r \right)  \mathrm{d}r \\
&=2\pi \left( - \dfrac{1}{5} + \dfrac{1}{8} + \dfrac{1}{4} \right) = \dfrac{7\pi}{20}
\end{aligned}
$$
> [!Tip]
> 不要漏了面积比例因子中那个额外的$r$

求$\displaystyle I =\iiint_V \left( \dfrac{x^{2}}{a^{2}} + \dfrac{y^{2}}{b^{2}} + \dfrac{z^{2}}{c^{2}} \right) \mathrm{d}x \mathrm{d}y \mathrm{d}z$, 其中$V : \dfrac{x^{2}}{a^{2}} + \dfrac{y^{2}}{b^{2}} + \dfrac{z^{2}}{c^{2}} \leq 1$, 则我们采用广义球坐标变换
$$
x = ar \sin \phi \cos \theta,\; y = b r \sin \phi \sin \theta,\; z = cr\cos \phi \implies \mathrm{d}V = abcr^{2}\sin \phi \mathrm{d}r \mathrm{d}\phi \mathrm{d}\theta
$$
于是有
$$
\begin{aligned}
I &= \int_0^{2\pi} \int_{0}^{\pi} \int_0^1 r^{2}\cdot abcr^{2}\sin \phi \mathrm{d}r \mathrm{d}\phi \mathrm{d}\theta \\
&= 2\pi \int_0^{\pi} \dfrac{1}{5}abc\sin \phi \mathrm{d}\phi \\
& = \dfrac{4}{5} abc \pi
\end{aligned}
$$
> [!Tip]
> 不要漏乘$abc$

计算$I = \displaystyle \iiint_V (x^{2}+y^{2}) \mathrm{d}x \mathrm{d}y \mathrm{d}z$, 其中$V$是曲面$2(x^{2}+y^{2}) = z$与$z = 4$为界面的区域, 采用柱坐标变换
$$
x = r \cos \theta,\; y = r\sin \theta \implies \mathrm{d}V = r \mathrm{d}r \mathrm{d}\theta \mathrm{d}z
$$
其中 $2r^{2} \leq z \leq 4,\;0 \leq r \leq \sqrt{ 2 },\;0 \leq \theta \leq 2\pi$, 故
$$
\begin{aligned}
I &= \int_0^{2\pi} \int_0^{\sqrt{ 2 }} \int_{2r^{2}}^4 r^{2}\cdot r \mathrm{d}z \mathrm{d}r \mathrm{d}\theta \\
&= 2\pi \int_{0}^{\sqrt{ 2 }} \left( r^3\cdot4 - r^3\cdot2r^{2} \right)  \mathrm{d}r \\
& = 2\pi \left[ (\sqrt{ 2 })^4 - \dfrac{1}{3}(\sqrt{ 2 })^6 \right]  = \dfrac{8\pi}{3}
\end{aligned}
$$

计算由圆锥体$z \geq \sqrt{ x^{2}+y^{2} }\cot \beta$和球体$x^{2}+y^{2}+(z-a)^{2} \leq a^{2}$所确定的立体的体积$V$, 这里如果使用柱坐标变换, 就非常难以确定$z$的积分限, 我们需要对方程$r\cot \beta = a \pm \sqrt{ a^{2}-r^{2} }$的根进行讨论, 而球坐标变换有以下两种设法
$$
x = r \sin \phi \cos \theta,\; y = r \sin \phi \sin \theta,\; z =a + r \cos \phi 
$$
和
$$
x = r\sin \phi \cos \theta,\; y = r \sin  \phi \sin \theta,\; z = r\cos \phi
$$
我们看到题目中球体的形式, 习惯于采用第一种设法, 但是这个时候的边界条件
$$
z \geq \sqrt{ x^{2} + y^{2} } \cot \beta \iff a + r\cos \phi \geq r \cot \beta
$$
处理起来比较麻烦, 但是如果我们采用第二种设法, 我们会得到两个约束条件
$$
z \geq \sqrt{ x^{2} + y^{2} } \cot \beta \iff r \cos \phi \geq r \cot \beta \iff 0 \leq \phi \leq \arccos (\cot \beta)
$$
和
$$
x^{2}+y^{2} + (z-a)^{2} \leq a^{2} \iff a^{2} -2ar\cos \phi + a^{2} \leq a^{2} \iff r \leq 2a\cos \phi
$$
而$\theta$的约束条件仍然是$0 \leq \theta \leq 2\pi$, 则此时有
$$
\begin{aligned}
V &= \int_0^{2\pi} \int_{0}^{\arccos(\cot \beta)} \int_0^{2a\cos \phi} r^{2} \sin \phi \mathrm{d}r \mathrm{d}\phi \mathrm{d}\theta \\
&= \dfrac{16}{3}\pi a^3 \int_0^{\arccos(\cot \beta)} \cos^3 \phi \sin \phi \mathrm{d}\phi\\
& = -\dfrac{16}{3}\pi a^3 \int_1^{\cot \beta} \cos^3 \phi \mathrm{d}(\cos \phi) \\
&= \dfrac{4}{3}\pi a^3 \left( 1 - \cot^4 \beta \right) 
\end{aligned}
$$
> [!Tip]
> 不要忘记球坐标变换中$x^{2}+y^{2} + z^{2}= r^{2}$其中$r$是变量
> 选择合适的坐标变换, 不是题目中出现了$(z-a)^{2}$就一定要把$z$换成$a + \cdots$的形式
> 无论如何先画个图, 来更好地确定变量的约束条件

## 重积分的应用
### 曲面的面积
设函数$f(x,y)$在$D$上具有连续的一阶偏导数, 对于方程
$$
z = f(x,y),\; (x,y)\in D
$$
确定的曲面, 它的面积为
$$
\Delta S = \iint_D \sqrt{ 1 + f_x^{2}(x,y) +f_y^{2}(x,y) } \mathrm{d}x \mathrm{d}y
$$
或者写成
$$
\Delta S = \iint_D \dfrac{\mathrm{d}x \mathrm{d}y}{\left|\cos \left< \boldsymbol n, \boldsymbol {\hat{z}} \right> \right|}
$$
### 质心的位置
对于某三维物体
$$
\bar{x} = \dfrac{\iiint_V x\rho(x,y,z) \mathrm{d}V}{\iiint_V \rho(x,y,z) \mathrm{d}V},\quad \bar{y} = \dfrac{\iiint_V y\rho(x,y,z) \mathrm{d}V}{\iiint_V \rho(x,y,z) \mathrm{d}V}
$$
对于平面薄板
$$
\bar{x} = \dfrac{\iint_D x \rho(x,y) \mathrm{d}\sigma}{\iint_D \rho(x,y) \mathrm{d}\sigma},\; \bar{y} = \dfrac{\iint_D y \rho(x,y) \mathrm{d}\sigma}{\iint_D \rho(x,y) \mathrm{d}\sigma}
$$
#### 形心公式
例如在对称的区域$D$（通常是球或者圆）上要计算
$$
\iint_D (x+3y) \mathrm{d}x \mathrm{d}y= \iint_D x \mathrm{d}x\mathrm{d}y + 3 \iint_D y \mathrm{d}x \mathrm{d}y = \bar{x} S_D + 3 \bar{y} S_D
$$

### 转动惯量
回顾力学定义
$$
J_o = \iiint_V R^{2}\mathrm{d}m = \iiint \Vert \overrightarrow{OR} \Vert ^{2} \rho \mathrm{d}V
$$
则有
$$
\begin{aligned}
J_x & = \iiint_V (y^{2}+z^{2}) \rho(x,y,z) \mathrm{d}V \\
J_y & = \iiint_V (x^{2}+z^{2}) \rho(x,y,z) \mathrm{d}V \\
J_z & = \iiint_V (x^{2}+y^{2}) \rho(x,y,z) \mathrm{d}V \\
J_{xy} & = \iiint_V (z^{2}) \rho(x,y,z) \mathrm{d}V \\
J_{yz} & = \iiint_V (x^{2}) \rho(x,y,z) \mathrm{d}V \\
J_{zx} & = \iiint_V (y^{2}) \rho(x,y,z) \mathrm{d}V
\end{aligned}
$$

求圆锥$z = \sqrt{ x^{2}+y^{2} }$在圆柱体$x^{2}+y^{2} \leq x$内那一部分的面积$S$, 我们求
$$
\frac{ \partial z }{ \partial x } = \dfrac{x}{\sqrt{ x^{2}+y^{2} }},\; \frac{ \partial z }{ \partial y } = \dfrac{y}{\sqrt{ x^{2}+y^{2} }}
$$
故$\sqrt{ 1 + z_x^{2} + z_y^{2} } = \sqrt{ 2 }$, 即$\displaystyle S = \sqrt{ 2 } \iint_D \mathrm{d}x \mathrm{d}y$, 又考虑到
$$
x^{2}+y^{2} \leq x \iff \left( x - \dfrac{1}{2} \right) ^{2} + y^{2} = \dfrac{1}{4}
$$
故$S = \sqrt{ 2} \pi \left( \dfrac{1}{2} \right)^{2} = \dfrac{\sqrt{ 2 }}{4}\pi$
# 曲面积分
## 第一型曲面积分
如下面的形式
$$
\iint_S f(x,y,z) \mathrm{d}S
$$
取合适的坐标系, 利用曲面方程把$z$化成以$x,y$表达的函数, 就可以把第一型曲面积分化成[[Multiple Integral#二重积分|二重积分]]

如果$S$由$z = z(x,y)$来表示, 则利用[[Multiple Integral#曲面的面积|曲面面积的求法]], 有
$$
\iint_S f(x,y,z) \mathrm{d}S = \iint_D f(x,y,z(x,y)) \sqrt{ 1+z_x^{2}+z_y^{2} } \mathrm{d} x \mathrm{d}y
$$
更一般地, 我们设$S$上的每一个点$\boldsymbol r$都可以通过两个参数来决定, 即我们有$\boldsymbol r(s,t)$, 其中$(s,t)$在 某个区域$D$内, 那么
$$
\iint_S f \mathrm{d}S = \iint_D f(\boldsymbol r(s,t)) \left\Vert \frac{ \partial \boldsymbol r }{ \partial s } \times \frac{ \partial \boldsymbol r }{ \partial t } \right \Vert \mathrm{d}s \mathrm{d}t
$$
其中$\Vert\cdot \Vert$表示[[Euclidean Space|欧式空间]]中的[[Euclidean Space#长度和距离|长度]], 这是因为这里的面元$\mathrm{d}S$满足
$$
\mathrm{d}S = \left\Vert \mathrm{d}\boldsymbol l_s \times \mathrm{d}\boldsymbol l_t \right\Vert  = \left\Vert \frac{ \partial \boldsymbol r(s,t) }{ \partial s } \mathrm{d}s \times \frac{ \partial \boldsymbol r(s,t) }{ \partial t } \mathrm{d}t \right\Vert 
$$

计算$\displaystyle \iint_S \dfrac{\mathrm{d}S}{z}$, 其中$S$是球面$x^{2}+y^{2} +z^{2} = a^{2}$被平面$z = h\quad(0 < h < a)$所截的顶部. 我们先写出$S$的方程
$$
S:x^{2}+y^{2} +z^{2} = a^{2},z \geq h
$$
作一个球坐标换元
$$
\begin{cases}
x = r \sin \phi \cos \theta \\
y = r \sin \phi \sin \theta \\
z = r \cos \phi
\end{cases}
$$
需要满足约束
$$
\begin{cases}
r^{2} = a^{2} \\
r\cos \phi \geq h
\end{cases} \implies \begin{cases}
r = a \\
\cos \phi \geq \dfrac{h}{a}
\end{cases}
$$
这样就可以写出$S$的参数方程
$$
S: \begin{cases}
x = a \sin \phi \cos \theta \\
y = a \sin \phi \sin \theta \\
z = a \cos \phi
\end{cases} , \quad 
0 \leq \phi \leq \arccos \dfrac{h}{a} ,\;
0 \leq \theta \leq 2\pi
$$
此时的$\mathrm{d}S$为
$$
\mathrm{d}S = \mathrm{d}l_\phi\cdot \mathrm{d}l_\theta  = a \sin \phi \mathrm{d}\phi\cdot a \mathrm{d}\theta = a^{2}\sin \phi \mathrm{d}\phi \mathrm{d}\theta
$$
故原式为
$$
\begin{aligned}
\iint_S \dfrac{\mathrm{d}S}{z} &= \int_0^{2\pi} \int_{0}^{\arccos (h/a)} \dfrac{a^{2}\sin \phi \mathrm{d}\phi}{a\cos \phi} \mathrm{d}\theta \\
&= 2\pi a \int_0^{\arccos(h/a)} \tan \phi \mathrm{d}\phi  \\
&=2\pi a \ln \left|\cos \phi\right| {\bigg\vert}_0^{\arccos (h/a)} \\
&= 2\pi a \ln \dfrac{a}{h}
\end{aligned}
$$
> [!tip]
> $$\int \tan x \mathrm{d}x = \ln \left|\cos x\right|$$

计算$I = \displaystyle \iint_S(x^{2}+y^{2}+z^{2}) \mathrm{d}S$, 其中$S: x^{2}+y^{2}+z^{2} =2az$, 同样采用球坐标变换
$$
S:\begin{cases}
x = a \sin \phi \cos \theta \\
y = a \sin \phi \sin \theta \\
z = a+a\cos \phi 
\end{cases},\quad 0 \leq \phi \leq \pi, \; 0 \leq \theta \leq 2\pi
$$
且$\mathrm{d}S = a^{2}\sin \phi \mathrm{d}\phi \mathrm{d}\theta$
故有
$$
\begin{aligned}
I &= \int_0^{2\pi} \int_0^{\pi} (2a^{2} + 2a^{2}\cos \phi) a^{2}\sin \phi\mathrm{d}\phi \mathrm{d}\theta \\
&= 4\pi a^{4}\int_0^{\pi}(\sin \phi+\sin \phi\cos \phi) \mathrm{d}\phi \\
& = 4\pi a^{4} \left( 2 + 0 \right)  = 8\pi a^4
\end{aligned}
$$
> [!Tip]
> 此题中如果用标准的球坐标变换形式, 则参数方程及其面元的形式将会十分难看. 所以如何选取球坐标变换的形式需要综合分析在某个变换下被积函数$f$本身和面元$\mathrm{d}S$的复杂程度（在计算多重积分时则是$S$的边界的复杂程度）

求均匀曲面$x^{2}+y^{2}+z^{2} = a^{2},\;x \geq 0,\; y \geq 0,\;z\geq 0$的质心, 考虑球坐标
$$
\begin{cases}
x = a\sin \phi \cos \theta \\
y = a \sin \phi \sin \theta \\
z = a\cos \phi
\end{cases},\quad 0 \leq \phi,\theta \leq \dfrac{\pi}{2}
$$
且$\mathrm{d}S = a^{2} \sin \phi \mathrm{d}\phi \mathrm{d}\theta$
由于$x,y,z$对称, 所以我们只需要计算一个方向的质心位置
$$
\begin{aligned}
\Delta S\cdot \bar{z} &= \int_0^{\pi/2} \int_0^{\pi/2} a \cos \phi\cdot a^{2}  \sin \phi \mathrm{d}\phi \mathrm{d}\theta  \\
&= \dfrac{a^3\pi}{2} \int_0^1 \sin \phi \mathrm{d}(\sin \phi) = \dfrac{a^3\pi}{4}
\end{aligned}
$$
而$\Delta S = \dfrac{1}{8}\cdot4\pi a^{2}$, 故$\bar{z} = \dfrac{a}{2}$

## 第二型曲面积分
对于向量值函数$\boldsymbol f(x,y,z)$定义第二型曲面积分
$$
\iint_S \boldsymbol f\cdot \mathrm{d}\boldsymbol S =\iint_S\boldsymbol f\cdot \boldsymbol{\hat{n}} \mathrm{d}S = \iint_S (f_x\hat{n}_x+f_y\hat{n}_y +  f_z\hat{n}_z) \mathrm{d}S
$$
写出分量后即可转换位第一型曲面积分来计算

我们有时候也把上面的式子写成
$$
\begin{aligned}
\iint_S\boldsymbol f\cdot \boldsymbol{\hat{n}} \mathrm{d}S &= \iint_S (f_x\hat{n}_x+f_y\hat{n}_y +  f_z\hat{n}_z) \mathrm{d}S \\
&= \iint_S f_x \mathrm{d}y \mathrm{d}z + f_y \mathrm{d}z \mathrm{d}x + f_z \mathrm{d}x \mathrm{d}y
\end{aligned}
$$

设积分曲面可由方程$F(x,y,z) = 0$来描述, 则由[[Implicit Function#曲面的切平面与法线|隐函数定理]], 其上某点的法向量由隐函数$z = z(x,y)$确定
$$
\boldsymbol n = (z_x(x_0,y_0), z_y(x_0,y_0),-1) \text{ or } \boldsymbol n = (-z_x(x_0,y_0), -z_y(x_0,y_0),1)
$$
根据不同的正负规定, 可以得到
$$
\boldsymbol {\hat{n}} = \pm\left( \frac{z_x}{\sqrt{ 1+z_x^{2}+z_y^{2} }}, \frac{z_y}{\sqrt{ 1+z_x^{2}+z_y^{2} }}, - \frac{1}{\sqrt{ 1+z_x^{2}+z_y^{2} }} \right) 
$$
或者我们采用更一般的形式, 如果光滑曲面$S$可以由参量方程给出
$$
S: \begin{cases}
 x= x(u,v)\\
y = y(u,v) \\
z = z(u,v)
\end{cases}
$$
则有对应的一个法向量
$$
\left( \frac{ \partial (y,z) }{ \partial (u,v) } ,\frac{ \partial (z,x) }{ \partial (u,v) } ,\frac{ \partial (x,y) }{ \partial (u,v) }  \right) 
$$
且它的大小恰好满足
$$
\begin{gather}
\iint_S f_x \mathrm{d}y \mathrm{d}z + f_y \mathrm{d}z \mathrm{d}x + f_z \mathrm{d}x \mathrm{d}y  \\
= \pm \left[ \iint_{S'} f_x\frac{ \partial (y,z) }{ \partial (u,v) } \mathrm{d}u \mathrm{d}v + f_y \frac{ \partial (y,z) }{ \partial (u,v) }\mathrm{d}u \mathrm{d}v + f_z \frac{ \partial (y,z) }{ \partial (u,v) } \mathrm{d}u \mathrm{d}v \right] 
\end{gather}
$$
这里的正负号取决于法向量$\displaystyle \left( \frac{ \partial (y,z) }{ \partial (u,v) } ,\frac{ \partial (z,x) }{ \partial (u,v) } ,\frac{ \partial (x,y) }{ \partial (u,v) }  \right)$是否在正向一侧


计算$\displaystyle \iint_S xyz \mathrm{d}x \mathrm{d}y$, 其中$S:x^{2}+y^{2}+z^{2} = 1, \; x\geq0, y \geq0$, 则曲面的法向量为
$$
\begin{aligned}
\boldsymbol n = (x,y,z) \implies \boldsymbol{\hat{n}} = \dfrac{(x,y,z)}{\sqrt{ x^{2}+y^{2}+z^{2} }}=(x,y,z)
\end{aligned}
$$
可以看出
$$
\iint_S xyz \mathrm{d}x \mathrm{d}y = \iint_S xyz^{2} \mathrm{d}S
$$
考虑球坐标
$$
\begin{cases}
x = \sin \phi \cos \theta \\
y = \sin \phi \sin \theta \\
z = \cos \phi
\end{cases}, \quad 0 \leq \phi \leq \pi,0 \leq \theta \leq \dfrac{\pi}{2}
$$
则有$\mathrm{d}S = 1^{2}\cdot \sin \phi \mathrm{d}\phi \mathrm{d}\theta$, 故
$$
\begin{aligned}
\iint_S xyz \mathrm{d}x \mathrm{d}y &= \iint_S xyz^{2} \mathrm{d}S \\
&= \int_0^{\pi/2} \int_0^{\pi} \sin ^{2}\phi \cos ^{2}\phi \sin \theta \cos \theta\cdot \sin \phi \mathrm{d}\phi \mathrm{d}\theta \\
&= \int_0^{\pi/2} \sin \theta \cos \theta \left[  \int_{-1}^1 (1-\cos ^{2}\phi)\cos ^{2}\phi \mathrm{d}(\cos \phi)  \right] \mathrm{d}\theta \\
&= \dfrac{4}{15} \int_0^{1} \sin \theta \mathrm{d}(\sin \theta) = \dfrac{2}{15}
\end{aligned}
$$

计算$\displaystyle \iint_S x^3 \mathrm{d}y \mathrm{d}z$, 其中$S: \dfrac{x^{2}}{a^{2}} + \dfrac{y^{2}}{b^{2}} + \dfrac{z^{2}}{c^{2}}=1,\;(z>0)$, 由于法向量较难计算, 我们直接作换元
$$
\begin{cases}
x = a  \sin \phi \cos \theta \\
y = b \sin \phi \sin \theta \\
z = c \cos \phi
\end{cases}, \quad 0 \leq \phi \leq \dfrac{\pi}{2}, 0 \leq \theta \leq 2\pi
$$
则我们计算
$$
\begin{aligned}
\mathrm{d}y \mathrm{d}z&= \begin{vmatrix}
\dfrac{ \partial y }{ \partial \phi }  & \dfrac{ \partial y }{ \partial \theta }  \\
\dfrac{ \partial z }{ \partial \phi }  & \dfrac{ \partial z }{ \partial \theta } 
\end{vmatrix} \mathrm{d}\phi \mathrm{d}\theta  \\
&= \begin{vmatrix}
b\sin \theta \cos \phi & b\sin \phi \cos \theta \\
-c\sin \phi & 0
\end{vmatrix}\mathrm{d}\phi \mathrm{d}\theta  \\
&= bc\sin ^{2}\phi \cos \theta \mathrm{d}\phi \mathrm{d}\theta
\end{aligned}
$$
同理, 在一开始计算$\displaystyle \iint_S xyz \mathrm{d}x \mathrm{d}y$, 其中$S:x^{2}+y^{2}+z^{2} = 1, \; x\geq0, y \geq0$时, 我们也能这样直接计算
$$
\begin{cases}
x = \sin \phi \cos \theta \\
y = \sin \phi \sin \theta \\
z = \cos \phi
\end{cases},\quad 0 \leq \phi \leq \pi, 0 \leq \theta \leq \dfrac{\pi}{2}
$$
于是
$$
\mathrm{d}x \mathrm{d}y = \begin{vmatrix}
\cos \theta \cos \phi  & -\sin \phi \sin \theta \\
\sin \theta \cos \phi  & \sin \phi \cos \theta
\end{vmatrix} \mathrm{d}s \mathrm{d}t = \cos \phi \sin \phi \mathrm{d}s \mathrm{d}t
$$
就和直接转化为$\hat{n}_z\mathrm{d}S$的办法得到了一样的积分式子

- [ ] 计算$\displaystyle \iint_S (2x+z) \mathrm{d}y \mathrm{d}z + z \mathrm{d}x \mathrm{d}y$, 其中$S: z = x^{2}+y^{2}, 0 \leq z \leq 1$, 我们依旧可以通般方法
$$
\begin{cases}
z = r^{2} \\
x =  r \cos \theta \\
y = r \sin \theta
\end{cases}, \quad 0 \leq r \leq 1,0 \leq \theta \leq 2\pi
$$
则有
$$
\begin{gather}
\mathrm{d}y \mathrm{d}z = \begin{vmatrix}
\sin \theta  & r \cos \theta \\
2r & 0
\end{vmatrix} \mathrm{d}r \mathrm{d}\theta = -2r^{2}\cos \theta \mathrm{d}r \mathrm{d}\theta\\
\mathrm{d}x \mathrm{d}y = \begin{vmatrix}
\cos \theta & -r\sin \theta \\
\sin \theta & r\cos \theta
\end{vmatrix}\mathrm{d}r \mathrm{d}\theta = r \mathrm{d}r \mathrm{d}\theta \\
\end{gather}
$$
故
$$
\begin{aligned}
\iint_S (2x+z) \mathrm{d}y \mathrm{d}z &= -\int_0^{2\pi} \int_0^1 (2r\cos \theta + r^{2}) 2r^{2}\cos \theta \mathrm{d}r \mathrm{d}\theta \\
&= -\int_0^{2\pi} \left( \cos \theta + \dfrac{2}{5} \right) \cos \theta\mathrm{d}\theta \\
&= -\int_0^{2\pi} \cos ^{2} \theta \mathrm{d}\theta  = -2\pi + 4 \times \dfrac{1}{2} \times \dfrac{\pi}{2} = -\pi
\end{aligned}
$$
和
$$
\begin{aligned}
\iint_S z \mathrm{d}x \mathrm{d}y  &= \int_0^{2\pi} \int_0^1 r^{2} r \mathrm{d}r \mathrm{d}\theta = 2\pi\cdot \dfrac{1}{4} = \dfrac{\pi}{2}
\end{aligned}
$$
综上$\displaystyle  \iint_S (2x+z) \mathrm{d}y \mathrm{d}z + z \mathrm{d}x \mathrm{d}y = -\dfrac{\pi}{2}$


## Gauss公式
$$
\iiint_V (\nabla\cdot \boldsymbol F) \mathrm{d}V = \iint_S (\boldsymbol F\cdot \boldsymbol {\hat{n}}) \mathrm{d}S
$$
计算$\displaystyle \iint_S y(x-z) \mathrm{d}y \mathrm{d}z+x^{2} \mathrm{d}z \mathrm{d}x+ (y^{2} +xz) \mathrm{d}x \mathrm{d}y$, 其中$S$表示由$x=y=z=0$,$x=y=z=a$六个平面所围立方体的表面

我们可以写出
$$
\boldsymbol F = (yx-yz,x^{2},y^{2}+xz)
$$
故此时有
$$
\begin{aligned}
\text{原式} &= \iiint_V \left( y + 0 + z \right)  \mathrm{d}V  \\
&= \int_0^a \int_0^a \int_0^a (y+z) \mathrm{d}y \mathrm{d}z \mathrm{d}x  \\
&=a \int_0^a \left( \dfrac{a^{2}}{2} + az \right)  \mathrm{d}z \\
&= a\left( \dfrac{a^3}{2} + a\cdot \dfrac{a^2}{2} \right)  = a^4
\end{aligned}
$$

## Stokes公式
$$
\iint_\Sigma (\nabla \times \boldsymbol F)\cdot \mathrm{d} \boldsymbol {\Sigma} = \int_{\delta \Sigma} \boldsymbol F\cdot \mathrm{d}(\boldsymbol \Gamma)
$$
计算
$$
I = \oint_\ell (y^{2}-z^{2}) \mathrm{d}x + (z^{2}-x^{2}) \mathrm{d}y + (x^{2}-y^{2}) \mathrm{d}z
$$
其中$\ell$是立方体$[0,a]\times[0,a]\times[0,a]$的表面和平面$x + y + z = \dfrac{3a}{2}$的交线

我们写出函数
$$
\boldsymbol F = (y^{2}-z^{2},z^{2}-x^{2},x^{2}-y^{2})
$$
计算
$$
\begin{aligned}
\nabla \times \boldsymbol F &= \begin{vmatrix}
\boldsymbol{\hat{x}}  & \boldsymbol{\hat{y}} & \boldsymbol{\hat{z}} \\
\frac{ \partial  }{ \partial x }  & \frac{ \partial  }{ \partial y } & \frac{ \partial  }{ \partial z }  \\
y^{2}-z^{2} & z^{2}-x^{2} & x^{2}-y^{2}
\end{vmatrix}  \\
&= (-2y-2z) \boldsymbol{\hat{x}} + (-2z-2x) \boldsymbol{\hat{y}} + (-2x-2y) \boldsymbol{\hat{z}}
\end{aligned}
$$
而$\ell$所围成的面$\Sigma$的法向量为$\displaystyle \left( \dfrac{1}{\sqrt{ 3 }}, \dfrac{1}{\sqrt{ 3 }}, \dfrac{1}{\sqrt{ 3 }} \right)$, 故
$$
I = \dfrac{1}{\sqrt{ 3 }}\iint_\Sigma  (-4)(x+y+z) \mathrm{d}S = -\dfrac{4}{\sqrt{ 3 }}\cdot \dfrac{3a}{2} \Delta \Sigma
$$
而$\Sigma$为边长为$\dfrac{a}{\sqrt{ 2 }}$的正六边形, 故$\Delta \Sigma = 6 \times \dfrac{\sqrt{ 3 }}{4} \times \left( \dfrac{a}{\sqrt{ 2 }} \right)^{2} = \dfrac{3}{4}\sqrt{ 3 }a^{2}$, 即$I = -\dfrac{9}{2}a^{2}$

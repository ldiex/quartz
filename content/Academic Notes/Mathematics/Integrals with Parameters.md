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
在$[a,b]$上可微，且
$$
F'(x) = \int_{c(x)}^{d(x)} f_x(x,y)\mathrm{d} y +f(x,d(x))d'(x)- f(x,c(x))c'(x)
$$
这可以通过把$F(x)$看做三元复合函数$H(x,c,d)$，通过应用复合函数求导法则
$$
\dfrac{\mathrm{d}}{\mathrm{d} {x}}F(x) = \dfrac{\partial {H}}{\partial {x}} + \dfrac{\partial {H}}{\partial {c}} \dfrac{\mathrm{d} {c}}{\mathrm{d} {x}} + \dfrac{\partial {H}}{\partial {d}} \dfrac{\mathrm{d} {d}}{\mathrm{d} {x}}
$$
和变限积分的求导法则
$$
\dfrac{\mathrm{d}}{\mathrm{d} {x}}\int_{u(x)}^{v(x)} f'(t)\mathrm{d} t = f(u(x))u'(x) - f(v(x))v'(x)
$$
得到
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
\lim_{A\to \infty}\sup_{x\in I}\left| \int_{A}^{\infty} f(x,y)\mathrm{d} y \right| = 0 
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

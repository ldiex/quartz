# 一致收敛性
## 函数列
函数列$f_1, f_2, \cdots, f_n, \cdots$代入$x = x_0$可以得到数列$f_1(x_0), f_2(x_0), \cdots$
若此数列收敛，则称函数列在点$x_0$收敛，$x_0$为该函数列的收敛点，反之则称函数列在点$x_0$发散. 函数列在数集$D$上的每一个点都收敛，则称函数列在数集$D$上收敛，此时可定义函数列的*极限函数*
$$
f(x) = \lim_{x \to \infty} f_n(x), \; x\in D
$$
使得函数列$\{f_n\}$收敛的全体收敛点的几何，被称为函数列的*收敛域*

若对$\forall \varepsilon > 0$总存在正整数$N$使得当$n > N$时，对一切$x \in D$，都有
$$
\left|{f_n(x) - f(x)}\right| < \varepsilon
$$
则称函数列$\{f_n\}$在$D$上*一致收敛*于$f$，记作
$$
f_n(x) \rightrightarrows f(x) \; (n \to \infty)
$$
和函数的一致收敛相似，**这里的$N$仅仅是$\varepsilon$的函数，而与$x$的取值无关**
这个命题的否定是：存在$\varepsilon_0 > 0$，对任何正整数$N$, 都有$D$上的某一点$x'$和正整数$n' > N$使得
$$
\left|{f_{n'}(x') - f(x')}\right| \ge \varepsilon_0
$$
函数列一致收敛的几何意义是：对任何$\varepsilon > 0$，对于一切序号大于$N$的曲线$y = f_n(x)$都落在以曲线$y = f(x) + \varepsilon$和$y = f(x) - \varepsilon$为边的带形区域内

## 函数列一致收敛的Cauchy准则
函数列$\{f_n\}$在数集$D$上一致收敛的充要条件是：对$\forall \varepsilon > 0$，总存在正数$N$，使得当$n,m > N$时，对一切$x \in D$都有
$$
\left|{f_n(x) - f_m(x)}\right| < \varepsilon
$$

如果已经知道函数列的极限函数，利用如下定理来判别一致收敛性更为方便：
函数列$\{f_n\}$在区间$D$上一致收敛于$f$的充要条件是
$$
\lim_{n \to \infty} \sup_{x \in D} \left|{f_n(x) - f(x)}\right| = 0
$$
由此得到推论：函数列$\{f_n\}$在$D$上不一致收敛于$f$的充分必要条件是：存在$\{x_n\} \in D$使得$\left|{f_n(x_n) - f(x_n)}\right|$不收敛于$0$

## 内闭一致收敛
设函数列$\{f_n\}$和$f$定义在区间$I$上，若对任意闭区间$[a, b] \subset I$, $\{f_n\}$在$[a, b]$上一致收敛于$f$，则称$\{f_n\}$在$I$上内闭一致收敛于$f$
若$I = [\alpha, \beta]$是有界闭区间，则$\{f_n\}$在$I$上内闭一致收敛于$f$和$\{f_n\}$在$I$上一致收敛于$f$是等价的
内闭一致收敛是比函数一致收敛更弱的条件，例子
- $f_n(x) = x^n$在$[0, 1)$上不一致收敛于$f$，但对$\forall \delta > 0$, $\displaystyle \sup_{x \in [0, \delta]} \left|{x^n}\right| \le \delta^n \to 0 \; (n \to \infty)$, 故其在$[0, 1)$上内闭一致收敛

## 函数项级数
设$\{u_n(x)\}$是定义在数集$E$上的一个函数列，表达式
$$
u_1(x) + u_2(x) + \cdots + u_n(x) + \cdots, \; x\in E
$$
称为定义在$E$上的*函数项级数*，简记为$\sum u_n(x)$. 并定义*部分和函数列*
$$
S_n(x) = \sum_{k = 1}^n u_k(x)
$$
若部分和函数列在点$x$收敛，则称该函数项级数在点$x$*收敛*. 在区间上收敛的定义类似

若部分和函数列在数集$D$上一致收敛于$S(x)$，则称该级数在$D$上*一致收敛*于$S(x)$

### 函数项级数一致收敛的Cauchy准则
 $\forall \varepsilon > 0, \; \exists N \in \mathbb N^*, \text{ s.t. } n > N \implies$
$$
\forall x \in D, p \in \mathbb N^*\; |S_{n+p}(x) - S_n(x)| < \varepsilon
$$

并定义*余项*
$$
R_n(x) = S(x) - S_n(x)
$$
有推论，另一个充要条件
$$
\lim_{n \to \infty} \sup_{x \in D} \left|{R_n(x)}\right| = 0
$$
比较函数列的收敛条件就是把$f$换成了$S = \sum f$
### 函数项级数一致收敛的其他判别法
#### Werierstrass 判别法
充分条件：对于定义在$D$上的函数项级数$\sum u_n(x)$, 如果$\sum M_n$是收敛的正项级数，若对一切$x \in D$有
$$
|u_n(x)| \le M_n,\; n = 1, 2, \cdots
$$
则称函数项级数$\sum u_n(x)$在$D$上*一致收敛*

由此知函数项级数
$$
\sum \frac{\sin nx}{n^2},\; \sum \frac{\cos nx}{n^2}
$$

在$\mathbb R$上一致收敛

Werierstrass 判别法也称为*M判别法*或者*优先级数判别法*. 若满足上述条件，则称级数$\sum M_n$在$D$上*优先于*级数$\sum u_n(x)$, 或称前者为后者的*优级数*

#### Abel 判别法
  充分条件：
  - $\sum u_n(x)$在区间$I$上一致收敛
  - 对于每一个$x \in I$, $\{v_n(x)\}$是单调的
  - $\{v_n(x)\}$在$I$上*一致有界*，即存在正数$M$，使得$\forall x \in I, n \in \mathbb N^*$有$|v_n(x)|  < M$
  
#### Dirichlet 判别法
充分条件
- $\sum u_n(x)$的部分和函数列在$I$上一致有界
- 对于每一个$x\in I$, $\{v_n(x)\}$是单调的
- 在$I$上$v_n(x) \rightrightarrows 0 \; (n \to \infty)$


# 具体讨论：什么是一致收敛
## 单点收敛
$$
\lim_{n \to \infty} S_n(x_0) = S(x_0)
$$
本质上就是普通的数项级数收敛
## 逐点收敛
对$\forall x \in D$
$$
\lim_{n \to \infty} S_n(x) = S(x)
$$
## 一致收敛
对$\forall \varepsilon > 0 ,\; \exists N(\varepsilon) \in \mathbb{N}^* \text{ s.t.} \forall x \in I,\; n > N \implies$
$$
|R_n(x)| = |S_n(x) - S(x)| < \varepsilon
$$
这等价于
$$
\lim_{n \to \infty} \sup_{x \in I} |R_n(x)| = 0
$$
![[数学分析-一致收敛.webp]]
例子:
- 逐点收敛 - $S_n(1), S_n(2), S_n(3)$通过不同的趋势、速度趋向$S(1),S(2),S(3)$
- 一致收敛 - $S_n(1), S_n(2), S_n(3)$通过相同的趋势、速度趋向$S(1),S(2),S(3)$

# 一致收敛函数列和函数项级数的性质
## 极限可交换性
$\{f_n(x)\}$一致收敛时
$$
\lim_{x \to x_0} \lim_{n \to \infty} f_n(x) = \lim_{n \to \infty}\lim_{x \to x_0} f_n(x)
$$
### 连续性推论
若函数列$\{f_n\}$在区间$I$上一致收敛，且每一项都连续，则其极限函数$f$也在$I$上连续

因为由极限可交换性，$\displaystyle \forall x_0 \in I, \lim_{x \to x_0}f(x) = \lim_{n \to \infty} f_n(x_0) = f(x_0)$，故得$f$的连续性

由于$f(x)$在$x$上的连续性只和$x$附近的性质有关，故上述推论的条件可弱化为**内闭一致收敛**

## 可积性
若函数列$\{f_n\}$在$[a,b]$上一致收敛，且每一项都连续，则
$$
\int_a^b \lim_{n \to \infty} f_n(x) \mathrm{d} x = \lim_{n \to \infty} \int_a^b f_n(x) \mathrm{d} x
$$
也就是说一致收敛情况下，**积分和求极限的顺序可以互换**

## 可微性
$$
\dfrac{\mathrm{d}}{\mathrm{d} {x}} \left( \lim_{n\to \infty} f_n(x)\right) = \lim_{n \to \infty} \dfrac{\mathrm{d}}{\mathrm{d} {x}}f_n(x)
$$
### 可微性推论
设$x_0 \in I$为$\{f_n\}$的收敛点，且$\{f_n'\}$在$I$上内闭一致收敛，则$f$在$I$上可导，且
$$
f'(x) = \lim_{n \to \infty} f_n'(x)
$$
## 连续性
若函数项级数$\sum u_n(x)$在区间$[a,b]$上一致收敛，且每一项都连续，则其和函数在$[a,b]$上连续

也就是说，在一致收敛的情况下，无限项求和和求极限可以互换
$$
\sum \left( \lim_{x \to x_0} u_n(x) \right) = \lim_{x \to x_0}\left( \sum u_n(x)\right)
$$
## 逐项求积
$$
\sum \int_a^b u_n(x) \mathrm{d} x = \int_a^b \sum u_n(x) \mathrm{d} x
$$
## 逐项求导
$$
\sum \left(\dfrac{\mathrm{d}}{\mathrm{d} {x}} u_n(x)\right) = \dfrac{\mathrm{d}}{\mathrm{d} {x}}\left(\sum u_n(x)\right)
$$
 

 


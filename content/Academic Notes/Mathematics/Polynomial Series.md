# 级数的收敛性
给定一个数列$\{u_n\}$, *数项级数*记为$\displaystyle \sum_{n = 1}^{\infty} u_n$, 并且记其前$n$项之和为$\displaystyle S_n = \sum_{k = 1}^n u_k$
若某数项级数的部分和数列$\{S_n\}$收敛于一个数$S$, 则称该数项级数*收敛*，并称$S$为该*数项级数的和*, 反之则称该数项级数*发散*

## 常见的数项级数
### 等比级数（几何级数）
$$
a + aq + aq^2 + \cdots
$$
在$\left|{q}\right| < 1$时收敛，$\left|{q}\right| \ge 1$时发散
### 裂项数列
$$
\sum_{n = 1}^{\infty} \dfrac{1}{n(n + 1)(n + 2)} \\
$$
$$
\sum_{n = 1}^{\infty} \dfrac{an+b}{q^n}
$$
### 调和级数
$$
1 + \frac{1}{2} + \frac{1}{3} + \cdots
$$
是发散的，因为
$$
\begin{aligned}
1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \cdots &\ge 1 +\left(\frac{1}{2} \right) + \left( \frac{1}{4} + \frac{1}{4} \right) + \left( \frac{1}{8} + \frac{1}{8} + \frac{1}{8} + \frac{1}{8}\right) + \cdots \\
&= 1 + \frac{1}{2} + \frac{1}{2} + \frac{1}{2} + \cdots \to +\infty
\end{aligned}
$$
## 级数收敛的Cauchy准则
级数收敛的充要条件是：对$\forall \varepsilon > 0, \exists N \in \mathbb{N}^* \text{ s.t. } \forall p \in \mathbb{N}^*, m > N \implies$
$$
\left|{u_{m + 1} + u_{m+2} + \cdots + u_{m+p}}\right| < \varepsilon
$$

由此可以直接给出级数发散的充要条件：$\exists \varepsilon_0 , \forall N \in \mathbb{N}^*$总存在$m_0 > N, p_0 \in \mathbb{N}^*$有
$$
\left|{u_{m_0 + 1} + u_{m_0 + 2} + \cdots + u_{m_0 + p_0}}\right| \ge \varepsilon_0
$$
**推论**：若级数收敛，则有
$$
\lim_{n \to \infty} u_n = 0
$$
需要注意**其逆命题不成立**



**例子**
$\displaystyle \sum_{n = 1}^{\infty} \dfrac{1}{n^2}$收敛，因为
$$
\begin{aligned}
\left|{u_{m + 1} + u_{m+2} + \cdots + u_{m+p}}\right| &= \frac{1}{(m + 1)^2} + \frac{1}{(m + 2)^2} + \cdots + \frac{1}{(m + p)^2} \\
&\le \frac{1}{m(m + 1)} + \frac{1}{(m + 1)(m + 2)} + \cdots + \frac{1}{(m + p - 1)(m + p)} \\
&= \frac{1}{m} - \frac{1}{m + p} < \frac{1}{m}
\end{aligned}
$$
故只需使$m > \dfrac{1}{\varepsilon}$, 取$N = \dfrac{1}{\varepsilon}$即可

$\displaystyle \sum_{n = 1}^{\infty} \frac{(-1)^{n - 1}}{n}$ 收敛，因为(不妨设$p$为偶数)
$$
\begin{aligned}
\left|{u_{m + 1} + u_{m+2} + \cdots + u_{m+p}}\right| &= \left|{\frac{1}{m + 1} - \frac{1}{m + 2} + \frac{1}{m + 3} - \cdots + \frac{(-1)^{p-1}}{m + p}}\right| \\
&= \frac{1}{m + 1}  -(\frac{1}{m + 2} -\frac{1}{m + 3}) - (\cdots) -\cdots -\frac{1}{m + p} \\
&\le \frac{1}{m + 1}
\end{aligned}
$$

## 收敛级数的线性
若级数$\sum u_n$和$\sum v_n$都收敛，则对任意常数$c, d$, 级数$\sum (cu_n + dv_n)$都收敛，且
$$
\sum (cu_n + dv_n) = c\sum u_n + d\sum v_n
$$
## 有限更改敛散不变性
去掉、增加和改变级数的有限个项不改变级数的敛散性
## 改变运算次序敛散不变性
在*收敛级数*的项中任意加括号（改变加法的运算次序），**既不改变级数的收敛性，也不改变级数的和**
**例子**
$$
\begin{aligned}
&\frac{1}{\sqrt{2} - 1} - \frac{1}{\sqrt{2} + 1} + \frac{1}{\sqrt{3} - 1} - \frac{1}{\sqrt{3} + 1} + \frac{1}{\sqrt{4} - 1} - \frac{1}{\sqrt{4} + 1} + \cdots \\
&= \left ( \frac{1}{\sqrt{2} - 1} - \frac{1}{\sqrt{2} + 1}\right) + \left ( \frac{1}{\sqrt{3} - 1} - \frac{1}{\sqrt{3} + 1}\right) + \left ( \frac{1}{\sqrt{4} - 1} - \frac{1}{\sqrt{4} + 1}\right) + \cdots \\
&= \frac{2}{2 - 1} + \frac{2}{3 - 1} + \frac{2}{4 - 1} + \cdots \\
&= 2\left(1 + \frac{1}{2} + \frac{1}{3} + \cdots \right)
\end{aligned}
$$
是发散的
**注**：只有收敛级数加括号后还是收敛级数，故不能通过加括号后的级数收敛推出原级数的收敛性，如
$$
(1 - 1) + (1 - 1) + (1 - 1) + \cdots = 0 + 0 + 0 + \cdots = 0
$$
收敛，但是级数
$$
1 - 1 + 1 -1 + 1 - 1 + \cdots
$$
发散
# 正项级数
## 一般判别原则
若数项级数各项的符号都相同，则称它为*同号级数*。对于同号级数，只需研究各项都是由非负数组成的级数，称为*正项级数*。
**注**：事实上$u_n = 0$的项不影响级数的散敛性，故在判别正项级数散敛性时自然可以排除
### 充要条件
正项级数$\sum u_n$收敛的充要条件是：部分和数列$\{S_n\}$有界
### 比较原则
设$\sum u_n, \sum v_n$是两个正项级数，若$\exists N \in \mathbb{N}^*, \forall n > N \implies u_n \le v_n$, 则
- $\sum v_n$收敛$\implies \sum u_n$收敛
- $\sum u_n$发散$\implies \sum v_n$发散
**证明**：需要注意到改变级数的有限项不影响原级数的散敛性，故可设$u_n \le v_n$对所有项均成立

可以通过比较原则实现将难以判断敛散性的级数放缩为容易判断敛散性的级数

**推论**：
设$\sum u_n, \sum v_n$是两个正项级数，若
$$
\lim_{n \to \infty} \dfrac{u_n}{v_n} = l
$$
则
1. $0 < l < +\infty \implies$两个级数同时收敛或发散
2. $l = 0$且$\sum v_n$收敛 $\implies$ $\sum u_n$收敛
3. $l = +\infty$且$\sum v_n$发散$\implies$ $\sum u_n$发散
对1的证明：
由定义$\forall \varepsilon > 0, \exists N \in \mathbb{N}^*, n>N \implies \displaystyle \left|{\dfrac{u_n}{v_n} - l}\right| < \varepsilon \implies (l - \varepsilon)v_n < u_n < (l + \varepsilon)v_n$
这是两级数同散敛性时的常见形式

**推论应用**：
$$
\left( \lim_{n \to \infty} \dfrac{\dfrac{1}{2^n - n}}{\dfrac{1}{2^n}} = \lim_{n \to \infty} \dfrac{2^n}{2^n - n} = 1 \right) \land \left( \sum\dfrac{1}{2^n} \text{ 收敛}\right) \implies \sum \dfrac{1}{2^n - n} \text{ 收敛}
$$
$$
\lim_{n \to \infty} \dfrac{\sin \dfrac{1}{n}}{\dfrac{1}{n}} = 1 \implies \sum \sin \dfrac{1}{n} \text{ 发散}
$$
## 比式判别法
设$\sum u_n$为正项级数，且存在某正整数$N_0$及常数$q:0<q<1$
1. $\forall n > N_0, \dfrac{u_{n +1 }}{u_n} \le q \implies \sum u_n \text{ 收敛}$
2. $\forall n > N_0, \dfrac{u_{n +1 }}{u_n} \ge 1 \implies \sum u_n \text{ 发散}$
**推论（极限形式）**
若$\sum u_n$为正项级数且$\displaystyle \lim_{n \to \infty} \dfrac{u_{n + 1}}{u_n} = q$, 则
1. $q < 1 \implies \sum u_n \text{ 收敛}$
2. $(q > 1) \vee (q = +\infty) \implies \sum u_n \text{ 发散}$
特别地，当$q = 1$时无法判断
## 根式判别法
设$\sum u_n$为正项级数, 且存在某正整数$N_0$及正常数$l$
1. $\forall n > N_0, \sqrt[n]{u_n} \le l < 1 \implies \sum u_n \text{ 收敛}$
2. $\forall n > N_0, \sqrt[n]{u_n} \ge 1 \implies \sum u_n \text{ 发散}$
**推论（极限形式）**
设$\sum u_n$为正项级数且$\displaystyle \lim_{n \to \infty} \sqrt[n]{u_n} = l$, 则
1. $l < 1 \implies \sum u_n \text{ 收敛}$
2. $l > 1 \implies \sum u_n \text{ 发散}$
## 积分判别法
设$f$为$[1, +\infty)$上的减函数，则级数$\sum f(n)$收敛的充要条件是反常积分$\displaystyle \int_1^{+\infty} f(x) \mathrm{d} x$收敛
**欧拉常数**
$$
\alpha = \lim_{n \to \infty} \left[ 1 + \frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n} - \ln(1+n) \right]
$$
收敛
# 一般项级数
## 交错级数
若级数的各项符号正负相间，即
$$
u_1 - u_2 + u_3 - u_4 + \cdots + (-1)^{n + 1} u_n + \cdots \; (u_n > 0)
$$
则称其为*交错级数*
### Leibniz 判别法
交错级数满足以下两个条件就收敛
1. 数列${u_n}$单调递减
2. $\displaystyle \lim_{n \to \infty} u_n = 0$
证明构建$S_{2m - 1}, S_{2m}$参考[[Nested Interval Theorem | 区间套定理]]

若级数满足Leibniz 判别法的条件，那么其余项估计式为
$$
|R_n| = |\sum^{\infty}_{k = 1} (-1)^{k + 1} u_k - S_n |\le u_{n + 1}
$$
## 绝对收敛级数
类似于[[Improper Integrals | 反常积分]] 的定义，若某级数**各项绝对值**组成的级数
$$
|u_1| + |u_2| + \cdots + |u_n| + \cdots
$$
收敛，则称原级数为*绝对收敛级数*. 若原级数收敛而此级数不收敛，则称原级数为*条件收敛级数*

**绝对收敛级数一定收敛**
### 绝对收敛级数的性质
#### 级数的重排
绝对收敛级数重排后得到的新级数也绝对收敛，且不改变和数，也就是说绝对收敛级数中的和运算*满足交换律*
#### 级数的乘积 (Cauchy 定理)
设$\sum u_n$和$\sum v_n$是两个绝对收敛级数，其和分别为$A, B$，则级数$\sum_{i = 1}^{\infty} \sum_{j = 1}^{\infty} u_i v_j$也收敛，其和为$AB$

**例子**: 证明
$$
\begin{aligned}
\dfrac{1}{(1 - r)^2} &= 1 + (r + r) + (r^2 + r^2 + r^2) + \cdots \\
&= 1 + 2r + 3r^2 + \cdots + (n + 1)r^n + \cdots
\end{aligned}
$$

## Abel - Dirichlet 判别法
### Abel 变换
设$\varepsilon_i, v_i$为两组实数，若令
$$
\sigma_k = v_1 + v_2 + \cdots + v_k
$$
则有如下分部求和公式
$$
\sum_{i = 1}^{n} \varepsilon_i v_i = (\varepsilon_1 - \varepsilon_2) \sigma_1 + (\varepsilon_2 - \varepsilon_3)\sigma_2 + \cdots + (\varepsilon_{n - 1} - \varepsilon_n)\sigma_{n - 1} + \varepsilon_n \sigma_n
$$
### Abel 引理
若
1. $\varepsilon_1, \cdots, \varepsilon_n$是单调数组
2. 对$\forall k \in [n]$有$|\sigma_k| \le A$
则有
$$
\left|\sum_{k = 1}^n \varepsilon_k v_k \right| \le 3 \max_{k} \left\{ |\varepsilon_k| \right\} A
$$
证明:
$$
\begin{aligned}
\left|\sum_{k = 1}^n \varepsilon_k v_k \right| &= |(\varepsilon_1 - \varepsilon_2) \sigma_1 + (\varepsilon_2 - \varepsilon_3)\sigma_2 + \cdots + (\varepsilon_{n - 1} - \varepsilon_n)\sigma_{n - 1} + \varepsilon_n \sigma_n| \\
&\le A |(\varepsilon_1 - \varepsilon_2) + (\varepsilon_2 - \varepsilon_3) + \cdots + (\varepsilon_{n - 1} - \varepsilon_n)| + A|\varepsilon_n| \\
&= A|\varepsilon_1 - \varepsilon_n| + A|\varepsilon_n| \\
&\le A(|\varepsilon_1| + 2|\varepsilon_n|) \\
&\le 3 \max_{k} \left\{ |\varepsilon_k| \right\} A
\end{aligned}
$$
### Abel 判别法
若$\{a_n\}$为单调有界数列，且级数$\sum b_n$收敛，则级数$\sum a_nb_n$收敛

### Dirichlet 判别法
若数列$\{a_n\}$单调递减，且$\displaystyle \lim_{n \to \infty} a_n = 0$，又级数$\sum b_n$的部分和数列有界，则级数$\sum a_n b_n$ 收敛
# 判断敛散性技巧
1. 先看$\displaystyle \lim_{n \to \infty} u_n$是否为$0$，若不然，则发散
2. 看看能不能直接求出$S_n$的通项（如一些特殊数列）
3. 


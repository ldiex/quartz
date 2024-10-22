**记号**: 设$D$是[[Integral Domain | 整环]]. 则$D^* = D \backslash \{0\}$ 且$U_D$是$D$中所有可逆元的集合.
# 重数
设$D$是UFD, $a, p \in D^*$是不可约元. 若非负整数$m \text{ s.t. } p^m | a , p^{m + 1} \nmid a$, 则称$m$是$p$在$a$中的*重数(multiplicity)*

这里的$m$是良定义的, 也就是说$m$一定存在且有限

## 不可约分解
设$a \in D^*$和$p_1, \cdots, p_k \in D^*$是两两互不相伴的不可约元, 设$p_1, \cdots, p_k$在$a$中的重数分别是$m_1, \cdots, m_k$, 则$p_1^{m_1} \cdots p_k^{m_k} | a$

## 多项式重根
设$f \in F[x]^*, x - \alpha \in F[x]$. 设$x - \alpha$在$f$中的重数$m$为正, 则称$\alpha$是$f$中的$m$重根. 当$m = 1$时称为*单根*, $m > 1$时称为*重根*

设$f \in F[x] \backslash F$, $\alpha_1, \cdots, \alpha_s \in F$是$f$互不相同的根, 其重数分别是$m_1, \cdots, m_s$. 则
$$
(x - \alpha_1)^{m_1} \cdots (x - \alpha_s)^{m_s} | f
$$
特别地, $m_1 + \cdots + m_s \le \operatorname{deg} (f)$

# UFD中的最大公因子和最小公倍式
设$D$是UFD, $a, b \in D^*$. 则它们的最大公因子和最小公倍式都存在(直接考虑不可约分解式)

设$D$是UFD, $a_1, \cdots, a_m, b \in D^*$, 则
$$
\gcd(a_1b, \cdots, a_mb) = \gcd(a_1, \cdots, a_m)b
$$
# Gauss 引理
## 容度
设$D$是UFD, $f \in D[x]^*$. 设
$$
f =f_n x^n + f_{n - 1}x^{n - 1} + \cdots + f_0, \; f_i \in D
$$
则$\gcd(f_n, f_{n -1}, \cdots, f_0)$称为$f$的*容度(content)*, 记为$\operatorname{cont}(f, x)$
设$f = \operatorname{cont}(f) g$, 其中 $g \in D[x]^*$满足$\operatorname{cont}(g) = 1$. 则称$g$是$f$的*本原部分(primitive part)*, 记为$\operatorname{pp}(f, x)$
设$h \in D[x]^*$. 如果$\operatorname{cont}(h) = 1$, 则称$h$是本原多项式

**引理**: 设$D$是UFD, $f \in D[x]^*$. 再设$a \in D^*, g \in D[x]^*$是本原多项式. 如果$ag = \operatorname{cont}(f)\operatorname{pp}(f)$, 则$a \approx \operatorname{cont}(f), g \approx \operatorname{pp}(f)$
## Gauss 引理
设D是UFD,  $f, g \in D[x]^*$都是本原多项式, 则$fg$也是本原多项式

**推论**: 设D是UFD, $f,g \in D[x]^*$. 则
$$
\operatorname{cont} (fg) \approx \operatorname{cont}(f) \operatorname{cont} (g), \; \operatorname{pp}(fg) \approx \operatorname{pp}(f) \operatorname{pp} (g)
$$

# Eisenstein 不可约性判别法
设$D$是UFD,  $F$是$D$的分式域. 设$f \in F[x]$且$\operatorname{deg}(f) > 0$. 如果$f$不能写成两个$D[x]$中正次数的多项式之积, 则$f$在$F[x]$不可约

例子: $\mathbb{Z}$ 中不可约$\to \mathbb{Q}$中也不可约

设$D$是UFD, $F$是$D$的分式域. 
$$
f =f_n x^n + f_{n - 1}x^{n - 1} + \cdots + f_0
$$
其中$n > 0, f_n, f_{n - 1} \cdots f_0 \in F, f_n \neq 0$. 设$p$是$D$中的不可约元. 如果
$$
p \nmid f_n, p \mid f_{n - 1}, \cdots, p \mid f_0, p^2 \nmid f_0
$$
则$f$在$F[x]$中不可约



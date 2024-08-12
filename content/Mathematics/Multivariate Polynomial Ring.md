# 齐次多项式和齐次分解
## 齐次多项式
每一个单项式的次数相等的多项式是*齐次多项式*
## 齐次分解
对于任意多项式$p$
$$
p = h_d + \cdots + h_2 + h_1 + h_0
$$
其中$h_n$为次数为$n$的齐次多项式
# 对称多项式
利用赋值定理，这里把未定元$x_i$赋值为$x_{\sigma(i)}$，于是我们就可以定义：
设$p \in R[x_1,\cdots, x_n].$ 如果对于任意的$\sigma \in S_n, \phi_\sigma (p) = p$，则称$p$是关于$x_1,\cdots,x_n$的*对称多项式*，这里$\phi_\sigma : R[x_1, \cdots, x_n] \to R[x_1, \cdots, x_n]$满足
$$
\phi_\sigma(x_i) = x_{\sigma(i)},\; i = 1, \cdots, n \text{ and } \phi_\sigma |_R = \phi
$$

# 整环中的最大公因子和最小公倍式
**记号**：设$D$是[[Integral Domain|整环]]. 则$D^* = D \backslash \{0\}$ 且$U_D$是$D$中所有可逆元的集合.
## 整除和相伴

### 整除
设$a \in D^*$和$b \in D$，如果存在$c \in D$使得
$$
b = ca
$$
则称$a$是$b$的*因子*，$b$是$a$的倍式. 则此时，我们称$a$在$D$中整除$b$，记为$a | b$
### 相伴
设$a, b\in D$. 如果存在$u, v \in U_D$ 使得 $ua = vb$, 则称$a,b$在$D$上相伴，记为$a \approx b$
相伴是一个*等价关系*
等价地
$$
a \approx b \iff (a \mid b) \land (b \mid a)
$$

如果$a \approx b$，那么就*无法用整除性质来区分*$a, b$. 特别地，当$D = \mathbb{Z}$时，$U_\mathbb{Z} = \{-1, 1\}$，故在$\mathbb{Z}$上$a \approx b \iff a \pm b$

在多项式中，对于$F[x]$有$U_{F[x]} = F^*$ ,故在$F[x]$中，
$$
f \approx g \iff \exists \alpha, \beta \in F^*, \alpha f = \beta g
$$
## 首一多项式
特别地，当$f \neq 0$时，$f \approx \operatorname{lc}(f)^{-1} f$ ，这里$\operatorname{lc}(f)$表示$f$的首项系数. $\operatorname{lc}(f)^{-1} f$是首项系数为1的多项式，简称*首一多项式(monic polynomial)*，也是多项式$f$的*首一部分*

**推论**：$f \approx g \iff$ $f, g$ 的首一部分相同
## 最大公因子和最小公倍式
通过[[Exgcd - Extended Euclidean Algorithm|exgcd]]算法来计算一元多项式的最大公因子(利用多项式除法)
**定义**：设$f, g \in F[x]$不全为零. 如果$\gcd(f, g) = 1$，则称$f,g$*互素*
**推论**：设$f, g \in F[x]$不全为零，则$f,g$互素当且仅当存在$u,v \in F[x]$使得
$$
uf + vg = 1
$$
类似地，也有
$$
\operatorname{lcm} (f, g) = \dfrac{fg}{\gcd(f,g)}
$$
## 核核分解
设$F$是域，从坐标空间$F^n$到$F^n$的线性映射简称*线性算子*. $\mathcal O$代表$F^n$上的*零算子*, $\mathcal E$是$F^n$上的*恒同算子*. 则五元组$(\operatorname{Hom} (F^n, F^n), +, \mathcal O, \circ, \mathcal E)$是环. 其中$\operatorname{Hom}(F^n,F^n)$表示从坐标空间$F^n$到$F^n$的线性映射组成的集合

考虑映射
$$
\begin{aligned}
\Psi: M_n(F) &\longrightarrow \operatorname{Hom}(F^n,F^n) \\
A &\longrightarrow \phi \coloneqq \mathcal A
\end{aligned}
$$
其中$\mathcal A$是以$A$为矩阵的线性算子. 由矩阵运算的定义可知$\Psi$是环同构
由此，令
$$
F[\mathcal A] = \left\{ \sum_{i = 0}^k f_i \mathcal A^i | k \in \mathbb N, f_i \in F \right\}
$$
则有$\Psi(F[A]) = F[\mathcal A]$. 
又注意到当$A \neq O$时，$F[A]$是$M_n(F)$的交换子环. 再根据赋值定理，对于任意非零线性算子$\mathcal A$, 有环同态
$$
\begin{aligned}
\rho_\mathcal A : F[x] &\longrightarrow F[\mathcal A] \\
f(x) = \sum_{i = 0}^k f_i x^i &\longrightarrow f(\mathcal A) = \sum_{i = 0}^k f_i \mathcal A^i
\end{aligned}
$$
由此引出如下*核核分解定理*
设$\mathcal A \in \operatorname{Hom}(F^n, F^n) \neq \mathcal O, f \in F[t]$且$f(\mathcal A) = \mathcal O$. 再设$f = pq$, 其中$p, q \in F[t], \gcd(p, q) = 1$. 则
$$
\ker (p(\mathcal A)) \oplus \ker(q(\mathcal A)) = F^n
$$
进而
$$
\dim(\ker(p(\mathcal A))) + \dim(\ker(q(\mathcal A))) = n
$$
**证明**：$\gcd(p, q) = 1 \implies \exists u, v\in F[t]$ s.t.
$$
up + vq = 1
$$
于是
$$
u(\mathcal A)p(\mathcal A) + v(\mathcal A)q(\mathcal A) = \mathcal E \tag{$\ast$}
$$
令$\boldsymbol v \in \ker(p(\mathcal A)) \cap \ker(q(\mathcal A))$, 有
$$
\begin{aligned}
(u(\mathcal A)p(\mathcal A) + v(\mathcal A)q(\mathcal A))(\boldsymbol v) &= \mathcal E (\boldsymbol v) \\
\implies
u(\mathcal A)p(\mathcal A)(\boldsymbol v) + v(\mathcal A)q(\mathcal A)(\boldsymbol v) &= \boldsymbol v \\
\implies \boldsymbol 0 &= \boldsymbol v
\end{aligned}
$$
于是有$\ker(p(\mathcal A)) \cap \ker(q(\mathcal A)) = \{\boldsymbol 0\}$
再设$\boldsymbol x \in F^n, \boldsymbol y = u(\mathcal A)p(\mathcal A)(\boldsymbol x),\boldsymbol z = v(\mathcal A)q(\mathcal A)(\boldsymbol x)$, 则$(\ast) \implies \boldsymbol x = \boldsymbol y + \boldsymbol z$
注意到
$$
\begin{aligned}
q(\mathcal A)(\boldsymbol y) &= q(\mathcal A)u(\mathcal A)p(\mathcal A)(\boldsymbol x) \; (\boldsymbol y\text{的定义})\\
&= u(\mathcal A)q(\mathcal A)p(\mathcal A)(\boldsymbol x) \; (F[\mathcal A]\text{是交换环}) \\
&= u(\mathcal A)f(\mathcal A)(\boldsymbol x) \; (f = pq) \\
&= \boldsymbol 0\; (f(\mathcal A) = \mathcal O)
\end{aligned}
$$
故$y \in \ker(q(\mathcal A))$, 同理$z \in \ker(p(\mathcal A))$. 于是
$$
\ker (p(\mathcal A)) \oplus \ker(q(\mathcal A)) = F^n
$$
**推论**： 设$A \in M_n(F), f \in F[t], f(A) = O, f = pq: p,q \in F[t], \gcd(p, q) = 1$则
$$
\operatorname{sol}(p(A)\boldsymbol x = \boldsymbol 0) \oplus \operatorname{sol}(q(A)\boldsymbol x = \boldsymbol 0) = F^n
$$
特别地
$$
\mathrm{rank}(p(A)) + \mathrm{rank}(q(A)) = n
$$
**例子**：设$\operatorname{char}(F) \neq 2, A \in M_n(F)$ 满足$A^2 = E$, 证明
$$
\mathrm{rank}(A + E) + \mathrm{rank}(A - E) = n
$$
其中$\operatorname{char}(F)$表示$F$的[[Characteristic of a Ring|特征]]





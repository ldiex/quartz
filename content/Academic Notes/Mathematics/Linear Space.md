# 线性空间
设$(V,+,\boldsymbol 0)$是交换群, $(F, +, 0, \cdot, 1)$是域, 设数乘
$$
\begin{aligned}
\cdot : F \times V \to V \\
(\alpha, \boldsymbol v) \to \alpha \boldsymbol v
\end{aligned}
$$
满足$\forall \alpha \beta \in F, \boldsymbol v, \boldsymbol u \in V$
- $(\alpha\beta)\boldsymbol v = \alpha(\beta \boldsymbol v)$
- $1\boldsymbol v = \boldsymbol v$
- $(\alpha + \beta)\boldsymbol v = \alpha \boldsymbol v + \beta \boldsymbol v$
- $\alpha(\boldsymbol u + \boldsymbol v) = \alpha \boldsymbol u + \alpha \boldsymbol v$
则称$(V, +, \boldsymbol 0, \text{数乘}, 1)$是域$F$上的*线性空间*或者*向量空间*, 并称$F$为$V$的*基域*
## 坐标空间
设$F$是域, 则$F^n$是$n$维*坐标空间*. 如$\mathbb R^n, \mathbb Z_p^n$
## 矩阵空间
关于矩阵的加法和数乘, $F^{m \times n}$是$F$上的线性空间
## 代数空间
$R$是环（不一定交换）, 设$F \subset R$是$R$的子域, 则$R$是$F$上的线性空间
如$\mathbb C$是$\mathbb R$上的线性空间, $\mathbb R$是$\mathbb Q$上的线性空间, $F[x_1, \cdots, x_n]$是$F$上的线性空间
## 映射空间
令$\operatorname{Map}(S,V)$表示从$S$到$V$的所有映射的集合, 则
$$
(\operatorname{Map}(S,V), +, \boldsymbol 0,\text{数乘},1)
$$
是线性空间. 如$[a,b]$上所有连续函数的集合$C[a,b]$和$\operatorname{Hom}(F^n, F^n)$

## 零和加法逆
设$V$是$F$上的线性空间, 设$\lambda \in F, \boldsymbol v \in V$则
- $\lambda \boldsymbol 0 = \boldsymbol 0$
- $\lambda \boldsymbol v = \boldsymbol 0 \iff (\lambda = 0) \vee (\boldsymbol v = \boldsymbol 0)$
- $(-1)\boldsymbol v = -\boldsymbol v$


# 线性相关性
设$S$是$V$的一个非空子集. 如果$S$中存在一个有限子集是线性相关的. 则称$S$是一个*线性相关集*, 否则称其为*线性无关集*

- 在$\operatorname{Map}(\mathbb R, \mathbb R)$中, $\sin(x)^2, \cos(x)^2, 1$ 是线性相关的

设$f,g$是$(a,b)$上的可微函数, 若它们在$\mathbb R$上线性相关, 则对$\forall x\in(a, b)$
$$
W_2 = \det \begin{pmatrix}
f(x) & g(x) \\ f'(x) & g'(x)
\end{pmatrix} = 0
$$
称为*二阶 Wronskian*
若$f$在$(a,b)$上恒正, 则上述命题的逆命题成立
# 子空间
设$W$是$V$的非空子集. 如果对于任意的$\alpha, \beta \in F ,\; \boldsymbol x, \boldsymbol y \in W$我们有$\alpha \boldsymbol x + \beta \boldsymbol y \in W$, 则称$W$是$V$的*子空间*

每一个子空间都是线性空间

- F上所有$n$阶对称方阵的集合$\operatorname{SM}_n(F)$和所有$n$阶斜对称方阵的集合$\operatorname{SSM}_n(F)$都是$M_n(F)$上的子空间
- $F[x]^{(d)} = \{p \in F[x] | \deg(p) < d\}$是$F[x]$的子空间
- 闭区间$[a,b]$上连续函数的集合$C[a,b]$和连续可微函数的集合$C^1[a,b]$是$\operatorname{Map}([a,b], \mathbb R)$的子空间

线性空间$V$中任意个子空间的交仍然是子空间

## 子空间的直和
设$V_1, \cdots, V_k$是$V$的子空间, $W = V_1 + V_2 + \cdots V_k$, 如果对于任意$\boldsymbol w \in W$都存在唯一的$\boldsymbol v_1 \in V_1, \cdots, \boldsymbol v_k \in V_k$使得
$$
\boldsymbol w = \boldsymbol v_1 + \cdots + \boldsymbol v_k
$$
则称$W$是$V_1, \cdots, V_k$的*直和*, 并记为
$$
W = V_1 \oplus \cdots \oplus V_k
$$
$W$是直和与以下两个命题等价
1. $\boldsymbol 0 = \boldsymbol v_1 + \cdots + \boldsymbol v_k \iff \boldsymbol v_1 = \cdots = \boldsymbol v_k = \boldsymbol 0$
2. $\forall i \in [k], V_i \cap (V_1 + \cdots + V_{i - 1} + V_{i + 1} +\cdots +V_k) = \{\boldsymbol 0\}$
>[!Tip] 注意
>这和$V_i \cap V_j = \left\{ \boldsymbol 0 \right\},\;\forall i,j\in [k]$不等价

**例子**: 对[[Characteristic of a Ring | 特征]] 不为$2$的域$F$, 有
$$
\mathrm{M}_n(F) = \mathrm{SM}_n(F) \oplus \mathrm{SSM}_n(F)
$$
因为
$$
B = \dfrac{1}{2}(A + A^t) \in \mathrm{SM}_n(F) , \quad C = \frac{1}{2} (A - A^t) \in \mathrm{SSM}_n(F)
$$

并对于多项式
$$
P^{(d)} \coloneqq \left\{f \in F[x_1, \cdots,x_n] \mid \deg(f) \le d\right\}
$$
有*齐次加法分解*
$$
P^{(d)} = \bigoplus_{i = 1}^d H_i
$$
## 子空间的生成元
设$S$是$V$的非空子集, 并令
$$
\langle S\rangle:=\left\{\sum_{i=1}^k\alpha_i\mathbf{v}_i|k\in\mathbb{Z}^+,\alpha_i\in F,\mathbf{v}_i\in S\right\}
$$
则$\langle S\rangle$也是$V$的一个子空间




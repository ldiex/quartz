# 送分题
- 坐标变换
- 对称矩阵的类型
- 二次型标准型
- 线性算子的矩阵表示
- 计算最小多项式
## 秩不等式
## 把映射转换为矩阵
## 求逆矩阵的时候**不能**使用初等列变换
# 参考题目
## 坐标变换
> 设$\boldsymbol e_1, \boldsymbol e_2, \boldsymbol e_3$是$\mathbb{R}^3$的标准基，$\boldsymbol u_1 = \boldsymbol e_1 - \boldsymbol e_2, \; \boldsymbol u_2 = \boldsymbol e_1 + \boldsymbol e_2,\; \boldsymbol u_3 = \boldsymbol e_3$
> 1. 计算$P$使得$(\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3) = (\boldsymbol e_1, \boldsymbol e_2, \boldsymbol e_3)P$
> 2. 证明$\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3$是$\mathbb{R}^3$的一组基
> 3. 计算$\boldsymbol v = \begin{pmatrix}1 \\ 1 \\ 1\end{pmatrix}$在$\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3$下的坐标表示

1. 直接写出$P = \begin{pmatrix}1 & 1 & 0 \\ -1 & 1 & 0 \\ 0 & 0 & 1\end{pmatrix}$
2. **因为$P$可逆**，所以$\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3$是$\mathbb{R}^3$的一组基
3. 可以直接代入
$$
\boldsymbol v = \boldsymbol e_1 + \boldsymbol e_2 + \boldsymbol e_3 = \dfrac{\boldsymbol u_1 + \boldsymbol u_2}{2} + \dfrac{\boldsymbol u_2 - \boldsymbol u_1}{2} + \boldsymbol u_3 = \boldsymbol u_2 + \boldsymbol u_3
$$
于是坐标为$\begin{pmatrix}0 \\ 1 \\ 1\end{pmatrix}$
或者利用坐标变换抽象上述过程
$$
\begin{aligned} 
(\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3)  & = (\boldsymbol e_1, \boldsymbol e_2, \boldsymbol e_3)P \\
\implies (\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3) P^{-1}  & = (\boldsymbol e_1, \boldsymbol e_2, \boldsymbol e_3); \\ \\
(\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3) \begin{pmatrix}
y_1 \\ y_2 \\ y_3
\end{pmatrix}  &= (\boldsymbol e_1, \boldsymbol e_2, \boldsymbol e_3) \begin{pmatrix}
x_1 \\ x_2 \\ x_3
\end{pmatrix} \\
\implies (\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3) \begin{pmatrix}
y_1 \\ y_2 \\ y_3
\end{pmatrix}  &= (\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3) P^{-1} \begin{pmatrix}
x_1 \\ x_2 \\ x_3
\end{pmatrix} \\
\implies \begin{pmatrix}
y_1 \\ y_2 \\ y_3
\end{pmatrix}  & = P^{-1} \begin{pmatrix}
x_1 \\ x_3 \\ x_3
\end{pmatrix}
\end{aligned}
$$
**不要直接用计算基底的办法计算坐标**
## 对称矩阵合同对角化
1. 行列相伴消元
2. 配方法（注意一次要把所有关于$x_k$的项都配进去）

## 正定二次型
> 设$\mathbb{R}^3$上的二次型由公式$q(\boldsymbol x) = 2x_1^2 + x_2^2 + 3x_3^3 + 2\lambda x_1x_2+ 2x_1x_3$确定
> 1. 计算$q$在$\mathbb{R}^3$标准基下的矩阵
> 2. 设$q$正定，求$\lambda$的取值范围
> 3. 证明$q$不可能负定

1. 直接写出
$$
A = \begin{pmatrix}
2 & \lambda & 1 \\
\lambda & 1 & 0 \\
1 & 0 & 3
\end{pmatrix}
$$
2. 矩阵$A$的三个[[Matrix Minor#Leading Principal Minor|顺序主子式]]为
$$
\Delta_1 = 2, \quad \Delta_2 = 2 -\lambda^2, \quad \Delta_3 = 5 - 3\lambda^2
$$
由[[Real Quadratic Forms#Jacobi公式|Jacobi公式]]只需要使上述三个子式都大于$0$即可
> [!Note] 负定(Negative Definite)的情况
> 如果$A$是负定的，那么$-A$是正定的，考虑到$\det(-A) = (-1)^n \det A$，此时$A$的顺序主子式需要满足$\Delta_1 < 0, \Delta_2 > 0, \Delta_3 < 0, \Delta_4 > 0, \ldots$

> [!Note] 半正定的情况
> 半正定需要不能满秩，需要取$\Delta_n = 0$，然后开始分类讨论
3. 因为$\Delta_1 > 0$所以$q$不可能是负定的

> 设$A$是$n$阶实对称矩阵，$r = \mathrm{rank}(A) > 0$.  则$A$是半正定的当且仅当$\exists B \in \mathbb{R}^{r \times n}$使得$A = B^t B$

若$A = B^t B$，则$\boldsymbol x^t A \boldsymbol x = (B\boldsymbol x )^t (B \boldsymbol x) \ge 0$，故$A$半正定
若$A$半正定，则存在$P \in \mathrm{GL}_n(\mathbb{R})$使得
$$
A = P^t \begin{pmatrix}
E_r & O \\
O & O
\end{pmatrix} P = \boxed{P^t \begin{pmatrix}
E_r \\
O
\end{pmatrix} \begin{pmatrix}
E_r & O
\end{pmatrix} P} = \left[ \begin{pmatrix}
E_r & O
\end{pmatrix} P \right] ^t \left[ \begin{pmatrix}
E_r & O
\end{pmatrix} P \right] 
$$

> 设$V$是$\mathbb{R}$上的$2n$维线性空间，$q$是$V$上的二次型且$\mathrm{rank}(q) = 2n$，则以下三个结论等价
> 1. 存在一个$n$维子空间$U \subset V$使得对任意$\boldsymbol u \in U, \; q(\boldsymbol u) = 0$
> 2. $q$的正惯性指数为$n$
> 3. 存在$V$的某组基$\boldsymbol \varepsilon_1, \ldots, \boldsymbol \varepsilon_{2n}$使得对任意的$\boldsymbol x = x_1 \boldsymbol \varepsilon_1 + \cdots + x_{2n}\boldsymbol \varepsilon_{2n} \in V$，有
> $\displaystyle q(\boldsymbol x) = \sum_{i = 1}^n x_{2i-1}x_{2i}$

$1. \implies 2.$ 设$q$的正惯性系数为$m$，则存在一组基$\boldsymbol \varepsilon_1, \ldots, \boldsymbol \varepsilon_{2n}$使得$q$有如下的规范型
$$
q = x_1^2 + \cdots x_m^2 - x_{m + 1}^2 - \cdots - x_{2n}^2
$$
若$n < m$则所取的$U \subset \ker(q)$至少包含$\boldsymbol \varepsilon_1, \ldots, \boldsymbol \varepsilon_m$之中的某一个基底$\boldsymbol \varepsilon _k$，而这和$q(\boldsymbol \varepsilon_k) > 0$矛盾

若$n > m$则所取的$U \subset \ker(q)$至少包含$\boldsymbol \varepsilon_{m + 1}, \ldots, \boldsymbol \varepsilon_{2n}$之中的某一个基底$\boldsymbol \varepsilon _k$，而这和$q(\boldsymbol \varepsilon_k) < 0$矛盾

故$n = m$

$2. \implies 3.$ 也就是恒等式
$$
\begin{aligned}
&x_1^2 + \cdots +x_n^2 - x_{n + 1}^2 - \cdots - x_{2n}^2  \\
= &(x_1 + x_{n + 1})(x_1 - x_{n +1}) + (x_2 + x_{n + 2})(x_2 - x_{n + 2}) + \cdots + (x_n + x_{2n})(x_n - x_{2n}) \\
\end{aligned}
$$
**且这个变量替换是可逆的**
$3. \implies 1.$ 做完变量替换后，在基底$\boldsymbol \var_1, \ldots, \boldsymbol \var_{2n}$下有
$$
q(\boldsymbol y) = y_1 y_2 + \cdots y_{2n-1}y_{2n}
$$
考虑$U = \langle\boldsymbol \var_1, \boldsymbol \var_3 \ldots, \boldsymbol \var_{2n - 1}\rangle$，则对$\forall \boldsymbol y \in U$有$y_2 = y_4 = \cdots = y_{2n} = 0$故有$q(\boldsymbol y) = 0$

> 设$A\in \mathrm{SM}_n(\mathbb{R})$是正定矩阵，则
> 1. $A^{-1}$正定
> 2. $A^\vee$正定

1. 设$A = P^tP, \; P \in \mathrm{GL}_ n(\mathbb{R})$. 则$A^{-1} = P^{-1}(P^t)^{-1}$ = $P^{-1}(P^t)^{-1} = P^{-1}(P^{-1})^t$，故$A^{-1}$正定
2. $A^\vee = \det(A) A^{-1} = \left( \sqrt{ \det(A) }P^{-1} \right) \left( \sqrt{ \det(A) }P^{-1} \right)^t$, 故$A^\vee$正定
> 设$A,B$是半正定的，则$\mathrm{rank}(A + B) \ge \max(\mathrm{rank}(A), \mathrm{rank}(B))$

因为$\boldsymbol x^t(A + B) \boldsymbol x = \boldsymbol x^t A \boldsymbol x + \boldsymbol x^T B \boldsymbol x \ge 0$，所以$A + B$是半正定的。故存在$P,Q,R\in \mathrm{M}_n(\mathbb{R})$使得$A = P^tP, B = Q^tQ, A+B = R^tR$, 且设$s = \mathrm{rank}(A+B) = \mathrm{rank}(R)$，并不妨令$r = \mathrm{rank}(P) = \mathrm{rank}(A)> \mathrm{rank}(Q) = \mathrm{rank}(B)$，只需要证明$s \ge r$，为此只需要证明$V_R \subset V_P$. 设$\boldsymbol v\in V_R$也就是$R\boldsymbol v  = \boldsymbol 0$，故有
$$
\boldsymbol v^t (A + B)\boldsymbol v = 0 \implies \boldsymbol v^t A \boldsymbol v + \boldsymbol v^t B \boldsymbol v = 0 \implies \boldsymbol v^t A \boldsymbol v = \boldsymbol v^t B \boldsymbol v = 0
$$
于是$\boldsymbol v^t P^tP \boldsymbol v = 0 \implies P\boldsymbol v = \boldsymbol 0$，即$V_R \subset V_P$

> [!Tip] 对$\mathrm{rank}(R^tR) = \mathrm{rank}(R)$的证明
> 因为矩阵乘法不增大秩，故$\mathrm{rank}(R^tR) \le \mathrm{rank}(R)$
> 又因为$V_{R^tR} \subset V_{R}$，故$\dim(\ker(R)) \ge \dim(\ker(R^tR))$，于是$\mathrm{rank}(R) \le \mathrm{rank}(R^tR)$
> 综上$\mathrm{rank}(R^tR) = \mathrm{rank}(R)$
## 二次型的性质
> 设$V$是$\mathbb{R}$上的有限维线性空间，$U$是$V$的子空间，$q$是$V$上的二次型，则
> 1. $q|_U$也是二次型
> 2. 设$q$的签名为$(k,l)$, $q|_U$的签名为$(s, t)$. 证明$k \ge s, l\ge t$

1. 设$f(\boldsymbol x, \boldsymbol y)$是$q$的配极，则$f|_{U\times U}$是$q|_U$的配极，故$q|_U$是$U$上的二次型
2. 存在$V$的一组基$\boldsymbol e_1, \ldots, \boldsymbol e_n$使得对任意$x = x_1\boldsymbol e_1 + \cdots + x_n \boldsymbol e_n$有
$$
q(\boldsymbol x) = x_1^2 + \cdots x_k^2 - x_{k + 1}^2 - x_{k + l}^2
$$
和$U$的一组基$\boldsymbol \varepsilon_1, \ldots, \boldsymbol \varepsilon_d$使得对任意$\boldsymbol y = y_1 \boldsymbol\varepsilon_1 + \cdots + y_d \boldsymbol \varepsilon_d$有
$$
q|_U (\boldsymbol y) = y_1^2 + \cdots + y_s^2 - y_{s + 1}^2 - \cdots - y_{s + t}^2
$$
假设$s > k$，令
$$
H = \langle\boldsymbol \varepsilon_1, \ldots, \boldsymbol \varepsilon_s\rangle, \; W = \langle\boldsymbol e_{k + 1}, \ldots, \boldsymbol e_n\rangle
$$
则$\dim(H) =  s$且$\dim(W) = n - k > n  - s$. 故存在非零向量$\boldsymbol z \in H \cap W$满足$q|_U(\boldsymbol z) > 0$且$q(\boldsymbol z) \le 0$，矛盾！
同理分析$-q$和$-q|_U$，我们可以得到$t \le l$

## 二次型的判定
### 第一种
设$q: V \to F$是$V$上的二次型，如果
1. 对于$\forall \boldsymbol v \in V,\; q (\boldsymbol v) = q(- \boldsymbol v)$
2. 对于$\forall \boldsymbol x, \boldsymbol y \in V$
$$
f(\boldsymbol x, \boldsymbol y) = \dfrac{1}{2}(q(\boldsymbol x + \boldsymbol y) - q(\boldsymbol x) - q(\boldsymbol y)) 
$$
是$V$上的[[Bilinear Form#对称双线性型 | 对称双线性型]] (关键是双线性型，显然是对称的), $f$称为$q$的*配极*，或者叫做*相伴双线性型*(*associated bilinear form*)
### 第二种
设$q: V \to F$. 则$q$是二次型当且仅当存在$f \in \mathcal L_2^+(V)$使得$\forall \boldsymbol x \in V, \; q(\boldsymbol x) = f(\boldsymbol x, \boldsymbol x)$. 此时$q$的配极是$f$

## 线性算子的矩阵及其秩
如定义在$F[x]^{(3)}$上的差分算子
$$
\begin{aligned}
\Delta: F[x]^{(3)}  & \to F[x]^{(3)}  \\
f(x)  & \to f(x + 1) - f(x)
\end{aligned}
$$
符合线性算子的[[Linear Operator#定义|定义]]
起在$1,x,x^2$下的矩阵为
$$
\begin{pmatrix}
0 & 1 & 1 \\
0 & 0 & 2 \\
0 & 0 & 0 
\end{pmatrix}
$$
**当需要计算秩时，需要考虑$F$的[[Characteristic of a Ring|特征]]是否等于$2$，如果是，则秩为$1$，否则秩为$2$**

## 线性映射的单满射性质
一个线性映射$\phi: V \to W$是单射当且仅当$\ker(\phi) = \{\boldsymbol 0\}$
一个线性映射$\phi: V \to W$是满射当且仅当$\mathrm{im}(\phi) = W$
如果$\dim(V) = \dim(W)$，则$\phi$是单射当且仅当$\phi$是满射

## 构造线性算子
> 设$V$是域$F$上的有限维线性空间，$U, W$是$V$的子空间且满足$U \oplus W = V$，那么
> 1. 存在$\mathcal A \in \mathcal{L}(V)$使得$U = \mathrm{im}(\mathcal A)$
> 2. 存在$\mathcal B \in \mathcal{L}(V)$使得$U = \ker (\mathcal B), W = \mathrm{im}(\mathcal B)$

1. 设$\boldsymbol e_1, \ldots, \boldsymbol e_d$是$U$的基底，把它扩充为$V$的一组基底$\boldsymbol e_1, \ldots, \boldsymbol e_d, \boldsymbol e_{d + 1}, \ldots, \boldsymbol e_{n}$，令
$$
\mathcal A(\boldsymbol e_i) = 
\begin{cases}
\boldsymbol e_i,  &  i = 1, 2, \ldots, d \\
\boldsymbol 0,  & i = d+1 ,\ldots, n
\end{cases}
$$
即可
2. 类似地，令
$$
\mathcal A(\boldsymbol e_i) = 
\begin{cases}
\boldsymbol e_i,  &  \boldsymbol e_i \text{ is the basis of } W \\
\boldsymbol 0,  & \boldsymbol e_i \text{ is the basis of } U
\end{cases}
$$
即可

## 直和的条件
设$V_1, \cdots, V_k$是$V$的子空间，$W = V_1 + V_2 + \cdots V_k$, 如果对于任意$\boldsymbol w \in W$都存在唯一的$\boldsymbol v_1 \in V_1, \cdots, \boldsymbol v_k \in V_k$使得
$$
\boldsymbol w = \boldsymbol v_1 + \cdots + \boldsymbol v_k
$$
则称$W$是$V_1, \cdots, V_k$的*直和*，并记为
$$
W = V_1 \oplus \cdots \oplus V_k
$$
$W$是直和与以下两个命题等价
1. $\boldsymbol 0 = \boldsymbol v_1 + \cdots + \boldsymbol v_k \iff \boldsymbol v_1 = \cdots = \boldsymbol v_k = \boldsymbol 0$
2. $\forall i \in [k], V_i \cap (V_1 + \cdots + V_{i - 1} + V_{i + 1} +\cdots +V_k) = \{\boldsymbol 0\}$
## 最小公倍式
> 设$F$是域，$f,g \in F[x]$是非零多项式，$m = \deg(f), n = \deg(g)$. 令$\ell$是$f$和$g$的最小公倍式和
> $$V = \left\{ p \in F[x] \mid \deg(p) \le m + n \right\} $$
> 设$U$是$V$中$f,g$所有公倍式的集合，证明$\dim(U) = m + n - d + 1$，其中$d = \deg(\ell)$

**直接构造基底**
注意到$\ell, x\ell, \ldots, x^{m + n - d}\ell \in U$. 因为这些多项式次数两两不同，所以它们线性无关。设$h \in U$，则存在$q\in F[x]$使得$h = q \ell$. 因为$\deg(h) \le m+ n$，故$\deg(q) \le m + n - d$，于是
$$
q = q_{m + n - d}x^{m + n - d} + \cdots + q_1 x + q_0
$$
则
$$
h =  q_{m + n - d}(x^{m + n - d} \ell)+ \cdots + q_1 (x\ell) + q_0 \ell
$$
故$h$是$\ell, x\ell, \ldots, x^{m + n - d}\ell$在$F$上的线性组合，由此可知上述多项式是$U$的基底，所以$\dim(U) = m + n - d + 1$

**另解（对偶定理）**：考虑线性映射
$$
\begin{aligned}
\phi: V  & \to V  \\
p  & \to \mathrm{rem}(p, \ell)
\end{aligned}
$$
注意到$\ker(\phi) = \{h \in V \mid \exists q \in F[x] \text{ s.t. } h = q\ell\} = U$, 而$\mathrm{im}(\phi) = F[x]^{(d)}$
于是有
$$
\dim(U) + d = \dim(V) \implies \dim(U) = m + n + 1 - d
$$
## 对偶空间
> 设$V$是域$F$上的有限维线性空间，$\mathrm{char}(F) \neq 2$. 设$f, g\in V^*\backslash\left\{ \boldsymbol 0^* \right\}$，令
> $$\begin{aligned}q: V  & \to F \\\boldsymbol x  & \to f(\boldsymbol x)g(\boldsymbol x)\end{aligned}$$> 则
> 1. $q$是$V$上的二次型
> 2. $\mathrm{rank}(q) = \dim \langle f, g\rangle$

1. 设
$$
\phi(\boldsymbol x, \boldsymbol y) = \dfrac{1}{2} (f(\boldsymbol x)g(\boldsymbol y)+ f(\boldsymbol y)g(\boldsymbol x))
$$
是对称双线性型且$\phi(\boldsymbol x, \boldsymbol x) = q(\boldsymbol x)$, 故$q$是二次型

2. 设$\boldsymbol e_1, \ldots, \boldsymbol e_n$是$V$的一组基，$\alpha_i = f(\boldsymbol e_i), \beta_j = g(\boldsymbol e_j)$ 则$q$在该基底下的矩阵是
$$
A=(\phi(\boldsymbol{e}_i,\boldsymbol{e}_j))_{n\times n}=\left(\frac{\alpha_i\beta_j+\alpha_j\beta_i}{2}\right)_{n\times n}=\frac{1}{2}(\begin{pmatrix}\alpha_1\\\vdots\\\alpha_n\end{pmatrix}(\beta_1,\dots,\beta_n)+\begin{pmatrix}\beta_1\\\vdots\\\beta_n\end{pmatrix}(\alpha_1,\dots,\alpha_n))
$$
由此可知$\mathrm{rank}(A) \le 1 + 1 = 2$

如果$\dim \langle f,g\rangle = 1$, 则存在$\lambda \in F \backslash\left\{ 0 \right\}$使得$g = \lambda f$, 于是
$$
A = \lambda(\alpha_i \alpha_j)_{n \times n} = \lambda \begin{pmatrix}
\alpha_1 \\ \vdots \\ \alpha_n
\end{pmatrix} (\alpha_1, \ldots, \alpha_n)
$$
故$\mathrm{rank}(A) = 1$

如果$\dim \langle f, g \rangle = 2$, 则$(\alpha_1, \ldots, \alpha_n)$和$(\beta_1, \ldots, \beta_n)$不线性相关，故矩阵
$$
\begin{pmatrix}
\alpha_1 & \cdots & \alpha_n \\
\beta_1 & \cdots  & \beta_n 
\end{pmatrix}
$$
中的一个二阶子式非零，不妨设
$$
\det \begin{pmatrix}
\alpha_1 & \alpha_2  \\
\beta_1 & \beta_2
\end{pmatrix} \neq 0
$$
则$A$中的二阶子式
$$
\det \begin{pmatrix}
\alpha_1\beta_1 & \dfrac{\alpha_1\beta_2 + \alpha_2\beta_1}{2}  \\
\dfrac{\alpha_1\beta_2 + \alpha_2 \beta_1}{2} & \beta_2\alpha_2
\end{pmatrix}  \neq 0
$$
于是$\mathrm{rank}(A) \ge 2 \implies \mathrm{rank}(A) = 2$

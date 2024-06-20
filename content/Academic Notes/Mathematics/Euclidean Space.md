# $V$上的内积
## 内积的定义
设$f(\boldsymbol x, \boldsymbol y)$是$V$上的[[Bilinear Form#对称双线性型|对称双线性型]]满足$f(\boldsymbol x,\boldsymbol x)$是[[Real Quadratic Forms#（半）正定二次型|正定]]的，则称$(V,f)$是一个*欧式空间*，$f$是$V$上的*内积*
> [!Tip]
> 由于正定性，我们无法在$\mathbb{C}^n$上定义一个内积空间
## 举例
设$V = \mathbb{R}^n$，由上述定义，就有内积$f(\boldsymbol x,\boldsymbol y) =\boldsymbol x ^t \boldsymbol y$满足$f(\boldsymbol x, \boldsymbol x)$是正定的，所以$(\mathbb{R}^n,f)$是欧式空间

设$V = \mathrm{M}_n(\mathbb{R})$，则
$$
\begin{aligned}
f:V\times V & \to \mathbb{R} \\
(X,Y) &\to \mathrm{tr}(X^tY)
\end{aligned}
$$
是内积，因为它满足
- **线性**：$f(\alpha A + \beta B,Y) = \mathrm{tr}((\alpha A+\beta B)^tY)= \alpha f(A,Y),\beta f(B,Y)$，且类似地对第二个变元也成立
- **对称性**：$f(Y,X) = \mathrm{tr}(Y^tX) = \mathrm{tr}(X^tY) = f(X,Y)$
- **正定性**：$f(X,X) = \mathrm{tr}{X^tX}=\displaystyle \sum_{i,j} x_{i,j}^2\ge0$

设$V = \mathbb{R}[x]^{(n)}$, $a,b \in\mathbb{R}$且$a < b$，则
$$
\begin{aligned}
\phi: V \times V  & \to \mathbb{R} \\
(f,g)  & \to \int_a^b f(x) g(x) \mathrm{d}x
\end{aligned}
$$
是$V$的内积

## Dirac符号
我们利用Dirac符号，把欧式空间$V$上的内积记为$\vert$ ,即
$$
\begin{aligned}
(\vert): V \times V &\to \mathbb{R} \\
(\boldsymbol x, \boldsymbol y) &\to(\boldsymbol x \vert \boldsymbol y)
\end{aligned}
$$
利用这个符号，内积的基本性质如下
- **双线性**：对任意的$\boldsymbol x, \boldsymbol y, \boldsymbol x \in V,\;\alpha,\beta \in \mathbb{R}$,
$$
(\alpha \boldsymbol x + \beta \boldsymbol y \vert \boldsymbol z) = \alpha(\boldsymbol x \vert \boldsymbol z) + \beta(\boldsymbol y \vert \boldsymbol z),\;(\boldsymbol x \vert \alpha \boldsymbol y + \beta \boldsymbol z) = \alpha(\boldsymbol x \vert \boldsymbol y) + \beta (\boldsymbol x \vert \boldsymbol z)
$$
- **对称性**：对任意$\boldsymbol x, \boldsymbol y \in V,\;(\boldsymbol x \vert \boldsymbol y) = (\boldsymbol y \vert \boldsymbol x)$
- **正定性**：对任意$\boldsymbol x \in V$
$$
(\boldsymbol x \vert \boldsymbol x) \geq 0 \text{ 且 } (\boldsymbol x \vert \boldsymbol x) = 0 \iff \boldsymbol x = \boldsymbol 0
$$
## Gram矩阵
设$V$是欧式空间，$\boldsymbol v_1, \ldots \boldsymbol v_m \in V$，定义
$$
G(\boldsymbol v_1,\ldots \boldsymbol v_m) = ((\boldsymbol v_i \vert \boldsymbol v_j))_{m \times m}
$$
称之为$\boldsymbol v_1,\ldots \boldsymbol v_m$的*Gram矩阵*

由内积的对称性可知**Gram矩阵是对称的**

由定义，若$\boldsymbol v_1,\ldots \boldsymbol v_m \in V,\;\alpha_1,\ldots\alpha_m,\; \beta_1,\ldots,\beta_m \in \mathbb{R}$，令
$$
\boldsymbol x = \alpha_1 \boldsymbol v_1 + \cdots + \alpha_m \boldsymbol v_m,\; \boldsymbol y = \beta_1 \boldsymbol v_1 + \cdots + \beta_m \boldsymbol v_m
$$
则有
$$
(\boldsymbol x \vert \boldsymbol y) = (\alpha_1,\ldots,\alpha_m)G(\boldsymbol v_1, \ldots,\boldsymbol v_m) \begin{pmatrix}
\beta_1 \\
\vdots \\
\beta_m
\end{pmatrix}
$$
若$V$是欧式空间，$\boldsymbol v_1,\ldots,\boldsymbol v_m \in V$. 则$\boldsymbol v_1,\ldots, \boldsymbol v_m$线性相关当且仅当$\mathrm{rank}(G(\boldsymbol v_1,\ldots,\boldsymbol v_m))< m$

进一步，我们可以知道$G(\boldsymbol v_1,\ldots \boldsymbol v_m)$是半正定的，它是正定的当且仅当$\boldsymbol v_1,\ldots,\boldsymbol v_m$线性无关

> [!Tip]
> Gram矩阵可以把向量的内积转化为基底的内积
# 长度、距离、角度和正交
## 长度和距离
设$V$是欧式空间，$\boldsymbol x \in V$. 称$\sqrt{ (\boldsymbol x \vert \boldsymbol x) }$是$\boldsymbol x$的*长度*（或称为*范数*），记为$\Vert \boldsymbol x \Vert$. 再设$\boldsymbol y \in V$. 则$\left\Vert \boldsymbol x - \boldsymbol y \right\Vert$称为$\boldsymbol x$到$\boldsymbol y$之间的*距离*

## Cauchy-Bunyakovsky不等式
设$\boldsymbol x,\boldsymbol y \in V$，则
$$
\left|(\boldsymbol x \vert \boldsymbol y)\right| \leq \Vert \boldsymbol x \Vert \Vert \boldsymbol y \Vert  
$$
特别地$\left|(\boldsymbol x \vert \boldsymbol y)\right| = \Vert \boldsymbol x \Vert \Vert \boldsymbol y \Vert$当且仅当$\boldsymbol x, \boldsymbol y$线性相关

在$\mathbb{R}^n$上，该不等式的形式是
$$
\left|x_1y_1+ \cdots +x_ny_n\right| \leq \sqrt{ x_1^{2}+ \cdots +x_n^{2} }\sqrt{ y_1^{2}+ \cdots +y_n^{2} }
$$
在$\mathrm{M}_n(\mathbb{R})$上，该不等式的形式是
$$
\left|\mathrm{tr}(A^tB)\right|\leq \sqrt{ \mathrm{tr}(A^tA) }\sqrt{ \mathrm{tr}(B^tB) }
$$
在$\mathbb{R}[x]^{(n)}$上，该不等式的形式是
$$
\left|\int_a^b f(x)g(x) \mathrm{d}x\right|\leq \sqrt{ \int_a^bf^{2}(x)\mathrm{d}x }\sqrt{ \int_a^b g^{2}(x) \mathrm{d}x }
$$
设$\boldsymbol x, \boldsymbol y \in V$，且存在$\alpha \in \mathbb{R}$使得$\boldsymbol x = \alpha \boldsymbol y$或者$\boldsymbol y = \alpha \boldsymbol x$，则称$\boldsymbol x, \boldsymbol y$*平行*. 如果$\alpha \geq 0$，则称$\boldsymbol x, \boldsymbol y$*同向*. 如果$\alpha \leq 0$，则称$\boldsymbol x, \boldsymbol y$*反向*，有时候也称$\boldsymbol 0$是*迷向*的

由此，我们得到Cauchy不等式的等价命题*三角不等式*

设$\boldsymbol x, \boldsymbol y \in V$. 则$\Vert \boldsymbol x + \boldsymbol y \Vert \leq \Vert \boldsymbol x \Vert + \Vert \boldsymbol y \Vert$. 等式成立当且仅当$\boldsymbol x, \boldsymbol y$同向

## 夹角
设$\boldsymbol x, \boldsymbol y \in V \backslash \left\{ \boldsymbol 0 \right\}$，称
$$
\arccos \left( \dfrac{(\boldsymbol x \vert \boldsymbol y)}{\Vert \boldsymbol x \Vert \Vert \boldsymbol y \Vert } \right) 
$$
是$\boldsymbol x, \boldsymbol y$的*夹角*，其通常的取值范围为$[0,\pi]$

## 正交
设$\boldsymbol x, \boldsymbol y \in V$. 如果$(\boldsymbol x \vert \boldsymbol y)=0$，则称$\boldsymbol x$和$\boldsymbol y$*正交*，记为$\boldsymbol x \perp \boldsymbol y$

设$\boldsymbol x, \boldsymbol x_1, \ldots ,\boldsymbol x_k \in V$,其中$\boldsymbol x_1 , \ldots , \boldsymbol x_k$非零，则
- $\boldsymbol x \perp \boldsymbol x \iff \boldsymbol x = \boldsymbol 0$
- 如果$\boldsymbol x_1, \ldots ,\boldsymbol x_k$两两正交，则它们线性无关

### 勾股定理
设$\boldsymbol x, \boldsymbol y \in V$，则$\boldsymbol x \perp \boldsymbol y$当且仅当
$$
\Vert \boldsymbol x + \boldsymbol y \Vert ^{2} = \Vert \boldsymbol x \Vert ^{2} + \Vert \boldsymbol y \Vert ^{2}   
$$
# 单位正交基
设$\dim(V) = n,\; \boldsymbol e_1, \ldots ,\boldsymbol e_n$是$V$中两两正交的单位向量，则称它们为$V$的一组*单位正交基*

## Gram-Schmidt正交化
设$\boldsymbol v_1, \ldots ,\boldsymbol v_k\in V$线性无关，则存在两两正交的单位向量$\boldsymbol\epsilon_1, \ldots ,\boldsymbol\epsilon_k$使得
$$
\left< \boldsymbol v_1, \ldots ,\boldsymbol v_i \right> = \left< \boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_i \right>  
$$
其中$i = 1, 2, \ldots ,k$. 特别地，$V$有单位正交基

可以利用如下递推式构造$\boldsymbol \epsilon_i$,
$$
\boldsymbol \epsilon_i' = \boldsymbol v_i - (\boldsymbol v_i \vert \boldsymbol \epsilon_1)\boldsymbol \epsilon_1 - \cdots - (\boldsymbol v_i \vert \boldsymbol \epsilon_{i-1})\boldsymbol  \epsilon_{i - 1} \implies \boldsymbol \epsilon_i = \dfrac{\boldsymbol \epsilon_i'}{\Vert \boldsymbol \epsilon_i' \Vert }
$$
例如要求$U = \left< \boldsymbol u_1,\boldsymbol u_2,\boldsymbol u_3 \right>$是$\mathbb{R}^4$的子空间的一组正交单位基，其中
$$
\boldsymbol u_1 = \begin{pmatrix}
1 \\ 0 \\ 1 \\ 0
\end{pmatrix},\;\boldsymbol u_2 = \begin{pmatrix}
0 \\ -1 \\ 1 \\ -1
\end{pmatrix},\; \boldsymbol u_3 = \begin{pmatrix}
1 \\ 1 \\ 1 \\ 1
\end{pmatrix}
$$
则可由Gram-Schmidt正交化得
$$
\begin{gather}
\boldsymbol \epsilon_1 = \dfrac{{\boldsymbol u_1}}{\Vert \boldsymbol u_1 \Vert } = \dfrac{1}{\sqrt{ 2 }} \boldsymbol u_1 \\
\boldsymbol \epsilon_2' = \boldsymbol u_2 - (\boldsymbol u_2 \vert \boldsymbol \epsilon_1)\boldsymbol \epsilon_1 = \begin{pmatrix}
-\frac{1}{2} \\ -1\\ \frac{1}{2} \\ -1
\end{pmatrix} \\
\boldsymbol \epsilon_2 = \dfrac{\boldsymbol \epsilon_2'}{\Vert \boldsymbol \epsilon_2' \Vert } = \dfrac{1}{\sqrt{ 10 }} \begin{pmatrix}
-1 \\ -2 \\ 1 \\ -2
\end{pmatrix} \\
\boldsymbol \epsilon_3' = \boldsymbol u_3 - (\boldsymbol u_3 \vert \boldsymbol \epsilon_1) \boldsymbol \epsilon_1 -(\boldsymbol u_3 \vert \boldsymbol \epsilon_2)\boldsymbol \epsilon_2 = \dfrac{1}{5} \begin{pmatrix}
-2 \\ 1 \\ 2 \\ 1
\end{pmatrix} \\
\boldsymbol \epsilon_3 = \dfrac{\boldsymbol \epsilon_3'}{\Vert  \boldsymbol\epsilon_3' \Vert } = \dfrac{1}{\sqrt{ 10 }} \begin{pmatrix}
-2 \\ 1 \\ 2 \\ 1
\end{pmatrix}
\end{gather}
$$
## 正交基的性质
### 内积的形式
设$V$的一组单位正交基是$\boldsymbol e_1, \ldots ,\boldsymbol e_n,\;\boldsymbol x, \boldsymbol y\in V$在这组基下的坐标分别是$(x_1, \ldots ,x_n)^t$和$(y_1, \ldots ,y_n)^t$，则有
$$
(\boldsymbol x \vert \boldsymbol y) = x_1y_1+ \cdots +x_ny_n
$$
### 内积取坐标分量
设$V$的一组单位正交基是$\boldsymbol e_1, \ldots ,\boldsymbol e_n,\;\boldsymbol x \in V$. 则$\boldsymbol x$在该基下的第$i$个坐标分量为$(\boldsymbol x \vert \boldsymbol e_i)$，$i = 1,2, \ldots ,n$

### 维数相等的欧式空间线性同构且保持内积不变
设$V,W$是两个$n$-维欧式空间，其中的内积分别记为$(\vert)_V$和$(\vert)_W$，则存在[[Linear Isomorphism|线性同构]]$\phi:V \to W$满足对任意$\boldsymbol x, \boldsymbol y\in V$
$$
(\boldsymbol x \vert \boldsymbol y)_V = (\phi(\boldsymbol x) \vert \phi(\boldsymbol y))_W
$$
# 正交投影和正交补
设$\boldsymbol v\in V \backslash \left\{ \boldsymbol 0 \right\},\;\boldsymbol x\in V$,称
$$
\left( \boldsymbol x \vert \dfrac{\boldsymbol v}{\Vert \boldsymbol v \Vert } \right) \dfrac{\boldsymbol v}{\Vert \boldsymbol v \Vert }
$$
为$\boldsymbol x$在$\boldsymbol v$上的*投影*

设$\boldsymbol v\in V \backslash \left\{ \boldsymbol 0 \right\},\;\boldsymbol x\in V$，$\boldsymbol y$是$\boldsymbol x$在$\boldsymbol v$上的投影，则$(\boldsymbol v - \boldsymbol y)\perp \boldsymbol y$

设$X,Y \subset V$. 如果对任意的$\boldsymbol x\in X$和$\boldsymbol y\in Y$都有$\boldsymbol x \perp \boldsymbol y$，则称$X$和$Y$*正交*，记为$X \perp Y$. 特别地，当$X = \left\{ \boldsymbol x \right\}$时，则$X \perp Y$也记为$\boldsymbol x \perp Y$

设$U \subset V$是[[Linear Space#子空间|子空间]]，$\boldsymbol x\in V$，则存在唯一的$\boldsymbol u\in U$使得$(\boldsymbol x - \boldsymbol u)\perp U$，称这里的$\boldsymbol u$是$\boldsymbol x$在子空间$U$上的*正交投影*. 特别地，向量$\boldsymbol x$在$\boldsymbol v\in V \backslash \left\{ \boldsymbol 0 \right\}$上的投影就是$\boldsymbol x$在$\left< \boldsymbol v \right>$上的正交投影

设$U \subset V$是子空间，令$U^{\perp} \coloneqq \left\{ \boldsymbol x \in V \mid \boldsymbol x\perp U \right\}$，则
1. $U^{\perp}$是子空间且$U \perp U^{\perp}$
2. $V = U \oplus U^{\perp}$，故称$U^{\perp}$是$U$的*正交补*
3. $\left( U^{\perp} \right)^{\perp} = U$，这是$(2)$的直接推论

由第$(2)$点我们知道，设$\boldsymbol e_1, \ldots ,\boldsymbol e_d$是$V$中的单位正交向量，则$\boldsymbol e_1, \ldots ,\boldsymbol e_d$可以扩充为$V$的一组单位正交基，比如说，设标准欧式空间$\mathbb{R}^3$的标准基为$\boldsymbol e_1,\boldsymbol e_2,\boldsymbol e_3$，则有
$$
\left< \boldsymbol e_1 \right>^{\perp} = \left< \boldsymbol e_2,\boldsymbol e_3 \right> ,\quad \left< \boldsymbol e_1 \right> ^{\perp\perp} = \left< \boldsymbol e_2,\boldsymbol e_3 \right> ^{\perp} = \left< \boldsymbol e_1 \right> 
$$
# 正交矩阵与正交等价
## 正交矩阵
设欧式空间$V$有两组单位正交基$\boldsymbol e_1, \ldots ,\boldsymbol e_n$和$\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n$，且矩阵$P\in \mathrm{GL}_n(\mathbb{R})$满足$(\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n)= (\boldsymbol e_1, \ldots ,\boldsymbol e_n)P$. 则对任意的$i,j\in \left\{ 1,2, \ldots ,n \right\}$，我们有
$$
\delta_{i,j} = (\boldsymbol \epsilon_i\vert\boldsymbol \epsilon_j) = \left( (\boldsymbol e_1, \ldots ,\boldsymbol e_n)P^{(i)} \vert (\boldsymbol e_1, \ldots ,\boldsymbol e_n)P^{(j)}\right) = (P^{(i)})^t P^{(j)}
$$
由此得出$P^tP=E$，进而$PP^t = E$

设$P\in \mathrm{GL}_n(\mathbb{R})$. 如果$P^t = P^{-1}$，则称$P$是*正交矩阵*. 所有$n$阶正交矩阵的集合记为$\mathrm{O}_n(\mathbb{R})$

集合$\mathrm{O}_n(\mathbb{R})$是$\mathrm{GL}_n(\mathbb{R})$的[[Group#Subgroup|子群]]

正交矩阵有如下性质
- 如果$P\in \mathrm{{O}}_n(\mathbb{R})$，则$\det (P) = \pm1$，这说明了正交矩阵是一个**旋转矩阵**
- $P\in \mathrm{O}_n(\mathbb{R})$当且仅当$P$的列向量是标准欧式空间$\mathbb{R}^n$中的一组单位正交基
- $P\in \mathrm{O}_n(\mathbb{R})$当且仅当$P$的行向量是标准欧式空间$\mathbb{R}^{1\times n}$中的一组单位正交基

特别地，$P\in \mathrm{O}_2(\mathbb{R})$当且仅当存在$\theta$使得
$$
P = \begin{pmatrix}
\cos \theta & -\sin \theta \\
\sin \theta  &  \cos \theta
\end{pmatrix}
\text{ or }
P = \begin{pmatrix}
\cos \theta & \sin \theta \\
\sin \theta  & -\cos \theta
\end{pmatrix}
$$
设欧式空间$V$由基$\boldsymbol e_1, \ldots , \boldsymbol e_n$和$\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n$，矩阵$P\in \mathrm{GL}_n(\mathbb{R})$满足
$$
(\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n) = (\boldsymbol e_1, \ldots ,\boldsymbol e_n)P
$$
再设$\boldsymbol e_1, \ldots ,\boldsymbol e_n$是单位正交基，则$\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n$是单位正交基当且仅当$P\in \mathrm{O}_n(\mathbb{R})$

## 正交等价
设$A,B\in \mathrm{M}_n(\mathbb{R})$. 如果存在$P\in \mathrm{O}_n(\mathbb{R})$使得$B = P^{-1}AP$，则称$A$与$B$*正交等价*（或*正交相似*），记为$A\sim_o B$

可以验证，$\sim_o$是[[Equivalence Relation|等价关系]]. 且若$A\sim_oB$，则由$A\sim _s B$且$A\sim_c B$，这是因为正交矩阵的逆和转置相等. 由此可得，矩阵的[[Linear Operator#矩阵相似|相似不变量]]和[[Bilinear Form#合同关系的不变量|合同不变量]]都是正交等价的不变量. 但是反之不然，不能用合同等价及相似等价同时成立推出正交等价

在正交等价下，可以同时用$B = P^{-1}AP$和$B = P^tAP$来表示基底变换


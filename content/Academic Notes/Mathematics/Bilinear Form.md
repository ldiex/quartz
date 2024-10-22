# 定义
设
$$
\begin{aligned}
f: V \times V &\to F \\
(\boldsymbol x, \boldsymbol y) &\to f(\boldsymbol x, \boldsymbol y)
\end{aligned}
$$
如果对$\forall \alpha,\beta \in F, \boldsymbol z \in V$满足
$$
f(\alpha \boldsymbol x + \beta \boldsymbol z ,\boldsymbol y) = \alpha f(\boldsymbol x, \boldsymbol y) + \beta f(\boldsymbol z , \boldsymbol y)
$$
和
$$
f(\boldsymbol x, \alpha \boldsymbol y + \beta \boldsymbol z ) = \alpha f(\boldsymbol x, \boldsymbol y) + \beta f(\boldsymbol x , \boldsymbol z)
$$
则称$f$是$V$上的*双线性型*

有如下性质
$$
f(\boldsymbol u + \boldsymbol v,\boldsymbol x + \boldsymbol y) = f(\boldsymbol u, \boldsymbol x) + f(\boldsymbol u , \boldsymbol y) + f(\boldsymbol v, \boldsymbol x) + f(\boldsymbol  v, \boldsymbol y)
$$
$$
f(\alpha \boldsymbol x, \beta \boldsymbol y) = \alpha\beta f(\boldsymbol x, \boldsymbol y)
$$
$$
f(\boldsymbol 0, \boldsymbol y) = f(\boldsymbol 0 + \boldsymbol0, \boldsymbol y) = f(\boldsymbol 0, \boldsymbol y) + f(\boldsymbol 0, \boldsymbol y) \implies f(\boldsymbol 0, \boldsymbol y) = 0
$$
同理有$f(\boldsymbol x, \boldsymbol 0) = 0$

## 例子
- 欧式空间$V$上的内积
- 积性线性函数: $f(\boldsymbol x, \boldsymbol y) = f_1(\boldsymbol x)f_2(\boldsymbol y)$

# 矩阵表示
和线性映射类似, 确定一个双线性型只需要知道它在各个基底下的值

设$V$的一组基为$\boldsymbol e_1, \cdots, \boldsymbol e_n$, $f$是$V$上的双线性型, 则存在唯一的矩阵$A \in \mathrm{M}_n(F)$使得对
$$
\forall \boldsymbol x = (\boldsymbol e_1, \cdots, \boldsymbol e_n) \begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix},\;\boldsymbol y = (\boldsymbol e_1, \cdots, \boldsymbol e_n) \begin{pmatrix}
y_1 \\ \vdots \\ y_n
\end{pmatrix}
$$
我们有
$$
f(\boldsymbol x, \boldsymbol y) = (x_1, \cdots,x_n) A\begin{pmatrix}
y_1 \\ \vdots \\ y_n
\end{pmatrix}
$$
事实上$A = (f(\boldsymbol e_i, \boldsymbol e_j))_{n \times n}$. 称$A$是$f$在$\boldsymbol e_1, \cdots, \boldsymbol e_n$下的矩阵表示, 又称为在这组基下的*度量矩阵*. 反过来, 任一个$n$阶矩阵$A$都对应了一个双线性函数

这个矩阵$A$称为此双线性型的*Gram矩阵*

# 坐标变换

考虑[[Coordinate Transformation | 坐标变换]] 假设双线性型$f$在$V$的两组基底$\boldsymbol e_1 \cdots, \boldsymbol e_n$和$\boldsymbol  \epsilon_1, \cdots, \boldsymbol \epsilon_n$下的矩阵分别是$A$和$B$,且有
$$
(\boldsymbol \epsilon_1, \cdots, \boldsymbol \epsilon_n) = (\boldsymbol e_1, \cdots, \boldsymbol e_n) P
$$
则
$$
B = P^t A P
$$
> [!Note] 小结
> 基底变换: $(\boldsymbol \epsilon_1, \cdots, \boldsymbol \epsilon_n) = (\boldsymbol e_1, \cdots, \boldsymbol e_n) P$
> - 由此对应的向量的坐标变换$\begin{pmatrix}x_1' \\ \vdots \\ x_n'\end{pmatrix} = P^{-1} \begin{pmatrix}x_1 \\ \vdots \\ x_n\end{pmatrix}$
> - 由此对应的双线性型的矩阵变换$B = P^tAP$
# 合同关系
设$A,B \in M_n(F)$. 如果存在$P \in \mathrm{GL}_n(F)$使得$B = P^tAP$, 则称$B$*合同于*$A$,记为$B \sim_c A$

合同关系是一个[[Equivalence Relation|等价关系]]

一个双线性型在不同基底下的矩阵是合同的. 而两个彼此合同的矩阵一定是一个双线性型在不同基底下的矩阵. 于是, **研究双线性型等价于研究方阵在合同意义下的等价类**. 利用矩阵的语言, 我们所要研究的问题是: $\mathrm{M}_n(F)/ \sim_c$ 含有多少不同的等价类? 在每个等价类中可否找出一个“标准” 的代表元? 这个代表矩阵应该尽可能**简单**, 也就是说应该含有尽可能多个$0$, 而非零元素出现的位置应该尽可能有规律.

## 合同关系的不变量

设$A, B \in \mathrm{M}_n(F)$ 若$A \sim_c B$, 则$\mathrm{rank}(A) = \mathrm{rank}(B)$, 这是因为可逆矩阵$P$是满秩的

于是有以下命题成立: 
- 设$f$是$V$上的双线性型, $A$是$f$在$V$的某组基下的矩阵, 则$f$的*秩*定义为$\mathrm{rank}(A)$, 记为$\mathrm{rank}(f)$

合同关系保持对称和斜对称性. 设$A \in \mathrm{M}_n(F)$ (斜)对称, 且$A \sim_c B$, 则$B$也(斜)对称

# 对称双线性型
设$f$是$V$上的双线性型, 如果对$\forall \boldsymbol x, \boldsymbol y \in V$, $f(\boldsymbol x, \boldsymbol y) = f(\boldsymbol y, \boldsymbol x)$, 则称$f$是*对称双线性型*

空间$V$上所有对称双线性型组成的集合记为$\mathcal L_2^+ (V)$

## 基底的对称性
设$f$是$V$上的双线性型, $\boldsymbol e_1, \cdots, \boldsymbol e_n$是$V$的一组基, $A$是$f$在$\boldsymbol e_1, \cdots, \boldsymbol e_n$下的矩阵. 则$f$是对称的当且仅当$A$是对称的

## 极化公式
设$F$的[[Characteristic of a Ring|特征]]不等于$2$且$f \in \mathcal L_2^+(V)$. 则对于$\forall \boldsymbol x, \boldsymbol y \in V$
$$
f( \boldsymbol x, \boldsymbol y) = \dfrac{1}{2}\left(f(\boldsymbol x + \boldsymbol y, \boldsymbol x + \boldsymbol y) - f(\boldsymbol x, \boldsymbol x) - f(\boldsymbol y , \boldsymbol y)\right)
$$

## 规范基
设$F$的特征不等于$2$且$f \in \mathcal L_2^+(V)$. 则$V$中有一组基使得$f$在该基下的矩阵是*对角阵*

设$f \in \mathcal L_2^+(V)$, $f$在$V$的基底$\boldsymbol e_1, \cdots, \boldsymbol e_n$下的矩阵是对角阵. 则称$\boldsymbol e_1, \cdots, \boldsymbol e_n$是$f$的一组*规范基*.

且有
$$
f(\boldsymbol e_i, \boldsymbol e_j) = 0, \quad i\neq j\in[n] 
$$

设双线性型$f$在一组规范基下的矩阵为$\operatorname{diag}(\lambda_1, \cdots, \lambda_n)$, 则
$$
f(\boldsymbol x, \boldsymbol y) = \lambda_1x_1y_1 + \cdots + \lambda_n x_n y_n
$$


设$f \in \mathcal L_2^+ (V)$且$r = \mathrm{rank} (f)$. 则存在$V$的一组规范基使得$f$在该基下的矩阵为
$$
\operatorname{diag} (\lambda_1, \lambda_2, \cdots, \lambda_r, 0, \cdots, 0)
$$
其中$\lambda_1, \lambda_2, \cdots, \lambda_r \in F \backslash \{0\}$

设$A \in \mathrm{SM}_n(F), \mathrm{rank}(A) = r$. 则存在$F$中非零元素$\lambda_1, \cdots, \lambda_r$使得$A \sim_c \operatorname{diag}(\lambda_1, \lambda_2, \cdots, \lambda_r, 0, \cdots, 0)$

## 对称矩阵和对角阵的合同性
设$F$的特征不等于$2$, $A \in \mathrm{SM}_n (F)$. 则$A$[[Bilinear Form#合同关系|合同]] 于一个对角阵, **这个对角阵并不是唯一的**

- 当$n = 1$时结论显然成立, 故采用归纳法, 假设维数小于$n$时上述结论成立
- 若$f(\boldsymbol x, \boldsymbol y)$恒为$0$的结论显然成立. 若存在一组$f(\boldsymbol x, \boldsymbol y) \neq 0$, 则此时必然存在$\boldsymbol e_1$使得$f(\boldsymbol e_1, \boldsymbol e_1) \neq 0$. 不然由[[Bilinear Form#极化公式|极化公式]] $f(\boldsymbol x,\boldsymbol y)$将恒等于$0$
- 令$W = \ker(f(\boldsymbol x, \boldsymbol e_1))$, 现在证明$V = \langle \boldsymbol e_1 \rangle \oplus W$
	- 容易看出$\langle \boldsymbol e_1 \rangle + W$是直和, 故我们只需要证明$\dim(W) = n - 1$
	- 一方面$f(\boldsymbol e_1, \boldsymbol e_1) \neq 0$, 故$\dim(\mathrm{im}(f(\boldsymbol x, \boldsymbol e_1))) \ge 1$
	- 另一方面$\mathrm{im}(f(\boldsymbol x, \boldsymbol e_1)) \subset F$, 故$\dim(\mathrm{im}(f(\boldsymbol x, \boldsymbol e_1))) \le 1$
	- 于是$\dim(\mathrm{im}(f(\boldsymbol x, \boldsymbol e_1))) = 1$, 由[[Basis and Dimension#对偶定理|对偶定理]] 得$\dim(W) = n - 1$
- 设$g \in \mathcal L_2(W)$满足$\forall \boldsymbol x, \boldsymbol y \in W,\; g(\boldsymbol x, \boldsymbol y) = f(\boldsymbol x, \boldsymbol y)$, 由归纳条件, 存在$W$的一组基$\boldsymbol e_2, \cdots, \boldsymbol e_n$使得$\forall i, j \in\{2, 3, \cdots, n\},\; i \neq j$有$g(\boldsymbol e_i, \boldsymbol e_j) = f(\boldsymbol e_i, \boldsymbol e_j)  = 0$, 由于我们已经证明了直和分解, $\boldsymbol e_1, \cdots, \boldsymbol e_n$即为$V$的一组基. 
- 又由$W$的定义, $f(\boldsymbol e_i, \boldsymbol e_1) = 0,\; i = 2, 3, \cdots, n$. 再由$f$对称性反过来也成立. 于是$\forall i, j \in\{1, 2, \cdots, n\},\; i \neq j$有$f(\boldsymbol e_i, \boldsymbol e_j) = 0$. 归纳假设对$\dim(V) = n$也成立
### 合同对角化方法
#### 求kernel
采用上面的证明过程, 将$\mathrm{SM}_n(F)$上的合同对角化问题转化为$\mathrm{SM}_{n - 1}(F)$上的合同对角化问题
#### 行列相伴
目标是找到一个可逆矩阵$C$使得
$$
C^t A C = B
$$
其中$A$是对称矩阵, $B$是对角矩阵
而$C$总可以写成一系列初等矩阵的积, 故我们需要找到
$$
P_k^t \cdots P_1^tAP_1\cdots P_k = B
$$
又因为矩阵乘法满足结合律, 故可以先计算$(P_1^t A P_1)$, 再计算$P_2^t(P_1^t A P_1)P_2 , \cdots$ 即每次先进行一次$P^t$对应的行变换, 紧接着进行$P$对应的行变换, 这就是所谓的*行列相伴*

对于第一类和第二类初等变换, 可以验证$P^t = P$
而对于第三类初等变换, 有
$$
r_i + kr_j \to r_j+kr_i;\; c_i + k c_j \to c_j + kc_i
$$
会把被加的行（列）号变成另外一个
**但是, 如果$r_i + kr_j$转置后再使用右乘, 仍然是$c_i + kc_j$的效果**

由此, 我们可以构造分块矩阵$\begin{pmatrix}A \\ E\end{pmatrix}$, 不断对其进行如上行列相伴的变换, 直到$A$变成对角矩阵, 此时的$E$就会变换成我们需要的那个$C$

#### 配方法
见[[Quadratic Forms | 二次型]]


#### 复数域上的平凡解
设$A \in \mathrm{SM}_n(\mathbb C), \mathrm{rank}(A) = r$则
$$
A \sim_c \begin{pmatrix}
E_r & O \\ O & O
\end{pmatrix}
$$
这里相应的$P$为
$$
P = \operatorname{diag} \left(\dfrac{1}{\sqrt{\lambda_1}}, \cdots, \dfrac{1}{\sqrt{\lambda_r}}, 1, \cdots, 1\right)
$$




# 重要提醒
## 1. $\mathbb{Z}_n$的子群包括两个平凡子群：自己和$\{ \bar 0 \}$!
## 2. $\det(kA) = k^2 \det(A)$!
## 3. $\gcd$函数可以对多项式使用! 
## 4. 写$a^{-1}$的时候先要想想$a$可不可逆（$a$会不会是$0$）
## 5. 什么是域的特征？

# 送分童子
## $\mathbb{Z}_n$中元素求阶
$(\mathbb{Z}_n, +)$是循环群，其中某个元素的阶
$$
\text{ord}(\bar k) = \text{ord}({\bar 1}^k) = \frac{n}{\gcd(n,k)}
$$
$(\mathbb{Z}_n^*,\cdot)$是群，包含$\mathbb{Z}_n$中所有的元素$\bar k: \gcd(n, k) = 1$. 特别地，当$n$为质数$p$时，$\mathbb{Z}_p^* = \mathbb{Z}_p$为循环群. 要求该群中的某个元素$a$的阶，需要计算最小的$k$使得
$$
a^k \equiv 1 \pmod{n}
$$
**计算子群**
对于$(\mathbb{Z}_n, +)$，只需要计算$n$的每一个因子生成的子群
对于$(\mathbb{Z}_n^*,\cdot)$，子群的阶一定是该群阶的因数，对于每一个子群可能的阶，枚举出所有的可能
## 线性无关互推
设$\boldsymbol v_1,\boldsymbol v_2, \boldsymbol v_3 \in \mathbb{F}^n$, 证明$\boldsymbol v_1 + \boldsymbol v_2, \boldsymbol v_2 + \boldsymbol v_3, \boldsymbol v_3+ \boldsymbol v_1$线性无关$\iff \boldsymbol v_1,\boldsymbol v_2, \boldsymbol v_3$线性无关
**证明**
设$\boldsymbol w_1 = \boldsymbol v_1 + \boldsymbol v_2,\boldsymbol w_2 = \boldsymbol v_2 + \boldsymbol v_3,\boldsymbol w_3 = \boldsymbol v_3 + \boldsymbol v_1$，若$\boldsymbol w_1, \boldsymbol w_2, \boldsymbol w_3$线性无关，因为$\boldsymbol w_1, \boldsymbol w_2, \boldsymbol w_3 \in \langle \boldsymbol v_1, \boldsymbol v_2, \boldsymbol v_3 \rangle$，所以
$$
\dim \langle \boldsymbol v_1, \boldsymbol v_2, \boldsymbol v_3 \rangle \ge 3
$$
故$\boldsymbol v_1, \boldsymbol v_2, \boldsymbol v_3$线性无关
反之，设$\boldsymbol v_1, \boldsymbol v_2, \boldsymbol v_3$线性无关，注意到
$$
\boldsymbol v_1 = \frac{1}{2}(\boldsymbol w_1 - \boldsymbol w_2 + \boldsymbol w_3),\;\boldsymbol v_2 = \frac{1}{2}(\boldsymbol w_1 + \boldsymbol w_2 - \boldsymbol w_3),\;\boldsymbol v_3 = \frac{1}{2}(-\boldsymbol w_1 + \boldsymbol w_2 + \boldsymbol w_3)
$$
于是$\boldsymbol v_1, \boldsymbol v_2, \boldsymbol v_3 \in \langle \boldsymbol w_1, \boldsymbol w_2, \boldsymbol w_3 \rangle$，同理可以得到$\boldsymbol w_1, \boldsymbol w_2, \boldsymbol w_3$线性无关
## 矩阵带入多项式
注意把$X^2 + 2X + \textcolor{red}{1}$这样的改成$A^2 + 2A + \textcolor{orange}{E}$
## 子群判别法证明
**命题**：设$(G,\cdot,e)$是群, $H$是$G$的非空子集. 则$H$是$G$的子群$\iff \forall h_1,h_2 \in H,\; h_1h_2^{-1} \in H$
**证明**：对于**充分性**，如果$H$是$G$的子群，那么运算$\cdot$在$H$上封闭，于是对于$\forall h_1,h_2 \in H$显然有$h_1h_2^{-1} \in H$. 充分性得证
对于**必要性**，设$h_1 \in H$，则$e = h_1 h_1^{-1} \in H$（单位元保持），进而$h^{-1} = eh^{-1} \in H$（逆元存在），再设$h_2 \in H \implies h_2^{-1} \in H \implies h_1h_2 = h_1(h_2^{-1})^{-1} \in H$（运算封闭）
**提醒：不要忘记证明充分性**
## 在域（剩余类）上解线性方程组
注意某个子空间中含有向量的个数可能是有限的
## 摄动法
把域扩张到$\text{Fr}[F[X]]$，然后把待证等式加一未定元转化为多项式恒等式，最后赋值$0$
## 从$F^n$到$F^m$的线性映射，确定$\text{ker}$和$\text{Im}$
## 矩阵求逆
### 行变换法
### 多项式法
设$A \in M_n(F)$，设$k$是最小的正整数使得
$$
\alpha_k A^k + \cdots + \alpha_1A + \alpha_0E = O
$$
则$A$可逆当且仅当$\alpha_0 \neq 0$，此时有
$$
\begin{aligned}
A(\alpha_k A^{k-1} + \cdots + \alpha_1 E) = -\alpha_0E \\
\implies A^{-1} = -\alpha_0^{-1}(\alpha_1E + \cdots + \alpha_k A^{k - 1})
\end{aligned}
$$
应用：
观察待求逆的矩阵的幂次（通常只需要观察$A^2$)，然后想办法凑成上面的形式

## 行列式计算
### 化为上（下）三角矩阵
### 按照行列展开寻找某个递归公式，然后通过归纳法来证明它
## 交换环的例子
$\mathbb{Z}_n$和$F[A]$

# 知识难点
## 伴随矩阵的秩
$$
\mathrm{rank} (A^{\vee}) =
\begin{cases}
n &, \mathrm{rank}(A) = n \\
1 &, \mathrm{rank}(A) = n - 1\\
0 &, \mathrm{rank}(A) \le n -2
\end{cases}
$$

## 环和整环
### 环
1. 在加法上是一个交换群
2. 在乘法中是一个半群
3. 同时满足左右分配律
### 整环
交换幺环+满足分配律

## 同态和同构
### 群同态
只需要验证（注意这里左右两边$\cdot$是不同的运算）
$$
\phi(a \cdot b) = \phi(a) \cdot \phi(b)
$$
有如下性质
$$
\phi(a^{-1}) = (\phi(a))^{-1} ,\; \phi(e) = e'
$$

### 环同态
只需要验证保持加法、乘法和单位元
$$
\begin{aligned}
\phi(a + b) &= \phi(a) + \phi(b) \\
\phi(a \cdot b) &= \phi(a) \cdot \phi(b) \\
\phi(1) &= 1
\end{aligned}
$$
有如下性质
$$
\phi(a^{-1}) = (\phi(a))^{-1} ,\; \phi(0) = 0
$$
环同态是单射，当且仅当
$$
\ker \phi = \{0\}
$$
### 同构
同态 + 双射

## 循环群
1. 一个循环群的子群也是循环群
2. 一个由一个生成元生成的循环群的阶等于其生成元的阶
## 秩不等式
[[Sylvester Inequality|Sylvester不等式]]
设$A \in F^{m \times s}, B \in F^{s \times n}$则
$$
\mathrm{rank}(A) + \mathrm{rank}(B) - s \le \mathrm{rank}(AB) \le \min\{\mathrm{rank}(A),\mathrm{rank}(B)\}
$$
$$
\mathrm{rank}(A + B) \le \mathrm{rank}(A) + \mathrm{rank}(B)
$$
$$
\mathrm{rank}(A,B) \le \mathrm{rank}(A) + \mathrm{rank}(B)
$$
$$
\mathrm{rank} \begin{pmatrix} A & C \\ O & B\end{pmatrix} \ge \mathrm{rank}(A) + \mathrm{rank}(B)
$$


# 历年真题

### 第一题
设$A = (a_{i,j}) \in M_n (\mathbb{Q})$, 其中$a_{i,j} \in \mathbb{Z}$. 再设$p$是素数，$\pi_p: \mathbb{Z} \to \mathbb{Z}_p$是商映射，和$A_p = (\pi_p(a_{i,j})) \in M_n(\mathbb{Z}_p)$
1. 证明$\pi_p (\det (A)) = \det{A_p}$
2. $\mathrm{rank} (A) \ge \mathrm{rank}(A_p)$且只存在有限个素数$p \text{ s.t. } \mathrm{rank}(A) > \mathrm{rank}(A_p)$
**证明**
1. 关键是**商映射是一个环同态**， 因为这个映射保留了加法和乘法，所以说当它作用于一个多项式时，相当于它作用到了这个多项式的每一项的那个未定元上.
2. 关键是用子式来分析秩，从而**将非多项式的秩转化为多项式的行列式**

如果$\mathrm{rank}(A) = n$那么不等式显然成立
如果$r = \mathrm{rank}(A) < n$那么，那么所有$A$中大于$r$阶的子式全部为零，根据$\pi_p$环同态的性质，$A_p$中大于$r$阶的子式也全部为$0$，于是不等式亦成立

现在证明素数$p$是有限的，设$r = \mathrm{rank}(A)$，那么$A$至少存在一个$r$阶子式不等于$0$，假设有$k$个$r$阶子式不为零，若要使$\mathrm{rank}(A) > \mathrm{rank}(A_p)$，这$k$个子式必须都被$p$整除，所以说$p$必须是这些子式的公共素因子，故而$p$必然是有限的

### 第二题
设$F$是域，矩阵$A \in F^{m \times n}$，且$E_m$代表$m$阶单位方阵，证明
1. $\mathrm{rank} A = m \iff \exists B \in F^{n \times m} \text{ s.t. } AB = E_m$
2. $(\mathrm{rank} A = m) \land (m < n) \iff \exists B,C \in F^{n \times m} \text{ s.t. } (AB = AC = E_m) \land (B \neq C)$
**证明**
1. 对于$\Longleftarrow$， 关键是**矩阵乘法不增加秩**，故$\mathrm{rank} A \ge \mathrm{rank} E_m = m$，即$\mathrm{rank} A = m$
对于$\implies$，关键是直接把$B$解出来，对于$B$的每一列$B^{(i)}$ 都满足方程
$$
AB^{(i)} = E_m^{(i)}
$$
因为$\mathrm{rank} A = m$，所以$\mathrm{rank}(A | E_m^{(i)}) = m$，于是$B^{(i)}$有解，故而$B$是有解的
这里利用了: **对于线性方程组$Ax = b$，如果$\mathrm{rank}(A) = \mathrm{rank}(A|b)$则方程组有解，如果$\mathrm{rank}(A) < \mathrm{rank}(A|b)$则方程组无解**；而由于$\mathrm{rank}(A) \le \mathrm{rank}(A|b)$且$\mathrm{rank}(A|b)$最大只能取$m$，故这里的$\mathrm{rank}(A|b) = m$
2. 对于$\Longleftarrow$，由第一小题已知$\mathrm{rank} A = m$，而$\mathrm{rank} A \le n \implies m \le n$，如果$m = n$，那么$A$是可逆方阵, $B,C$自然是同一个矩阵，这不符合题设. 于是只能有$m < n$
对于$\implies$，和第一小题一样，$B^{(i)}$必然是有解的，我们考虑其对应的齐次方程$AB^{(i)} = 0$的解空间$V_i$的维数
$$
\dim V_i = n - \mathrm{rank}(A) = n - m >0
$$
故$V_i$至少存在一个基底，记为$\boldsymbol e_i$，于是便可以取$C^{(i)} = B^{(i)} + \boldsymbol e_i$，如此可以得到$C \neq B$
**注意：只有齐次线性方程组的解构成一个子空间，而一般的线性方程组的解构成一个线性流形**

**另证**
直接求解矩阵方程$AX = E_m$, 其中未知矩阵$X \in F^{n \times m}$. 根据打洞引理，存在$P \in GL_m(F)$和$Q \in GL_n(F)$使得
$$
A = P \begin{pmatrix} E_r & O \\ O & O\end{pmatrix} Q
$$
其中$r = \mathrm{rank}(A)$. 故原方程等价于
$$
P\begin{pmatrix} E_r & O \\ O & O \end{pmatrix} QX = E_m \iff \begin{pmatrix} E_r & O \\ O & O\end{pmatrix} QX = P^{-1}
$$
令$Y = QX$，则$Y \in F^{n \times m}$. $因为$$Q$可逆，所以原方程有解当且仅当
$$
\begin{pmatrix} E_r & O \\ O & O \end{pmatrix}Y = P^{-1} \tag{$\ast$}
$$
有解.
1. 如果$B$存在，则$(\ast)$ 有解. 故$r = m$. 如果$r = m$，则$(\ast)$可以写为
$$
(E_m, O) \begin{pmatrix} Y_1 \\ Y_2\end{pmatrix} = P^{-1},\; Y_1 \in M_m,Y_2 \in F^{(n-m) \times m} \tag{$\ast\ast$}
$$
故有
$$
Y = \begin{pmatrix}P^{-1} \\ M\end{pmatrix}
$$
其中$M \in F^{(n-m) \times m}$是任意矩阵. 故$B$存在
2. 如果存在不同的矩阵$B, C, \text{ s.t. } AB=AC=E_m$，故上述$Y$中矩阵$M$至少存在一行，故有$n > m$. 如果$\mathrm{rank}(A) = m$且$m < n$，则任意矩阵$M$必然存在. 于是,$(\ast\ast)$至少有两个解
### 第三题
设$F$是域，$A,B,C,D \in M_n(F)$且$AC = CA$. 证明
$$
\det \begin{pmatrix} A & B \\ C & D\end{pmatrix} = \det (AD-CB)
$$
思路：我们希望把分块矩阵化成**上三角的形式**，就要把$C$约掉，所以不妨假设$A$可逆，那么
$$
\begin{pmatrix} E & O \\ -A^{-1}C & E\end{pmatrix} \begin{pmatrix} A & B \\ C & D\end{pmatrix} = \begin{pmatrix} A & B \\ -A^{-1} CA+C & -A^{-1}CB+D\end{pmatrix} = \begin{pmatrix} A & B \\ O & -A^{-1}CB + D\end{pmatrix}
$$
于是
$$
\det \begin{pmatrix} A & B \\ C & D\end{pmatrix} = \det \begin{pmatrix} A & B \\ O & -A^{-1}CB + D\end{pmatrix} = \det A \det(-A^{-1}CB + D) = \det (AD - CB)
$$
如果$A$不可逆，设$t \in F$未定，则$tE + A \in M_n(\text{Fr}[F[x]])$，故$tE + A$可逆，于是
$$
\det \begin{pmatrix} tE + A & B \\ C & D\end{pmatrix} = \det((tE + A)D - CB)
$$
左右两边都是$t$的多项式，所以令$t = 0$，即有
$$
\det \begin{pmatrix} A & B \\ C & D\end{pmatrix} = \det (AD-CB)
$$
### 第四题
证明$\text{SL}_2(\mathbb{R}) = \langle S \rangle$，其中$S$是所有$2\times 2$的第二类初等矩阵构成的集合
思路，利用第二类初等矩阵把所有行列式为1的$2\times 2$矩阵变为$E$
$$
P_1AQ_1 = \begin{pmatrix} 1 & 0 \\ -a^{-1}c & 1\end{pmatrix} \begin{pmatrix} a & b \\ c & d\end{pmatrix} \begin{pmatrix} 1 & -a^{-1}b \\ 0 & 1\end{pmatrix} = \begin{pmatrix} a & 0 \\ 0 & d - bca^{-1}\end{pmatrix} = \begin{pmatrix} a & 0 \\ 0 & a^{-1}\end{pmatrix} = B
$$
$$
P_2BQ_2 = \begin{pmatrix} 1 & 1 \\ 0 & 1\end{pmatrix} \begin{pmatrix} a & 0 \\ 0 & a^{-1}\end{pmatrix} \begin{pmatrix} 1 & 0 \\ a(1-a) & 1\end{pmatrix} = \begin{pmatrix} 1 & a^{-1} \\ 1-a & a^{-1}\end{pmatrix} =C
$$
$$
P_3CQ_3 = \begin{pmatrix} 1 & 0 \\ a - 1 & 1\end{pmatrix}\begin{pmatrix} 1 & a^{-1} \\ 1-a & a^{-1}\end{pmatrix}\begin{pmatrix}1 & -a^{-1} \\ 0 & 1 \end{pmatrix} = E
$$
于是
$$
A = P_1^{-1}P_2^{-1}P_3^{-1}Q_3^{-1}Q_2^{-1}Q_1^{-1}
$$
注意，讨论$a = 0$的情况

### 第五题
设$A$是域$F$上的$n$阶方阵，$B \in F[A]$且$B$不是零矩阵，证明
1. $B$是$F[A]$中的可逆元$\iff \mathrm{rank}(B) = n$
2. $B$是$F[A]$中的零因子$\iff \mathrm{rank}(A) < n$
**证明**
这道题的关键在于如下定理：
设$A$为给定的$n \times n$矩阵，$A$的**特征多项式**定义为
$$
p(\lambda) = \det(\lambda E_n-A)
$$
那么，Cayley–Hamilton定理断言
$$
p(A) = O
$$
这告诉我们总存在一个非零多项式$p \in F[X]$使得$p(A) = O$

那么，从这一点出发，注意到[[Linear Algebra 23 Fall Final#多项式法]]给出的方法，$\alpha_0, \alpha_1, \cdots, \alpha_k$总是存在的，而$B$在$M_n(F)$上的可逆性将决定$\alpha_0$是否为$0$




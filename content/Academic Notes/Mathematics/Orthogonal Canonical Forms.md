# 正规算子和正规矩阵的标准型
设$\dim (V) = 1$, 则任意的$\mathcal A\in \mathcal{L}(V)$都是[[Normal Operator and Normal Matrix#正规算子|正规算子]], 这是因为对$V$中的单位向量$\boldsymbol v$, $\mathcal A(\boldsymbol v) = \lambda \boldsymbol v$, 其中$\lambda$是某个实数

设$\dim{(V)}=2,\;\mathcal A\in \mathcal{L}(V)$正规, 且$V$是$\mathcal A$-不可分的（在可分的情形下$A$可以通过一维形式的直和得到）, 则$\mathcal A$在$V$的任意[[Euclidean Space#单位正交基|单位正交基]]下的矩阵式
$$
A = \begin{pmatrix}
\alpha  &  - \beta \\
\beta  &  \alpha
\end{pmatrix}
$$
其中$\alpha,\beta\in \mathbb{R}$且$\beta \neq 0$

设$\mathcal A\in \mathcal{L}(V)$正规, 则存在$V$的一组单位正交基$\boldsymbol e_1, \ldots ,\boldsymbol e_n$和$\alpha_1,\beta_1, \ldots , \alpha_s,\beta_s,\;\lambda_{2s+1},\lambda_n\in \mathbb{R}$, 其中$\beta_1, \ldots ,\beta_s \neq 0$, 使得$\mathcal A$在这组基下的矩阵等于
$$
B=\begin{pmatrix}
N(\alpha_1,\beta_1) & & & & &\\
& \ddots & & & &\\
& & N(\alpha_s,\beta_s) & & & \\
& & & \lambda_{2s+1} & & \\
& & & & \ddots & \\
& & & & & \lambda_n
\end{pmatrix}
$$
其中
$$
N(\alpha,\beta) = \begin{pmatrix}
\alpha & -\beta \\
\beta & \alpha
\end{pmatrix}
$$
也就是说, 存在如上这样一个标准型$B$使得$A$[[Euclidean Space#正交等价|正交等价]]于$B$, 即$A \sim_o B$, 弱化这个结论就是有$A$[[Linear Operator#矩阵相似|相似]]于$B$, 即$A \sim_s B$

设$\mathcal A\in \mathcal{L}(V)$正规, $\lambda_1,\lambda_1\in \mathrm{spec}_{\mathbb{R}}(\mathcal A)$, 且$\lambda_1 \neq \lambda_2$, 则$V^{\lambda_1} {\perp} V^{\lambda_2}$. 也就是说, 一个正规算子的不同[[Eigenvectors and Characteristic Polynomial#特征值|特征值]]对于的[[Eigenvectors and Characteristic Polynomial#特征子空间|特征子空间]]两两[[Euclidean Space#正交子空间和正交投影|正交]], 这是在正规算子情况下, 对命题[[Eigenvectors and Characteristic Polynomial#特征子空间的和|特征子空间的和是直和]]的一个加强

# 实对称矩阵的正交标准型
## 实对称矩阵可正交化
对于实对称矩阵, 有如下命题成立
1. 设$\mathcal A\in \mathcal{L}(V)$对称, 则$\mathcal A$在$V$的某组[[Euclidean Space#单位正交基|正交基]]下的矩阵是$\mathrm{diag}(\lambda_1, \ldots ,\lambda_n)$, 其中$\lambda_1, \ldots ,\lambda_n \in \mathbb{R}$不必两两不同
2. 设$A\in \mathrm{SM}_n(\mathbb{R})$, 则$A \sim_o \mathrm{diag}(\lambda_1, \ldots ,\lambda_n)$, 其中$\lambda_1, \ldots ,\lambda_n\in \mathbb{R}$不必两两不同, 即实对称矩阵是[[Diagonalization|可对角化的]]
3. $\lambda_1, \ldots ,\lambda_n$是算子$\mathcal A$或者是矩阵$A$的[[Eigenvectors and Characteristic Polynomial#特征值|特征根]], 特别地, 实对称矩阵和[[Euclidean Space|欧式空间]]上的对称算子的特征根都是实数

现在给出求解该对角矩阵的算法
1. 计算$\mathcal A$的特征根, 设互不相同的特征根是$\lambda_1, \ldots ,\lambda_k$
2. 对$i\in \left\{ 1,2, \ldots ,k \right\}$, 求$V^{\lambda_i}$的一组基
3. 对$i\in \left\{ 1,2, \ldots ,k \right\}$, 利用[[Euclidean Space#Gram-Schmidt正交化|Gram-Schmidt正交化]]求$V^{\lambda_i}$的一组单位正交基$\boldsymbol e_{i,1}, \ldots ,\boldsymbol e_{i,d_i}$
4. 由此得到的$\boldsymbol e_{1,1}, \ldots ,\boldsymbol e_{1,d_1}, \ldots ,\boldsymbol e_{k,1}, \ldots ,\boldsymbol e_{k,d_k}$是$V$的一组单位正交基, 且在该基下$\mathcal A$是对角的

例如, 设
$$
A = \begin{pmatrix}
0 & 1 & 1 & -1 \\
1 & 0 & -1 & 1 \\
1 & -1 & 0 & 1 \\
-1 & 1 & 1 & 0
\end{pmatrix}\in \mathrm{SM}_4(\mathbb{R})
$$
则可计算$\chi_A(t) = (t-1)^3(t+3) \implies \lambda_1 = 1,\lambda_2 = -3$, 由于$4 = \dim{V^{\lambda_1}} + \dim{V^{\lambda_2}}$且$\dim{V^{\lambda_2}}$至少为$1$且其最大值为$\lambda_2$的[[Eigenvectors and Characteristic Polynomial#维数和重数|代数重数]]也为$1$, 故$\dim{V^{\lambda_2}}=1,\dim{V^{\lambda_1}} = 3$, (事实上, 由于$A$是[[Diagonalization|可对角化的]], 故$\lambda_1$的代数重数必然等于其几何重数), 考虑到
$$
{V^{\lambda_1}} = {{\ker \left( \lambda_1E-A \right) }} = \ker \begin{pmatrix}
1 & -1 & -1 & 1 \\
-1 & 1 & 1 & -1 \\
-1 & 1 & 1 & -1 \\
1 & -1 & -1 & 1
\end{pmatrix}
$$
只需要考虑方程
$$
x_1 -x_2-x_3+x_4 = 0
$$
的解空间即可, 直接得出
$$
V^{\lambda_1} = \left< \begin{pmatrix}
1 \\ 1 \\ 0 \\ 0
\end{pmatrix}, \begin{pmatrix}
0 \\ 0 \\ 1 \\ 1
\end{pmatrix}, \begin{pmatrix}
1 \\ 0 \\ 0 \\ -1
\end{pmatrix} \right> 
$$
再计算$V^{\lambda_2}$, 因为$V^{\lambda_1} {\perp} V^{\lambda_2}$且$\mathbb{R}^4 = V^{\lambda_1} \oplus V^{\lambda_2}$, 所以$V^{\lambda_2}$为$V^{\lambda_1}$的[[Euclidean Space#正交补|正交补]], 由于上述方程已经给出了
$$
(1,-1,-1,1)\cdot(x_1,x_2,x_3,x_4) = 0
$$
故
$$
V^{\lambda_2} = \left< \begin{pmatrix}
1 \\ -1 \\ -1 \\ 1
\end{pmatrix} \right> 
$$
利用Gram-Schmidt正交化可分别求出$V^{\lambda_1},V^{\lambda_2}$的单位正交基
$$
\boldsymbol \epsilon_1 = \dfrac{1}{\sqrt{ 2 }} (1,1,0,0)^t,\boldsymbol \epsilon_2 = \dfrac{1}{\sqrt{ 2 }}(0,0,1,1)^t,\boldsymbol \epsilon_3 = \dfrac{1}{2}(1,-1,1,-1)^t;\;\boldsymbol \epsilon_4 = \dfrac{1}{2} (1,-1,-1,1)^t
$$
故
$$
P = \begin{pmatrix}
\dfrac{1}{\sqrt{ 2 }} & 0 & \dfrac{1}{2} & \dfrac{1}{2} \\
\dfrac{1}{\sqrt{ 2 }} & 0 & -\dfrac{1}{2} & -\dfrac{1}{2} \\
0 & \dfrac{1}{\sqrt{ 2 }} & \dfrac{1}{2} & -\dfrac{1}{2} \\
0 & \dfrac{1}{\sqrt{ 2 }} & -\dfrac{1}{2} & \dfrac{1}{2}
\end{pmatrix}
$$
我们得到$P^tAP = \mathrm{diag}(1,1,1,-3)$

## 惯性指数的求法
设$A\in \mathrm{SM}_n(\mathbb{R})$, 则$A$的正（负）[[Real Quadratic Forms#惯性定理 (Sylvester)|惯性指数]]等于$\mathrm{spec}(A)$中正（负）根的个数（在记重数的意义下）, 特别地, $A$（半）正定当且仅当$A$的特征根都是正的（非负的）

特别地, 设$A,B\in \mathrm{SM}_n(\mathbb{R})$且$A$正定, 则存在$P\in \mathrm{GL}_n(\mathbb{R})$使得$P^tAP=E$和$P^tBP$是对角阵, 这是因为
1. 由于$A$正定, 所以存在$P_1\in\mathrm{GL}_n(\mathbb{R})$使得$P_1^tAP_1=E$
2. 令$C = P_1^tBP_1$, 则$C$也对称, 故存在$P_2\in \mathrm{O}_n(\mathbb{R})$使得$D = P_2^tCP_2$是对角阵
3. 令$P = P_1P_2$, 则$P^tBP = P_2^tCP_2 = D$且
$$
P_2\in \mathrm{{O}_n(\mathbb{R}) \implies }P^tAP = P_2^tEP_2 = P_2^tP_2 = E
$$
由此可以证明**对于正定矩阵**
$$
\det{(A+B)} \geq \det{(A)} + \det{(B)}
$$
由于存在$P\in \mathrm{GL_n}(\mathbb{R})$使得$P^tAP = E,P^tBP = \mathrm{diag}(\alpha_1, \ldots ,\alpha_n)$, 于是
$$
P^t(A+B)P = \mathrm{diag}(1+\alpha_1, \ldots ,1+\alpha_n)
$$
两边取行列式有
$$
\det{(P)}^{2} \det{(A+B)} = \prod_{i = 1}^n(1+\alpha_i)
$$
而
$$
\det{(P)}^{2}\left( \det{(A)} + \det{(B)}\right)  = \det{(P^tAP)} + \det{(P^tBP)} = 1+ \prod_{i = 1}^n \alpha_i
$$
因为$B$正定, 所以$\alpha_1, \ldots ,\alpha_n\in \mathbb{R}^+$, 于是$\prod(1+\alpha_i) \geq 1+ \prod\alpha_i$, 故命题得证

# 斜对称算子和斜对称矩阵
设$\mathcal A\in \mathcal{L}(V)$斜对称, 则存在$\beta_1, \ldots ,\beta_s\in \mathbb{R} \backslash \left\{ 0 \right\}$, 使得$\mathcal A$在$V$的某组单位正交基下的矩阵为
$$
M = \begin{pmatrix}
N(0,\beta_1) & & & & & \\
& \ddots & & & &  \\
& & N(0,\beta_s) & & & \\
& & & 0 & & \\
& & & & \ddots &  \\
& & & & & 0
\end{pmatrix}
$$
设$A\in \mathrm{SSM}_n(\mathbb{R})$, 则$A$正交相似于上述形式的矩阵

实斜对称矩阵和欧式空间上的斜对称算子的特征根或者是纯虚数, 或者等于$0$

设$A\in \mathrm{SSM}_n(\mathbb{R})$, 则$\det{(E+A)} \geq 1$, 这是因为存在$P\in \mathrm{O}_n(\mathbb{R})$使得$P^tAP = M$, 于是
$$
P^t(E+A)P = E+ M = \mathrm{diag} (N(1,\beta_1), \ldots ,N(1,\beta_s),1, \ldots ,1)
$$
因为$\det{(P)} = \pm 1$和$\det{(N(1,\beta_i))} \geq 1$, 所以
$$
\det{(E+A) \geq 1}
$$
这里用到了[[Matrix Determinant#对角分块矩阵的行列式|对角分块矩阵的行列式]]
# 正交算子和正交矩阵
设$\mathcal A\in \mathcal{L}(V)$正交, 则存在$\theta_1, \ldots ,\theta_s\in(0,\pi) \cup (\pi,2\pi)$和$\lambda_{2s+1}, \ldots ,\lambda_n\in \left\{ -1,1 \right\}$使得$\mathcal A$在$V$的某组单位正交基下的矩阵为
$$
M=\begin{pmatrix}
N(\cos \theta_1,\sin \theta_1) & & & & &\\
& \ddots & & & &\\
& & N(\cos \theta_s, \sin \theta_s) & & & \\
& & & \lambda_{2s+1} & & \\
& & & & \ddots & \\
& & & & & \lambda_n
\end{pmatrix}
$$
设$A\in \mathrm{O}_n(\mathbb{R})$, 则$A$正交相似于上述形式的矩阵$M$

正交矩阵和正交算子的（复）特征根的模长都等于$1$

设$P\in \mathrm{O}_n(\mathbb{R})$满足$\det{(P)} = -1$, 则$\det{(E+P)} = 0$, 这是因为存在正交矩阵$Q$使得$Q^{-1}PQ=M$, 而$\det{(P)} = -1 \implies \det{(M)} = -1$, 于是存在$j\in \left\{ 2s+1, \ldots ,n \right\}$使得$\lambda_j = -1$, 故$-1$是$M$的特征根, 其必然也是$P$的特征根, 故我们有$\det{(E+P)} = 0$
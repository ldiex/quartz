# 行列式的几何意义
在[[Euclidean Space|Euclidean空间]]$\mathbb{R}^n$中，设$A\in \mathrm{GL}_n(\mathbb{R})$为[[General Linear Group|可逆矩阵]]，则$\left|\det{(A)}\right|$表示由$A$的列向量张成的$2n$面体的体积
# 行列式的性质
一个矩阵的行列式是它所有[[Eigenvectors and Characteristic Polynomial#特征值|特征值]]的乘积(包括相同的特征值), 这是因为我们知道一个矩阵$A\in \mathrm{M}_n(F)$的[[Characteristic Polynomial|特征多项式]]是
$$
\chi_A(t) = \det{(tE - A)}= t^n + a_{n-1}t^{n-1} + \cdots +a_1t + a_0
$$
令$t = 0$即有$\det{(A)} = -a_0$, 根据Vieta定理这就是$\chi_A$的所有根之积, 也就是所有特征值的乘积
# 特殊矩阵的行列式
## 上三角矩阵的行列式
上三角矩阵、下三角矩阵和对角矩阵的行列式都是对角线元素之积
## 对角分块矩阵的行列式
$$
\det \left( \begin{array}{cccc} A_1 \hspace{-5pt} &&& \\ & A_2 \hspace{-5pt} && \\[-3pt] && \ddots \hspace{-5pt} & \\ &&& A_k \end{array} \right) = \det (A_1) \det (A_2) \cdots \det (A_k)
$$
## 2阶分块矩阵的行列式
如果$A$可逆，则有
$$
\begin{aligned}
\det{\begin{pmatrix}
A & B \\ C & D
\end{pmatrix}} = \det{\begin{pmatrix}
A & B \\ O & D-CA^{-1}B
\end{pmatrix}} = \det{(A)} \det{(D-CA^{-1}B)}
\end{aligned}

$$

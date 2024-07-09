# 行列式的几何意义
在[[Euclidean Space|Euclidean空间]]$\mathbb{R}^n$中，设$A\in \mathrm{GL}_n(\mathbb{R})$为[[General Linear Group|可逆矩阵]]，则$\left|\det{(A)}\right|$表示由$A$的列向量张成的$2n$面体的体积
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

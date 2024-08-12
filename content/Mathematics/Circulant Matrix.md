设*循环矩阵*
$$
A = \begin{pmatrix}
a_0 & a_1 & \cdots & a_{n - 2} & a_{n - 1} \\
a_{n - 1} & a_0 & \cdots & a_{n - 3} & a_{n - 2} \\
a_{n - 2} & a_{n - 1} & \cdots &a_{n - 4} & a_{n - 3} \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
a_1 & a_2 & \cdots & a_{n - 1} & a_0 
\end{pmatrix} 
\in M_n(\mathbb R)
$$
设$\epsilon_k = e^{\frac{2k\pi \mathrm i}{n}}\; k = 0, \cdots, n - 1$, 令
$$
f = a_0 + a_1x + \cdots +a_{n - 2}x^{n - 2} + a_{n - 1}x^{n - 1} \in \mathbb C[x]
$$
于是利用$\epsilon_k^n = 1$有
$$
\begin{aligned}
f(\epsilon_k) &= a_0 + a_1 \epsilon_k + \cdots + a_{n - 2}\epsilon_k^{n - 2} + a_{n - 1}\epsilon_k^{n - 1} \\
\epsilon_k f(\epsilon_k) &= a_{n - 1} + a_0\epsilon_k +\cdots +a_{n - 3}\epsilon_k^{n - 2} + a_{n - 2}\epsilon_k^{n - 1} \\
&\vdots \\
\epsilon_k^{n - 1} f(\epsilon_k) &= a_1 + a_2\epsilon_k + \cdots + a_{n - 1} \epsilon_k^{n - 2} + a_0 \epsilon_k^{n - 1}
\end{aligned}
$$
可以写成矩阵形式
$$
f(\epsilon_k) = \begin{pmatrix}
1 \\
\epsilon_k \\
\vdots \\
\epsilon_k^{n - 1}
\end{pmatrix} = A \begin{pmatrix}
1 \\
\epsilon_k \\
\vdots \\
\epsilon_k^{n - 1}
\end{pmatrix}
$$
设
$$
V = \begin{pmatrix}
 1& 1 & \cdots & 1 \\
 \epsilon_0 & \epsilon_1 & \cdots & \epsilon_n \\
 \vdots & \vdots & \ddots & \vdots \\
 \epsilon_0^{n - 1} & \epsilon_1^{n - 1} & \cdots & \epsilon_{n - 1}^{n - 1}
 
\end{pmatrix}
$$
则$V\operatorname{diag}(f(\epsilon_0), \cdots, f(\epsilon_{n-1})) = AV$. 由Vandermonde行列式知$V$可逆，于是
$$
A = V\operatorname{diag}(f(\epsilon_0), \cdots, f(\epsilon_{n-1}) )V^{-1}
$$
两边取行列式有
$$
\det A = f(\epsilon_0) \cdots f(\epsilon_{n - 1})
$$



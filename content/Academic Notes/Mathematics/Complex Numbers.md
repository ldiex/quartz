# $\mathbb{C}$的定义
$$
\mathbb{C} = \left\{ x + y \sqrt{-1} \mid x,y \in \mathbb{R} \right\}
$$
矩阵表示
$$
x + y \sqrt{-1} \sim \begin{pmatrix} x & y \\ -y & x\end{pmatrix}
$$
# 共轭
如果$c = a + b \mathrm{i},\;(a,b\in \mathbb{R})$，则$c$的共轭复数（记为$c^*$或$\bar{c}$）为
$$
c^* = a-b\mathrm{i}
$$
# Euler 公式
$$
e^{i \theta} = \cos \theta + \mathrm{i} \sin \theta
$$
# 单位根
$$
z^n = 1 \; (z \in \mathbb C) \implies z\in \left\{\epsilon_k = e^{\dfrac{2k\pi\mathrm i}{n}} \bigg|\; k =0, 1, \cdots,n - 1\right\}
$$
三元组$(U_n, \cdot, 1)$是循环群. $U_n = \langle \epsilon_\ell \rangle \iff \gcd(\ell, n) = 1$


# 代数学基本定理
设$f \in \mathbb C[x] \backslash \mathbb C$. 则$f$在$\mathbb C[x]$有根
## 推论$1$
设$f \in \mathbb C[x] \backslash \mathbb C$.  则存在互不相同的复数$\alpha_1, \cdots, \alpha_k$和非零正整数$m_1, \cdots, m_k$使得
$$
f = \operatorname{lc}(f)(x-\alpha_1)^{m_1}\cdots(x-\alpha_k)^{m_k}
$$
## 推论$2$
在$\mathbb R[x]$中的不可约元的次数最多为$2$次

# 应用举例
[[Circulant Matrix]]
[[Hamilton Quaternion]]



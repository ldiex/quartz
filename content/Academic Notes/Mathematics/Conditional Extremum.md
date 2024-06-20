# 条件极值
设$U\subset \mathbb{R}^n$为[[Planar Point Set#开集|开集]]，$f:U\to \mathbb{R}$是可微函数，$\Phi:U\to \mathbb{R}^m$是$C^k\;(k\ge1)$映射. 记
$$
\Sigma = \Phi^{-1}(0) = \left\{ x\in U | \Phi(x) = 0 \right\} 
$$
则$f$在$\Sigma$上的极值称为*条件极值*，方程$\Phi(x) = 0$称为*约束条件*

如果对于任意$x\in \Sigma$，矩阵$J\Phi(x)$的[[Matrix Rank|秩]]均为$m$，则称$\Sigma$上的点满足$m$个独立的约束条件。此时利用[[Implicit Function#隐映射定理|隐映射定理]]，知$\Sigma$是$\mathbb{R}^n$中$n-m$维隐式曲面，且$\Sigma$在$x$处的法空间由$\left\{ \nabla \varphi_1(x),\ldots,\nabla \varphi_m(x) \right\}$张成，其中$\varphi_i$是$\Phi$的第$i$个分量（因为$\Sigma$实际上表示了$\Phi$的一个等值面，故$\Sigma$的切平面必然和$\Phi$的每一个分量的[[Differential of Multivariable Functions#梯度|梯度]]垂直），特别地，如果$x^0\in \Sigma$为$f$的[[Extremum of Multivariable Functions#极值定义|极值点]]，则$\nabla f(x^0)$必为$\Sigma$在$x^0$处的法向量。

事实上，设$\gamma(t)$是$\Sigma$上的可微函数曲线，$\gamma(0)=x^0$，则$t = 0$是$f\circ\gamma(t)$的极值点，从而是[[Stationary Point|驻点]]
 $$
 (f\circ\gamma)'(0)=0\iff \nabla f(x^0)\cdot\gamma'(0) = 0
 $$
 注意到$\gamma'(0)$为$\Sigma$在$x^0$处的切向量，由$\gamma$的任意性得到$\nabla f(x^0)$为$\Sigma$在$x^0$处的法向量，因此存在$\lambda_1,\ldots,\lambda_m\in\mathbb{R}$使得
 $$
 \nabla f(x^0) = \sum_{i = 1}^m \lambda_i\nabla\varphi_i(x^0)
 $$
 其中$\left\{ \lambda_i \right\}$称为*Lagrange乘数*

# Lagrange乘数法
设$f,\Phi$如上述定义，$x^0\in\Sigma$为$f$的条件极值点。如果$\mathrm{rank} J\Phi(x^0)=m$，则存在$\lambda\in \mathbb{R}^m$使得
$$
\nabla f(x^0) -\lambda \cdot J\Phi(x^0) = 0
$$
在实际应用中，上式常被解释为，如果$x^0$为极值点，则$(x^0,\lambda)$为辅助函数
$$
\mathcal{L}(x, \lambda) = f(x) - \sum_{i = 1}^m \lambda_i\cdot \varphi_i(x)
$$
的驻点


 
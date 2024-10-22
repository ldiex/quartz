# 商空间
设$U$是$V$的子空间. 我们在$V$上定义如下等价关系
设$\boldsymbol x, \boldsymbol y \in V$, 若$\boldsymbol x - \boldsymbol y \in U$, 则称$\boldsymbol x$和$\boldsymbol y$关于$U$等价. 记为$\boldsymbol x \sim_U \boldsymbol y$
设$\boldsymbol x \in V$且$[\boldsymbol x]$是$\boldsymbol x$所在的等价类, 则
$$
[\boldsymbol x] = \boldsymbol x + U
$$
这意味着
$$
V / {\sim_U} = \{\boldsymbol v + U \mid \boldsymbol v \in V\}
$$
并用$V/U$简记$V / \sim_U$, 并在其上定义如下线性运算
$$
(\boldsymbol x + U) + (\boldsymbol y + U) = (\boldsymbol x+ \boldsymbol y) + U;\quad \alpha(\boldsymbol x + U) = (\alpha \boldsymbol x) + U
$$
则$V/U$是域$F$上的线性空间, 称其为$V$关于$U$的*商空间*, 其中的零向量为$\boldsymbol 0 + U = U$

>[!Tip]
>$$\dim(V / U) = \dim(V) - \dim(U)$$
# 自然的线性映射
设$\pi_U: V \to V/U$是*自然投射*, 即对$\forall \boldsymbol x \in V, \pi_U(\boldsymbol x) = \boldsymbol x + U$, 容易验证$\pi_U$是线性映射

设$\phi: V \to W$是从$V$到$F$上的线性空间$W$的线性映射. 则对$\forall \boldsymbol x, \boldsymbol y \in V$
$$
\phi(\boldsymbol x) = \phi(\boldsymbol y) \iff \phi(\boldsymbol x - \boldsymbol y) = \boldsymbol 0 \iff \boldsymbol x - \boldsymbol y \in \ker(\phi) \iff \boldsymbol x \sim_{\ker(\phi)} \boldsymbol y
$$
故存在唯一的*单射*$\bar \phi: V / \ker(\phi) \to W$使得
$$
\phi = \bar \phi \circ \pi_{\ker(\phi)}
$$
且
$$
\begin{aligned}
\bar \phi : V / \ker(\phi) &\to W \\
\boldsymbol x + \ker(\phi) &\to \phi(\boldsymbol x)
\end{aligned}
$$
## 线性映射基本定理
设$\phi \in \mathrm{Hom}(V, W)$, 其中$W$是$F$上的线性空间. 则存在唯一的线性单射$\bar \phi$使得$\phi = \bar \phi \circ \pi_{\ker(\phi)}$. 特别地, $V/\ker(\phi)$与$\mathrm{im}(\phi)$ [[Linear Isomorphism|线性同构]]


**推论**: 设$V_1, V_2$是$V$的子空间, 则$V_2 / (V_1 \cap V_2)$和$(V_1 + V_2)/ V_1$线性同构

**证明**: 
- 线性映射$\phi: V_2 \to V_1 + V_2$是嵌入
- 线性映射$\pi:V_1 + V_2 \to (V_1 + V_2) / V_1$是自然投射
- 于是$\psi = \pi \circ \phi$是$V_2 \to (V_1 + V_2) / V_1$的线性映射
- 注意到
$$
\begin{aligned}
(V_1 + V_2) /V_1 &= \{(\boldsymbol v_1 + \boldsymbol v_2) + V_1 \mid \boldsymbol v_1 \in V_1, \boldsymbol v_2 \in V_2\} \\
&= \{(\boldsymbol v_2 + V_1 )\mid  \boldsymbol v_2 \in V_2\} 
\end{aligned}
$$
- 故
$$
\psi(\boldsymbol v_2) = \pi \circ \phi(\boldsymbol v_2) = \boldsymbol v_2 + V_1
$$
于是$\psi$是满射
- 若$\boldsymbol v_2\in V_1 \cap V_2$,则$\boldsymbol v_2 + V_1 = V_1$, 即$V_1 \cap V_2 \subset \ker(\psi)$. 反之, 设$\boldsymbol v_2 \in \ker(\phi)$, 则$\psi(\boldsymbol v_2) = \boldsymbol v_2 + V_1 = V_1$, 于是$\ker (\phi) \subset V_1 \cap V_2$. 故有$\ker(\phi) = V_1 \cap V_2$ . 所以由线性映射基本定理, 这两个商空间线性同构

**推论**: 若$V_1 + V_2$是直和, 则$(V_1 + V_2) / V_1$和$V_2$线性同构
- 由上一个推论, $(V_1 + V_2)/ V_1$和$V_2/\{\boldsymbol 0\}$线性同构
- 由$\mathrm{id}_{V_2}$和线性映射基本定理, $V_2$和$V_2/\{\boldsymbol 0\}$线性同构


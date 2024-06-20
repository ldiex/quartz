# 线性映射的矩阵表示
## 线性映射下的矩阵
设$F$是任意域，$V$和$W$是$F$上的线性空间，$\boldsymbol e_1, \ldots, \boldsymbol e_n$是$V$的一组基，$\boldsymbol \varepsilon_1, \ldots, \boldsymbol \varepsilon_n$是$W$的一组基

设$\phi \in \operatorname{Hom}(V, W),\; \boldsymbol v_1, \ldots, \boldsymbol v_k \in V,\;M \in F^{k \times \ell}$. 定义
$$
\phi(\boldsymbol v_1, \ldots, \boldsymbol v_k) := (\phi(\boldsymbol v_1), \ldots, \phi(\boldsymbol v_k))
$$
则
$$
\phi((\boldsymbol v_1, \ldots, \boldsymbol v_k) M) = (\phi(\boldsymbol v_1), \ldots, \phi(\boldsymbol v _k))M
$$
于是，对$\boldsymbol e_j$进行分解
$$
\phi(\boldsymbol e_j) = a_{1,j} \boldsymbol \varepsilon_1 + \cdots + a_{m,j} \boldsymbol \varepsilon_m
$$
其中$j = 1, 2, \ldots, n$. 称
$$
A = \begin{pmatrix}
a_{1, 1} & \cdots & a_{1, n} \\
\vdots & \ddots & \vdots \\
a_{m,1} & \cdots & a_{m,n}
\end{pmatrix}
$$
是$\phi$在基底$\boldsymbol e_1, \ldots, \boldsymbol e_n$和$\boldsymbol \varepsilon_1, \ldots, \boldsymbol \varepsilon_m$下的矩阵表示. 当$V$和$W$的基底选定后$\phi$的矩阵是唯一的，我们有
$$
\phi(\boldsymbol e_1, \ldots, \boldsymbol e_n) = (\boldsymbol \varepsilon_1, \ldots, \boldsymbol \varepsilon_n) A
$$
设$\boldsymbol x = x_1 \boldsymbol e_1 + \cdots + x_n \boldsymbol e_n, \; \phi(\boldsymbol x) = y_1 \boldsymbol \varepsilon_1 + \cdots + y_m \boldsymbol \epsilon_m$则
$$
\begin{pmatrix}
y_1 \\ \vdots \\ y_m
\end{pmatrix} = A \begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix}
$$
> [!Note]
> 设$V = F^n, W = F^m, \boldsymbol e_1, \ldots, \boldsymbol e_n$和$\boldsymbol \epsilon_1, \ldots, \boldsymbol \epsilon_m$都是标准基，则$\phi$的矩阵表示为
> $$
> (\phi(\boldsymbol e_1), \ldots, \phi(\boldsymbol e_n))
> $$

## 线性映射在不同基底下的矩阵
设$\phi \in \operatorname{Hom}(V, W)$. 再设$\boldsymbol e_1', \ldots, \boldsymbol e_n'$是$V$的另一组基，$\boldsymbol \epsilon_1', \ldots, \boldsymbol \epsilon_m'$是$W$的另一组基，且
$$
(\boldsymbol e_1', \ldots, \boldsymbol e_n') = (\boldsymbol e_1, \ldots, \boldsymbol e_n) P ,\quad (\boldsymbol \epsilon_1', \ldots, \boldsymbol \epsilon_m') = (\boldsymbol \epsilon_1, \ldots, \boldsymbol \epsilon_m) Q
$$
其中$P \in \mathrm{GL}_n(F), Q \in \mathrm{GL}_m(F)$. 如果$\phi$在$\boldsymbol e_1, \ldots, \boldsymbol e_n; \boldsymbol \epsilon_1, \ldots, \boldsymbol \epsilon_m$下的矩阵是$A$，则$\phi$在$\boldsymbol e_1', \ldots, \boldsymbol e_n'; \boldsymbol \epsilon_1', \ldots, \boldsymbol \epsilon_m'$下的矩阵为$Q^{-1}AP$

> [!Note] 
> 上述结论说明线性映射在不同基底下的矩阵有相同的秩. 设$B \in F^{m \times n}$， 则$B$是$\phi$在$V$和$W$某组基底下的矩阵**当且仅当**$A \sim_e B$，即$\mathrm{rank}(A) = \mathrm{rank}(B)$

因此，我们可以用表示矩阵的秩来定义线性映射$\phi$的*秩*，记为$\mathrm{rank}(\phi) = \mathrm{rank}(A)$. 并且，由打洞引理，存在一组基底使得$\phi$的矩阵为
$$
M = \begin{pmatrix}
E_r & O \\ O & O
\end{pmatrix}_{m \times n}
$$
其中$r = \mathrm{rank}(M) = \mathrm{rank}(\phi) = \dim(\mathrm{im}(\phi))$

> [!Tip]
> 1. $\phi$是单射当且仅当$\mathrm{rank}(\phi) = \dim(V)$, 即$\mathrm{rank}(A) = n$
> 2. $\phi$是满射当且仅当$\mathrm{rank}(\phi) = \dim(W)$, 即$\mathrm{rank}(A) = m$
> 3. $\phi$是双射当且仅当$A$是可逆方阵
## 线性映射的复合
在选定的基底下，设$A = A_\phi, B = A_\psi$，则$\psi \circ \phi$的矩阵表示是$BA$
## 线性同构
设
$$
\begin{aligned}
\Phi : \operatorname{Hom}(V, W) &\to F^{m \times n} \\
\phi & \to A_\phi
\end{aligned}
$$
则$\Phi$是[[Linear Isomorphism|线性同构]]

由此可知$\dim(\operatorname{Hom}(V, W)) = mn$
## 对偶映射
设$\phi \in  \operatorname{Hom}(V, W)$，则
$$
\begin{aligned}
\phi^* : W^* &\to V^* \\
f &\to f \circ \phi
\end{aligned}
$$
是线性映射。且若$\phi$在某两个基底下的矩阵为$A$，则*对偶映射*$\phi^*$在这两组基底的[[Dual Space#对偶基|对偶基]]下的矩阵是$A^t$

> [!Note]
> 由此可推出，$\phi$和$\phi^*$的秩相等


# 对偶空间
设$V = F^n$, 线性空间$\mathrm{Hom}(V, F)$称为$V$的*对偶空间*，记为$V^*$. 换言之，$V^*$是$V$上所有[[Linear Map|线性函数]] 的集合，其中的加法和数乘由$\mathrm{Map}(V, F)$给出.
# 对偶基
设$\boldsymbol e_1, \cdots, \boldsymbol e_n$是$V$的一组基，则在$V^*$中存在唯一的一组基$\boldsymbol e_1^*, \cdots, \boldsymbol e_n^*$满足$\boldsymbol e_i^* (\boldsymbol e_j) = \delta_{i, j},\; \forall i,j \in [n]$. 特别地，$\dim(V^*) = n$. 其中$\delta_{i, j}$为[[Kronecker Delta|Kronecker Delta 函数]]

称$\boldsymbol e_1^*, \cdots, \boldsymbol e_n^*$为$\boldsymbol e_1, \cdots, \boldsymbol e_n$的*对偶基*

这里对$\forall \boldsymbol v \in V$, $\boldsymbol e_i^*(\boldsymbol v)$就是取$\boldsymbol v$在基底$\boldsymbol e_i$上的坐标，由此我们可以知道**对偶空间和原空间是一一对应的**

我们可以把$\boldsymbol e_i^*(\boldsymbol v)$ 看做*内积*

# 对偶的对偶
下列映射
$$
\begin{aligned}
\phi: V &\to V^{**} \\
\boldsymbol v &\to \epsilon_{\boldsymbol v}
\end{aligned}
$$
是[[Linear Isomorphism|线性同构]] , 其中
$$
\begin{aligned}
\epsilon_{\boldsymbol v}: V^* &\to F \\
f &\to f(\boldsymbol v)
\end{aligned}
$$
这个线性同构$\phi$的定义和基底无关，此时我们说$V$和$V^{**}$*自然同构*

# 向量和映射的统一
对偶空间中的线性映射和原空间中的向量一样多，说明两者地位相同. 映射可以作用于向量，向量也应该可以作用于映射，这实际上就是**把向量看做成了映射的映射**


# 对偶映射
见[[Matrix Representation of Linear Map#对偶映射|对偶映射]]




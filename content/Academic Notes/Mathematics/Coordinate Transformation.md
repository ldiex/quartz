# 坐标
设$\boldsymbol v_1, \cdots, \boldsymbol v_n$是$V$的一组基, 对任意的$\boldsymbol x \in V$, 存在唯一的$x_1, \cdots, x_n \in F$使得
$$
\boldsymbol x = x_1 \boldsymbol v_1 + \cdots + x_n \boldsymbol v_n
$$
则称$(x_1, \cdots, x_n)^t$是$x$在基底$\boldsymbol v_1, \cdots, \boldsymbol v_n$的*坐标*

# 坐标变换
设$\boldsymbol e_1, \cdots, \boldsymbol e_n$是$V$的一组基, $\boldsymbol e_1' , \cdots , \boldsymbol e_n' \in V.$ 则$\boldsymbol e_1', \cdots, \boldsymbol e_n'$是$V$的一组基当且仅当存在唯一的$P \in \mathrm{GL}_n(F)$使得
$$
(\boldsymbol e_1', \cdots, \boldsymbol e_n') = (\boldsymbol e_1, \cdots, \boldsymbol e_n) P
$$
并称$P$是*转换矩阵* 
($\mathrm{GL}_n(F)$参考[[General Linear Group | 一般线性群]])

由此得到*坐标变换*
$$
\begin{pmatrix}
x_1' \\ \vdots \\ x_n'
\end{pmatrix} = P^{-1} \begin{pmatrix}
x_1' \\ \vdots \\ x_n'
\end{pmatrix}
$$
> [!Tip] 注意
> **基底**变换是基底矩阵**右乘**转换矩阵；而**坐标**变换是**左乘**转换矩阵的**逆矩阵**







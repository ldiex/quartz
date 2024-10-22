# 定义
设[[Bilinear Form|双线性型]]$f \in \mathcal L_2(V)$, 若对任意$\boldsymbol x, \boldsymbol y \in V$, 有
$$
0 = f(\boldsymbol x, \boldsymbol y) + f(\boldsymbol y, \boldsymbol x)
$$
则称$f$为*斜对称双线性型*, 记为$f \in \mathcal L_2^-(V)$

设$f \in \mathcal L_2(V)$, 则$f \in \mathcal L_2^- (V)$当且仅当对任意$\boldsymbol x \in V, f(\boldsymbol x, \boldsymbol x) = 0$

# 性质
## 判定线性无关
设$f \in \mathcal L_2^-(V), \; \boldsymbol u, \boldsymbol v \in V$使得$f(\boldsymbol u, \boldsymbol v) \neq 0$, 则$\boldsymbol u, \boldsymbol v$线性无关

# 辛平面（sympletic plane）
## 定义
设$f \in \mathcal L_2^-(V), \; \boldsymbol u, \boldsymbol v \in V$使得$f(\boldsymbol u, \boldsymbol v) \neq \boldsymbol 0$. 则$\langle \boldsymbol u, \boldsymbol v \rangle$称为$f$的*辛平面*

## 基底
设$f \in \mathcal L_2^-(V)$, $W$是$f$的辛平面, $\boldsymbol w_1, \boldsymbol w_2$是$W$的一组基, 则$f(\boldsymbol w_1, \boldsymbol w_2) \neq 0$

## 线性空间的辛平面分解
设$V$是$F$上的$n$维线性空间, $f \in \mathcal L_2^-(V)$, $W$是$f$的辛平面. 则存在$V$中的[[Linear Space#子空间|子空间]]$\widetilde{W}$满足对任意的$\boldsymbol x \in W,\; \boldsymbol y \in \widetilde W$使得$f(\boldsymbol x, \boldsymbol y) = 0$, 且$V = W \oplus \widetilde W$

设$V$是$F$上的有限维线性空间, $f \in \mathcal L_2^-(V)$. 则存在$f$的辛平面$W_1, \ldots, W_k$和子空间$U$满足
1. $V = W_1 \oplus \cdots \oplus W_k \oplus U$
2. $f|_{U \times U}$是零双线性型
3. 对任意$i \in \{1, 2, \ldots, k\},\; \boldsymbol x \in W_1 \oplus \cdots \oplus W_i,\; \boldsymbol y \in W_{i + 1} \oplus \cdots \oplus W_k \oplus U$, 我们有$f(\boldsymbol x, \boldsymbol y) = 0$

> [!tip] 推论
> 设$V$是$F$上$n$维线性空间, $f \in \mathcal L_2^-(V)$. 则存在$V$的一组基$\boldsymbol e_1, \ldots, \boldsymbol e_n$使得$f$在该基下的矩阵等于
> $$
> M = \begin{pmatrix}
> S_2 & & & & \\
> & S_2 & & & \\
> & & \ddots & & \\
> & & & S_2 & \\
> & & & & O_{(n - 2k) \times (n - 2k)}
> \end{pmatrix}
> $$
> 其中
> $$
> S_2 = \begin{pmatrix}
> 0 & 1 \\ -1 & 0
> \end{pmatrix}
> ,\; 2k = \mathrm{rank}(f)
> $$

> [!Note] 由此可知
> $F$上奇数阶斜对称方阵的行列式等于$0$;  偶数阶写对称方阵的行列式等于$F$中某个元素的平方


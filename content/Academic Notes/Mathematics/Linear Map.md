# 定义
设$\phi: V \to W$. 如果对$\forall \alpha,\beta \in F, \; \boldsymbol u, \boldsymbol v \in V$都有$\phi(\alpha \boldsymbol u + \beta \boldsymbol v)  = \alpha \phi(\boldsymbol u) + \beta \phi(\boldsymbol v)$, 则称$\phi$是从$V$到$W$的一个*线性映射*

$\phi$是[[Injective, Surjective and Bijective#Injective (One-to-One)|单射]]当且仅当$\ker (\phi) = \{\boldsymbol 0_V\}$

设$V = F^n, W = F^m$, 则$\phi: V \to W$是线性映射当且仅当存在$A \in F^{m \times n}$使得
$$
\forall \boldsymbol x \in V,\; \phi(\boldsymbol x) = A \boldsymbol x
$$
# 运算
令$\mathrm{Hom}(V,W)$是从$V$到$W$的所有线性映射的集合. 它是$\mathrm{Map}(V, W)$的子集. 

可以直接验证, 对任意的$\alpha, \beta \in F, \phi, \psi \in \mathrm{Hom}(V, W)$, 有$\alpha \phi + \beta \psi \in \mathrm{Hom}(V,W)$. 故$\mathrm{Hom}(V,W)$是[[Linear Space|线性空间]]

同样, 设$\phi \in \mathrm{Hom}(U, V), \psi \in \mathrm{Hom}(V, W)$, 则有$\psi \circ \phi \in \mathrm{Hom}(U,W)$

# 性质
一个线性映射$\phi: V \to W$是[[Injective, Surjective and Bijective#Injective (One-to-One)|单射]]当且仅当$\ker(\phi) = \{\boldsymbol 0\}$
一个线性映射$\phi: V \to W$是[[Injective, Surjective and Bijective#Surjective (Onto)|满射]]当且仅当$\mathrm{im}(\phi) = W$
如果$\dim(V) = \dim(W)$, 则$\phi$是单射当且仅当$\phi$是满射
# 线性映射基本定理
设$\phi:V \to W$是线性映射, 则
$$
V / {\ker \phi} \cong \mathrm{im} \phi
$$

其中$V/\ker\phi$表示一个[[Quotient Space|商空间]], $\cong$代表[[Linear Isomorphism|线性同构]]. 这个式子两边取维数, 就有
$$
\dim(\ker \phi) + \dim(\mathrm{im} \phi) = \dim V
$$
这被称为*对偶定理*, 或者*Rank-Nullity定理*

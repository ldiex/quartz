# 定义
## 循环子空间
设$\mathcal A \in \mathcal{L}(V)$和$\boldsymbol v \in V$. 由$\boldsymbol v,\mathcal A(\boldsymbol v), \mathcal A^2(\boldsymbol v),\ldots$生成的子空间被称为由$\mathcal A$和$\boldsymbol v$生成的*循环子空间*. 记为$F[\mathcal A]\cdot \boldsymbol v$，或者表示成[[Invariant Subspace#线性轨道|线性轨道]]的形式$[\boldsymbol v]$

循环子空间包含了任意$\mathcal A$的多项式在$\boldsymbol v$上的作用，也就是说$F[\mathcal A]\cdot \boldsymbol v = \left\{ p(\mathcal A)(\boldsymbol v) \mid p(t)\in F[t]\right\}$

特别地，如果$\boldsymbol v$是$\mathcal A$的[[Eigenvectors and Characteristic Polynomial#特征向量|特征向量]]，则有$F[\mathcal A]\cdot \boldsymbol v =[\boldsymbol v]= \left< \boldsymbol v \right>$

## 循环空间和循环算子
设$\mathcal A \in \mathcal{L}(V),\; \boldsymbol v \in V$. 如果$V = F[\mathcal A]\cdot \boldsymbol v$，则称$\mathcal A$是$V$上的*循环算子*，$\boldsymbol v$是$V$中的*循环向量*，$V$是关于$\mathcal A, \boldsymbol v$的*循环空间*，简称 *$\mathcal A$-循环空间*

> [!Tip]
> 我们可以用任意的$\mathcal A\in \mathcal{L}(V), \boldsymbol v\in V$生成一个循环子空间，当我们选择一个合适的$\boldsymbol v$使得这个循环子空间就是$V$本身时，我们才能称$V$是$\mathcal A$-循环空间
# 极小多项式的构造
## 极小多项式$\to$线性算子
我们将说明，**任何一个首一多项式都可以是某一个线性算子$T$的[[Minimal Polynomial|极小多项式]]**

设$p(t) = t^n +a_{n-1}t^{n-1} + \cdots + a_1 t+a_0 \in F[t]$.  令$V = F^n$的标准基为$\boldsymbol e_1,\ldots, \boldsymbol e_n$，考虑下述线性映射
$$
\begin{aligned}
T_p:V&\to V \\ 
\boldsymbol e_i &\to T_p(\boldsymbol e_i)
\end{aligned}
$$
其中
$$
T_p(\boldsymbol e_i) = \begin{cases}
\boldsymbol e_{i + 1}, & 1 \le i \le n -1 \\
-a_0\boldsymbol e_1-\cdots-a_{n-1}\boldsymbol e_n, & i = n
\end{cases}
$$
于是有
$$
\begin{aligned}
p(T_p)\boldsymbol e_1 &= (T_p^n+a_{n-1}T_p^{n-1}+\cdots + a_1T_p + a_0)\boldsymbol e_1 \\
&= T_p\boldsymbol e_n+a_{j-1}\boldsymbol e_n +a_{n-2}\boldsymbol e_{n -1}+\cdots +a_1\boldsymbol e_2 +e_0\boldsymbol e_1 = 0
\end{aligned}
$$
同理有$p(T_p)\boldsymbol e_2 = p(T_p)T_p\boldsymbol e_1= T_pp(T_p)\boldsymbol e_1 = 0$，于是$p(T_p)\boldsymbol e_i = 0,\; \forall 1\le i \le n$，这说明$p$是$T_p$的一个*零化多项式*，那么便有$\mu_{T_p} \mid p$

另一方面，我们又有$V = [\boldsymbol e_1] = F[T_p]\cdot \boldsymbol e_1$，所以$T_p$[[Minimal Polynomial#零化某个向量的极小多项式|零化]]$\boldsymbol e_1$的极小多项式的次数是$\dim V = n$. 又因为$\mu_{T_p,\boldsymbol e_1} \mid \mu_{Tp}$，故有$\deg \mu_{T_p}\ge n$，于是只能有$p = \mu_{T_p}$
## 线性算子$\to$极小多项式
如果$n$维线性空间$V$是$T$-循环的，设$V =F[T]\cdot \boldsymbol v$，则
$$
V = \left< \boldsymbol v,T \boldsymbol v,T^2\boldsymbol v,\ldots \right> 
$$
因为$n=\dim(V)$是有限的，则必然存在一个$i$使得
$$
T^i \boldsymbol v \in \left< \boldsymbol v,T\boldsymbol v,\ldots,T^{i-1}\boldsymbol v \right> 
$$
于是
$$
T^{i+1} \boldsymbol v \in \left< \boldsymbol v,T\boldsymbol v,\ldots,T^{i}\boldsymbol v \right>  = \left< \boldsymbol v,T\boldsymbol v,\ldots,T^{i-1}\boldsymbol v \right> 
$$
同样对任意$k \ge i$有$T^k \boldsymbol v \in \left< \boldsymbol v,T\boldsymbol v,\ldots,T^{i-1}\boldsymbol v \right>$，结合$V$的维数是$n$，所以
$$
V =\left< \boldsymbol v,T\boldsymbol v,\ldots,T^{n-1}\boldsymbol v \right> 
$$
那么$T^n\boldsymbol v$必然是上述基底的线性组合，将其写作
$$
T^n\boldsymbol v = -a_0\boldsymbol v-a_{1}T\boldsymbol v - \cdots - a_{n-1}T^{n-1}\boldsymbol v
$$
其系数对应的多项式
$$
p(t) = t^n +a_{n-1}t^{n-1} + \cdots + a_1 t+a_0 \in F[t]
$$
自然就是$T$的极小多项式，也就是说$T$的极小多项式是它的*友阵(Frobenius块)*
$$
F = \begin{pmatrix}
0 & 0 & \cdots & 0 & -a_0 \\
1 & 0 & \cdots & 0 & -a_1 \\
0 & 1 & \cdots & 0 & -a_2 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & \cdots & 1 & -a_{n-1}
\end{pmatrix}
$$
的特征多项式
# 性质
## 极小多项式
在上面已经构造出了$\mu_\mathcal A =p(t)$的形式，可知$\dim(\mu_\mathcal A) = n =\dim(\chi_\mathcal A)$，又因为$\mu_\mathcal A \mid \chi_\mathcal A$，所以就有$\mu_\mathcal A = \chi_\mathcal A$，也就是$\mathcal A$的[[Minimal Polynomial|首一极小多项式]]等于它的[[Characteristic Polynomial|特征多项式]]

相反，如果$\mu_\mathcal A = \chi_\mathcal A$，也可以推出$V$是$\mathcal A$-循环的. 
## 不变子空间 
 $F[\mathcal A]\cdot \boldsymbol v$是$\mathcal A$-[[Invariant Subspace|不变]]的，因为$F[\mathcal A]\cdot\boldsymbol v$自然包含了所有对$\mathcal A$的多项式作用的结果，它自然是$\mathcal A$封闭的
 
循环空间的所有不变子空间都是循环空间. 
## 维数
循环子空间的维数和$\mathcal A$的零化$\boldsymbol v$的极小多项式的次数一致，即$\dim(F[\mathcal A]\cdot \boldsymbol v) =\deg \mu_{\mathcal A,\boldsymbol v}$

如果$V = F[\mathcal A]\cdot \boldsymbol v$是循环空间，则$\dim{(V)} = \deg{\mu_{\mathcal A, \boldsymbol v}}$，又$\deg{\mu_{\mathcal A}} \leq \deg{\chi_{\mathcal A}}= \dim{(V)}$且$\mu_{\mathcal A,\boldsymbol v} \mid \mu_{\mathcal A} \implies \deg{(\mu_{\mathcal A, \boldsymbol v}) \leq \deg{(\mu_{\mathcal A})}}$，故有$\dim(V) = \deg \mu_{\mathcal A,\boldsymbol v} =\deg \mu_\mathcal A$，且$\mu_{\mathcal A,\boldsymbol v} = \mu_{\mathcal A}$

反过来，若设$d = \deg \mu_\mathcal A$则存在$\boldsymbol v \in V$使得
$$
\dim (F[\mathcal A]\cdot \boldsymbol v) = d
$$
且不存在维数大于$d$的$\mathcal A$-循环子空间，也就是说，有$\mathcal A,\boldsymbol v$生成的循环子空间的最大维数就是$\mathcal A$的极小多项式的次数
# 循环子空间分解
设$\mathcal A \in \mathcal{L}(V)$，则存在
$$
\boldsymbol v_1, \ldots, \boldsymbol v _{\ell} \in V \backslash \left\{ \boldsymbol 0 \right\} 
$$
使得
$$
V = (F[\mathcal A]\cdot \boldsymbol v_1) \oplus \cdots \oplus(F[\mathcal A]\cdot \boldsymbol v_{\ell})
$$
其中$W_i = F[\mathcal A]\cdot \boldsymbol v_i$都是$\mathcal A$-不可分的. 
# 循环定理
**下面证明若$V$是$T$-循环空间，那么对于$V$的每一个$T$-子空间$W$，存在$\mu_T$的一个因子$f$使得$W =\ker f$**

设$V = F[T]\cdot \boldsymbol v$是$n$维循环空间，且有极小多项式$\mu_T$
考虑$\mu_T$的每一个首一的多项式因子$f$，设$fg = \mu_T$，则有$f(T)g(T)\boldsymbol v = \boldsymbol 0$，于是$g(T)\boldsymbol v \in \ker f(T)$，进一步得到$[g(T)\boldsymbol v] = F[T]\cdot g(T)\boldsymbol v \subset \ker f(T)$. 

由循环子空间的[[Cyclic Subspace#维数|维数性质]]，
$$
\dim[g(T)\boldsymbol v] = \deg \mu_{T,g(T)\boldsymbol v}
$$
和零化某个向量的极小多项式的[[Minimal Polynomial#零化某个向量的极小多项式的性质|多项式变换性质]]
$$
\begin{aligned}
\mu_{T,\boldsymbol v}  & = \mu_{T,g(T)\boldsymbol v}\cdot \gcd(g,\mu_{T,\boldsymbol v})  \\
\implies \mu_{T,\boldsymbol v}  & = \mu_{T,g(T)\boldsymbol v}\cdot \gcd(g,\mu_{T})\\
\implies n  & = \deg \mu_{T,g(T)\boldsymbol v} \cdot\deg g
\end{aligned}
$$
则有
$$
\dim[g(T)\boldsymbol v] = \deg f
$$
同理有
$$
\dim[f(T)\boldsymbol v] = \deg g
$$
于是
$$
\begin{aligned}
\dim \ker f(T) &= \dim V - \dim f(T)V  = n - \dim[f(T)\boldsymbol v] \\
&= n - \deg g = \deg f = \dim[g(T)\boldsymbol v]
\end{aligned}
$$
所以$[g(T)\boldsymbol v] = \ker f(T)$

再利用一次零化某个向量的极小多项式的[[Minimal Polynomial#零化某个向量的极小多项式的性质|多项式变换性质]]，我们有
$$
\mu_{T|_{\ker f(T)}} = \mu_{T|_{[g(T)\boldsymbol v]}} = \mu_{T,g(T)\boldsymbol v}  = \dfrac{\mu_T}{\gcd(\mu_T,g)} = \dfrac{\mu_T}{g} =f \tag{1}
$$
设$W$是$T$-不变子空间，那么由[[Minimal Polynomial#和极小多项式之间的联系|零化某向量的极小多项式总存在“同归于尽”向量]]，存在$\boldsymbol w\in W$满足$\mu_{T|_{W}}=\mu_{T|_{W},\boldsymbol w}$，设$\mu_T = f\mu_{T|_{W}}$，利用上面证明的结论$(1)$就有
$$
[\boldsymbol w] \subset W \subset \ker \mu_{T|_{W}} =\ker \mu_{T|_{W},\boldsymbol w} = [f(T)\boldsymbol v]
$$
继续利用[[Minimal Polynomial#零化某个向量的极小多项式的性质|多项式变换性质]]，得到$\mu_{T,f(T)\boldsymbol v} =\dfrac{\mu_T}{\gcd(\mu_T,f)} = \dfrac{\mu_T}{f}=\mu_{T|_W}$，于是有
$$
\dim [f(T)\boldsymbol v] =  \deg \mu_{T,f(T)\boldsymbol v} = \deg \mu_{T|_W} = \deg \mu_{T|_W,\boldsymbol w} = \dim[\boldsymbol w]
$$
于是就有
$$
W = [f(T)\boldsymbol v]
$$
是循环空间
# Hamilton-Cayley定理加强版
设$\mathcal A \in \mathcal{L}(V)$，则
1. $\chi_\mathcal A(\mathcal A)= \mathcal O$，即$\mu_\mathcal A(t) \mid \chi_\mathcal A(t)$
2. $\chi_A(t)$在$F[t]$的[[Unique Factorization Domain, UFD#不可约元|不可约]]因子都是$\mu_\mathcal A(t)$的因子，也就是说，**这两个多项式的根都是一样的**

其中2.可具体为L设$\mathcal A \in \mathcal{L}(V)$, $\mu_\mathcal A = p_1^{m_1}\cdots p_s^{m_s}$是$\mu_\mathcal A$在$F[t]$中的不可约分解，则$\chi_\mathcal A$在$F[t]$中的不可约分解为
$$\chi_{\mathcal A} = p_1^{n_1}\cdots p_s^{n_s}
$$
其中$m_1\le n_1,\ldots, m_s \le n_s$且$n_1\deg(p_1) + \cdots + n_s\deg(p_s)=n$

	
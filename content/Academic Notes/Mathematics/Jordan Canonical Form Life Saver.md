# 一般方法
给定一个$F$上的[[Linear Space|线性空间]]$V$和一个定义在其上的[[Linear Operator|线性算子]]$\mathcal A\in \mathcal{L}(V)$, 我们可以对$V$作[[Invariant Subspace#不可分子空间|不可分]]子空间[[Linear Space#子空间的直和|直和]]分解
$$
V = W_1 \oplus  \cdots \oplus  W_k
$$
其中每一个$W_i$都是$\mathcal A$-不可分子空间, 这个性质等价于一下两条的联立: 
1. $W_i$是$\mathcal A$-[[Cyclic Subspace|循环子空间]]
2. 设$\mathcal A_i=\mathcal A_{W_i}$为把$\mathcal A$的定义域限制在$W_i$上的新算子, 则$\mathcal A_i$的[[Minimal Polynomial|极小多项式]]$\mu_i = \mu_{\mathcal A_i}$是$F[t]$中某个[[Unique Factorization Domain, UFD#不可约元|不可约多项式]]的幂次

我们称这里的每一个$\mu_i$为$\mathcal A$的一个*初等因子*, 这些$\mu_i$是可以重复的, 所以我们通过一个[[Elementary Divisors#重集|重集]]来将这些初等因子放在一起, 称为$\mathcal A$关于上述不可分因子直和分解的[[Elementary Divisors#初等因子组|初等因子组]], 记为$\left\{ \mu_1, \ldots ,\mu_k \right\}$

考虑每一个初等因子$p^{m}$, 其中$p$是$F[t]$中的一个不可约元, 它们都对应着一个[[Jordan Canonical Form#Jordan块|Jordan块]]$J_m(\lambda)$, 其中Jordan块的大小$m$就是$p$在该初等因子中的[[Gauss's Lemma and Eisenstein's Irreducibility Criterion#重数|重数]], 而$\lambda$则是$p(\lambda)=0$的解. 如果$\lambda$不唯一或者不存在, 我们这样的$\mathcal A$的Jordan标准型就有可能不存在, 具体细节不在此讨论

假设相同的初等因子$p^m$在初等因子组中出现了$n$次, 在最后的[[Jordan Canonical Form#Jordan标准型的形式|Jordan标准型]]中$J_m(\lambda)$也就相应地出现了$n$次

把这些$J_n(\lambda)$在对角线上排列后（无所谓顺序）得到的大矩阵就是$\mathcal A$的Jordan标准型$J_A$, 也就是
$$
J_A = \mathrm{diag}(J_{{n_1}}(\lambda_1), \ldots ,J_{n_k}(\lambda_k))
$$
所以要计算Jordan标准型, 关键就是要确定这些初等因子, 也就是
1. 有哪些可能的初等因子$p^m$
2. 每一种初等因子分别出现了几次

对第一个问题, 我们只需要计算$\mathcal A$[[Matrix Representation of Linear Map|对应的矩阵表示]]$A$的[[Characteristic Polynomial|特征多项式]], 根据[[Cyclic Subspace#Hamilton-Cayley定理加强版|Hamilton-Cayley定理加强版]], $A$的特征多项式和极小多项式具有相同的不可约因子, 而由于$\mu_{\mathcal A_i} | \mu_{\mathcal A}$, 所以$\mu_i = \mu_{\mathcal A_i}$的全部不可约因子都可以在$\chi_{A}$中找到, 且$\chi _A$中的每一个不可约因子都是某个$\mu_i$的不可约因子

对于第二个问题, 如果我们已经找到了所有可能的$p$, 我们就可以利用一个递推公式来计算$p^m$在初等因子组中出现的次数

我们设从$\chi_A$找到的所有不可约因子为$p_1, \ldots ,p_s$, 且设$\deg{p_i} = d_i$, 那么$p_i^\ell$在初等因子组中出现的次数$N(i,\ell)$为
$$
N(i,\ell) = \dfrac{1}{d_i}\left( R(i,\ell -1)+R(i,\ell + 1)-2R(i,\ell) \right) 
$$
其中$R(i,j) = \mathrm{rank}(p_i^j(\mathcal A)),\; j \in \mathbb{N}$, 这给出了计算Jordan标准型的一般方法

# 复数域的情况
我们来具体讨论复数域上的特例, 因为$\mathbb{C}[t]$中的不可约因子都是一次的, 所以这时候初等因子的形式为$\mu_i = (t-\lambda_i)^{m_i}$, 其中$m_i = \dim{(W_i)}$, 这是因为$W_i$是循环空间, 所以$\mu_i$和$\mathcal A_i$的[[Characteristic Polynomial|特征多项式]]$\chi_i$相同, 又$\chi_A$的次数等于$W_i$的维数, 所以$\deg{(\mu_i)} = \dim{(W_i)}$

对于每一个特征根$\lambda_i$, $(t-\lambda_i)^\ell$出现的次数为
$$
N(i, \ell) = R(i,\ell-1) + R(i,\ell + 1) - 2R(i, \ell)
$$
其中$R(i,j) = \mathrm{rank}{((A-\lambda_iE)^j)}$. 
# 利用更多的信息
上面的计算对于高阶矩阵来说比较麻烦, 所以我们考虑是否有其他的信息能帮助我们更方便地确定Jordan标准型的形式

我们可以直接从$\mathcal A$的矩阵表示求出$\chi_{\mathcal A}$, 上面的标准算法中我们只利用了$\chi_A$的不可约因子, 而没有利用它们对于的重数（也就是所谓的[[Eigenvectors and Characteristic Polynomial#维数和重数|代数重数]]）, 考虑所有初等因子的乘积
$$
p_\mu = \mu_1 \cdots \mu_n
$$
由于$W_i$都是循环的, 所以$\deg{(\mu_i)} = \deg{(\chi_i)}= \dim{(W_i)}$, 根据直和的性质, 我们知道$\displaystyle\deg{(p_\mu)} = \sum_i \deg{(\mu_i)}= \sum_i\dim{(W_i)}=\dim{(V)} = \deg{(\chi_{\mathcal A})}$, 而又由于$\mu_i \mid \mu_{\mathcal A} = \chi_{\mathcal A}$, 所以$p_\mu \mid \chi_{\mathcal A}$, 这两者又恰好维数相等, 故而
$$
\chi_{\mathcal A} = \mu_1 \cdots \mu_n
$$
这说明了$\chi_{\mathcal A}$中每个不可约因子$(t-\lambda_i)$的重数就是每个$\lambda_i$的Jordan块的大小的和, 也就是对应的$\lambda_i$在Jordan标准型的对角线上出现的次数

如果我们还知道极小多项式$\mu_{\mathcal A}$, 我们就得到了每一个$p=t-\lambda$在$\mu_\mathcal A$中的重数, 事实上, 由于$\mu_i \mid \mu_{\mathcal A}$, 故我们有
$$
\mu_\mathcal A = \mathrm{lcm}(\mu_1, \ldots ,\mu_n)
$$
从而如果某个$t-\lambda$在$\mu_{\mathcal A}$的重数$m$, 那么必然存在一个初等因子$(t-\lambda)^m$

以上两个新增信息可以帮我们快速确定一些矩阵的Jodran标准型, 例如

已知复方阵$A$的特征多项式和极小多项式分别为
$$
\begin{aligned}
\chi_A  & = (t-1)^4(t+1)^3t^2 \\
\mu_A  & = (t-1)^3(t+1)^3t^2
\end{aligned}
$$
对于特征值$1$, 其代数重数为$4$, 则知$1$在对角线上出现了$4$次；而由于$t-1$在$\mu_A$中的重数为$3$, 则知存在一个$J_3(1)$, 且这是最大的$1$的Jordan块

所以只能有一种情况, 就是存在两个关于$1$的Jordan块$J_3(1),J_1(1)$

对于特征值$-1$和$0$, 同理知道它们对应的Jordan块只能是$J_3(-1);J_2(0)$

综上
$$
A \sim \mathrm{diag}(J_1(1),J_3(1),J_3(-1),J_2(0))
$$





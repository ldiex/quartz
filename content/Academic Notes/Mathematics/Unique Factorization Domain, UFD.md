**记号**：设$D$是[[Integral Domain | 整环]]. 则$D^* = D \backslash \{0\}$ 且$U_D$是$D$中所有可逆元的集合.
# 唯一因子分解整环
## 不可约元和素元
### 不可约元
设$a \in D^*$不可逆. 如果不存在非可逆元$b, c \in D^* \text{ s.t. } a = bc$，则称$a$为*不可约元*
一个等价的定义是，若不可逆元$a = bc$, 则$b, c$中有可逆元

反之，若$a$不是不可约元，则必然存在非可逆元$b, c \in D^* \text{ s.t. } a = bc$ ^flag1

设$a, b \in D$且$a \approx b$, 则$a$不可约当且仅当$b$不可约. 设$a,b \in D$是不可约元，如果$a | b$，则$a\approx b$

**例子**：
$\mathbb{Z}$中的不可约元是所有的素数和它们的相反数
$\mathbb C[x]$中的不可约元是所有的一次多项式（*代数基本定理*）
$\mathbb R[x]$中的不可约元的次数不大于$2$
$F[x]$中的不可约元就是其中的不可约多项式

### 素元
设$p \in D^*$不可逆. 如果对于$\forall a, b \in D^*$
$$
p | ab \implies p | a \vee p | b
$$
则称$p$是*素元*

设$a, b \in D$且$a \approx b$, 则$a$是素元当且仅当$b$是素元
设$p \in D$是素元，$a_1, \cdots, a_n \in D$. 如果$p | a_1\cdots a_n$, 则存在$i \in \{1, \cdots, n\} \text{ s.t. } p | a_i$

**引理**: 整环中的素元都是不可约元
**反例**: 整环中的不可约元不一定是素元，如在$\mathbb{Z}[\sqrt{-5}]$ (环中元素形如$a + b\sqrt{-5}; a, b \in \mathbb{Z}$) 中
$$
6 = (1 -\sqrt{-5})(1 + \sqrt{-5}) = 2 \cdot 3
$$
显然$2, 3$是不可约元，但不是素元
**引理**: 在$\mathbb{Z}$和$F[x]$中，不可约元都是素元

**注意：不可约元的相伴依然是不可约元，素元的相伴依旧是素元**

## 唯一因子分解整环
### 不可约分解
设$a \in D^*$是不可逆元. 如果存在不可约元$p_1, \cdots, p_n$使得
$$
a = p_1 \cdots p_n
$$
则称$a$有*不可约分解*. 上式则称为$a$的一个不可约分解
每一个绝对值大于$1$的整数都有不可约分解

**例子**: 设$f \in F[x]  \backslash F$, 则$f$有不可约分解
**证明**: 设$n  = \operatorname{deg} f$. 对$n$归纳:
$n = 1$时，$f$是不可约多项式，结论成立
$n > 1$时，假设结论对任何次数大于零且小于$n$的多项式都成立. 
	若$f$是不可约的，结论成立
	若$f$可约，则存在次数为正且小于$n$的多项式使得$f = gh$ （[[Unique Factorization Domain, UFD#^flag1 | 参考此处]]）,  而由归纳假设可知$g,h$都是若干个不可约多项式之积，故$f$也是
### 唯一因子分解整环(UFD)
我们称$D$是*唯一因子分解整环(UFD)*, 如果$D$中的每个非零单位的元素$a$都满足下列两个条件
1. $a$ 可以写成$D$中有限多个不可约元素之积
2. 若$a$有以下两种不可约分解
$$
a = p_1 \cdots p_m = q_1 \cdots q_n
$$
则$m = n$且适当调整下标后，我们有
$$
p_1 \approx q_1, \cdots, p_m \approx q_m
$$
**命题**：设$D$满足上述定义中的条件(i), 则$D$是唯一因子分解整环当且仅当$D$中的不可约元都是素元

在唯一因子分解整环中，素元就是不可约元，不可约元就是素元
反之，如果在一个整环中有不可约元就是素元，那么这个整环就是一个唯一因子分解整环

**命题**：在唯一因子分解整环中，每个非零非可逆元$a$可以被表示为
$$
a = up_1^{m_1} \cdots p_k^{m_k}
$$
其中$u \in U_D, p_1, \cdots, p_k$是两两不相伴的不可约元，称之为$a$的*标准不可约分解*
如果还有
$$
a = vq_1^{n_1} \cdots q_l^{n_l}
$$
则有$k = l$且适当调整下标后有$p_i \approx q_i$和$m_i = n_i$

例：$44 = 2^2 \cdot 11 = -(-2)^2 \cdot (-11)$
### 算术基本定理
设$n \in \mathbb{N} \backslash \{0, 1, -1\}$. 则存在唯一的两两不同的素数$p_1, p_2, \cdots, p_m$和正整数$i_1, i_2, \cdots, i_m$使得
$$
n = \pm p_1^{i_1} \cdots p_m^{i_m}
$$


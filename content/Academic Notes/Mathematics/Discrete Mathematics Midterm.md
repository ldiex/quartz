# 逻辑和推理
## 命题逻辑
### Operators
- $x \to y$, material implication (conditional statement)
	- $(x \to y) = 1 \iff (x = 0) \vee (y = 1)$
- $x \leftrightarrow y$, bi-conditional statement
	- $(x \leftrightarrow y) = 1 \iff (x = y = 0) \vee (x = y = 1)$
## 逻辑等价式
### Distributive laws
$$
\begin{gather}
p \lor (q \land r) \equiv (p \lor q) \land (p \lor r) \\
p \land (q \lor r) \equiv (p \land q) \lor (p \land r)
\end{gather}
$$
### De Morgan's laws
$$
\begin{gather}
\neg (p \land q) \equiv \neg p \lor \neg q \\
\neg (p \lor q) \equiv \neg p \land \neg q
\end{gather}
$$
### Absorption laws
$$
\begin{gather}
p \lor (p \land q) \equiv p \\
p \land (p \lor q) \equiv p
\end{gather}
$$
### Conditional distributive laws
$$
\begin{gather}
(p \lor q) \to r \equiv (p \to r) \land (q \to r) \\
(p \land q) \to r \equiv (p \to r) \lor (q \to r)
\end{gather}
$$
> Like De Morgan's laws, ha?

### Normal forms
#### Disjunction normal Form
$$
F(x_1,x_2, \cdots, x_n) = Q_1 \vee Q_2 \vee \cdots \vee Q_m
$$
#### Conjunction Normal Form
$$
F(x_1,x_2, \cdots, x_n) = Q_1 \land Q_2 \land \cdots \land Q_m
$$
### Minimal Operators to Express Statements
One could use and only use 
1. AND, NOT
2. OR, NOT
3. IMPLICATION
## 谓词和量词
### Unique Quantifier
The uniqueness quantifier is denoted as $!\exists$, the statement $!\exists x\ P(x)$ states "There exists a unique $x$ such that $P(x)$ is true." 
### Quantifiers with Restricted Domains
$$
\forall P(x) \ Q(x) \equiv \forall x \left( P(x) \to Q(x) \right) 
$$
and
$$
\exists P(x) \ Q(x) \equiv \exists x\left( P(x) \land Q(x) \right) 
$$
> [!Tip]
> Note that for existential quantification, here is $P(x) \land Q(x)$ but not $P(x) \to Q(x)$

## 推理规则

| Tautology                                          | Name                   |
| -------------------------------------------------- | ---------------------- |
| $(p \land (p \to q)) \to q$                        | Modus ponens           |
| $(\neg q \land (p \to q) \to \neg p)$              | Modus tollens          |
| $((p \to q) \land (q \to r)) \to(p \to r)$         | Hypothetical syllogism |
| $((p \lor q) \land \neg p) \to q$                  | Disjunctive syllogism  |
| $p \to(p \lor q)$                                  | Addition               |
| $(p \lor q) \to p$                                 | Simplification         |
| $((p) \land (q)) \to(p \land q)$                   | Conjunction            |
| $((p \lor q) \land (\neg p \lor r)) \to(q \lor r)$ | Resolution             |

## 证明方法
### Proof by Contraposition
Proofs by contraposition make use of the fact that the conditional statement $p \to q$ is equivalent to tis contrapositive, $\neg q \to \neg p$. This means that the conditional statement $p \to q$ can be proved by showing that its contrapositive, $\neg q \to \neg p$, is true. In a proof by contraposition of $p \to q$, we take $\neg q$ as a premise, and using axioms, definitions, and previously proven theorems, together with rules of inference, we show that $\neg p$ must follow.

### Proof by Contradiction
Suppose we want to prove that a statement $p$ is true. Furthermore, suppose that we can find a contradiction $q$ such that $\neg p \to q$ is true. Because $q$ is false, but $\neg p \to q$ is true, we can conclude that $\neg p$ is false, which means that $p$ is true.

To find a contradiction $q$, we consider the statement $r \land \neg r$, which is a contradiction whenever $r$ is a proposition. We can prove that $p$ is true if we can show that $\neg p \to (r \land \neg r)$ is true for some proposition $r$. 
# 集合
## 幂集(Power Sets)
Given a [[Set|set]] $S$, the *power set* of $S$ is the set of all subsets of the set $S$. The power set of $S$ is denoted as $\mathcal P(S)$

For example
$$
\begin{gather}
\mathcal P \left( \left\{ 0,1,2 \right\}  \right)  = \left\{ \emptyset,\left\{ 0 \right\} , \left\{ 1 \right\} , \left\{ 2 \right\} , \left\{ 0,1 \right\} ,\left\{ 0,2 \right\} ,\left\{ 1,2 \right\} ,\left\{ 0,1,2 \right\}  \right\}  \\
\mathcal P(\emptyset) = \left\{ \emptyset \right\} \\
\mathcal P(\left\{ \emptyset \right\} ) = \left\{ \emptyset , \left\{ \emptyset \right\}  \right\} 
\end{gather}
$$
If $\left|S\right|=n$, than we have $\left|\mathcal P(S)\right| = 2^n$
## Cartesian积
$$
A \times B = \left\{ (a,b) \mid a\in A \land b\in B \right\} 
$$
$$
A_1 \times A_2 \times \cdots \times A_n = \left\{ (a_1,a_2, \ldots ,a_n) \mid a_i\in A_i \text{ for } i = 1,2, \ldots ,n \right\} 
$$
### Relation
A **subset** $R$ of the Cartesian Product $A \times B$ is called a *relation* from set $A$ to the set $B$. A relation from $A$ to itself is called a relation *on* $A$
## 重集(Multisets)
The multiset denoted by $\left\{ a,a,a,b,b \right\}$ is the multiset that contains the element $a$ thrice and $b$ twice. There is another notation $\left\{ m_1\cdot a_1,m_2\cdot a_2, \ldots ,m_r\cdot a_r \right\}$ denotes the multiset with $a_i$ occurs $m_i$ times.

The numbers $m_i$ are called the *multiplicities* of the elements $a_i$. (Elements not in a multiset are assigned $0$ as their multiplicities in this set)
## 势(基数, Cardinality)
The sets $A$ and $B$ have the same *cardinality* if and only if there is one-to-one **correspondence** from $A$ to $B$. When $A$ and $B$ have the same cardinality, we write $\left|A\right| = \left|B\right|$

If there is a one-to-one **function** from $A$ to $B$, the cardinality of $A$ is less than or the same as the cardinality of $B$ and we write $\left|A\right| \leq \left|B\right|$.

If $A$ and $B$ are sets with $\left|A\right|\leq \left|B\right|$ and $\left|B\right|\leq \left|A\right|$, then $\left|A\right|= \left|B\right|$
### Countable Sets
A set that is either finite or has the same cardinality as the set of positive integers is called *countable*. A set that is not countable is called *uncountable*. When an **infinite** set $S$ is countable, we denote the cardinality of $S$ by $\aleph_0$. We write $\left|S\right|= \aleph_0$ and say that $S$ has cardinality "aleph null"

If $A$ and $B$ are countable sets, then $A \cup B$ is also countable.

### The Continuum Hypothesis
Cantor states that the cardinality of a set is always less than the cardinality of its [[Power Sets|power set]]. Hence, $\left|\mathbb{Z}^+\right| < \left|\mathcal P(\mathbb{Z}^+)\right|$. We can rewrite this as $\aleph_0 < 2^{\aleph_0}$. We denote $2^{\aleph_0} = \aleph_1$

We have $\left|\mathbb{R}\right| = \aleph_1$

The continuum hypothesis is that there is no cardinal number $X$ between these numbers:
$$
\aleph_0 <\aleph_1 < \aleph_2< \cdots
$$
where $\aleph_{n+1} = 2^{\aleph_n}$

# 矩阵
## 01矩阵
A *0-1 Matrix* is a matrix whose elements are either 0 or 1.

Let $A = (a_{ij})_{m \times n}, \ B = (b_{ij})_{m \times n}$ be 0-1 matrices, we define
$$
A \lor B = (a_{ij} \lor b_{ij})_{m \times n} , \quad A \land B = (a_{ij} \land b_{ij})_{m \times n}
$$
and 
$$
A \odot B = (c_{ij})_{m \times n}, \ \text{where}\ c_{ij} = (a_{i1} \land b_{1j}) \lor (a_{i2} \land b_{2j}) \lor \cdots \lor (a_{ik} \land b_{kj})
$$
which is called the *Boolean Product* of $A$ and $B$
> [!Tip]
> We can see Boolean Product as a normal matrix multiplication with $+$ replaced by $\lor$ and $\times$ replaced by $\land$

Based on this, we can also define the $r$-th *Boolean power* of $A$ as
$$
A^{[r]} = \underbrace{A \odot A \odot \cdots \odot A}_{A \text{ occurs } r \text{ times}}
$$
# 算法
## 性质
- 输入
- 输出
- 确定性: Well-defined, without a second interpretation
- 正确性: Generate correct output for every possible input
- 有限性: Finishing in finite steps
- 有效性: Each step finishing in finite time
- 通用性: Can be generalized

> [!Note]
> The following example demonstrate correctness for specific cases but lack generality
> ``` python
> def sort_five_numbers(a, b, c, d, e): 
> 	return sorted([a, b, c, d, e])
> ```
> 
## 时间复杂度
### Ranking
$1 \leq \log n \leq  n \leq n \log n \leq n^{2} \leq 2^n \leq n!$
### 记号
#### Big $\Theta$
For function $f(n), g(n)$, $f(n) = \Theta (g(n))$ if and only if $\exists c_1, c_2, n_0 > 0$ s.t. 
$$
\forall n \ge n_0, 0 \le c_1 \cdot g(n) \le f(n) \le c_2 \cdot g(n)
$$
Big $\Theta$ symbol indicates both the upper and lower bound of a time function

#### Big $O$
We say $f(n) = O(g(n))$ if and only if $\exists c, n_0$ s.t.
$$
\forall n \ge n_0, 0\le f(n) \le c \cdot g(n)
$$
This gives us the upper bound of a time function.

#### Big $\Omega$
We say $f(n) = \Omega(g(n))$ if and only if $\exists c, n_0$, s.t. 
$$
\forall n \ge n_0, 0 < c \cdot g(n) \le f(n)
$$
This gives us the lower bound of a time function.
# 数论
## 模算数
$(\mathbb{Z}_m, +, \cdot)$ is a commutative [[Ring|ring]]:
1. Definition
$$
\begin{aligned}
a \equiv b \pmod{m} \iff a  \operatorname{mod} m = b \operatorname{mod} m
\end{aligned}
$$
2. If $a \equiv b \pmod{m}$ and $c \equiv d \pmod{m}$, then
$$
a + c \equiv b + d \pmod{m}, \quad ac \equiv bd \pmod{m}
$$
3. 
$$
\begin{aligned}
(a + b) \operatorname{mod} m &= (a  \operatorname{mod} m + b \operatorname{mod} m) \operatorname{mod} m\\
ab \operatorname{mod} m &= \left[ (a  \operatorname{mod} m )( b \operatorname{mod} m) \right]  \operatorname{mod} m
\end{aligned}
$$
## $\mathbb{Z}_m$中的乘法逆元
The *modular inverse* of $a$ in the [[Ring|ring]] of integers modulo $m$ is an integer $x$ such that
$$
ax \equiv 1 \pmod{m}
$$
## Euler定理
 i if $n$ is a positive integer, and let $a$ be an integer that is relatively prime to $n$. Then
$$
a^{\phi(n)} \equiv 1 \pmod{n}
$$
where $\phi(n)$ is [[Euler's Totient Function|Euler's totient function]], which counts the number of positive integers less than $n$ that is also relative prime to $n$
## Fermat小定理(Euler定理的一个特例)
If $p$ is a prime, then $\phi(p) = p$, then Euler's Theorem becomes Fermat's Little Theorem
$$
a^{p-1} \equiv 1 \pmod{p}
$$
### 伪素数
Let $b$ be a positive integer. If $n$ is a composite positive integer, and $b^{n-1} \equiv 1 \pmod{n}$, then $n$ is called a *pseudo-prime* to be base $b$

Among the positive integer not exceeding $x$, where $x$ is a positive real number, compared to primes there are relatively few pseudo-primes to the base $b$. So determining  whether $b^{n-1} \equiv 1 \pmod{n}$ is a useful test that provides some evidence concerning whether $n$ is prime.

However, there are some composite $n$ that satisfies the congruence $b^{n-1} \equiv 1 \pmod{n}$ for all positive integers $b$ with $\mathrm{gcd}(b,n) = 1$ is called a *Carmichael number*. For example, the integer $561$ is a Carmichael number.

## Exgcd
For example, calculate $\mathrm{exgcd}(108, 68)$

| $a\ (r_i)$ | $b$ | $x_i = x_{i -2} - x_{i-1}q_{i-1}$ | $y_i = y_{i-2} - y_{i-1}q_{i-1}$ |     |
| ---------- | --- | --------------------------------- | -------------------------------- | --- |
| 0          | 108 | 1                                 | 0                                |     |
| 108        | 68  | 0                                 | 1                                |     |
| 68         | 40  | 1                                 | -1                               |     |
| 40         | 28  | -1                                | 2                                |     |
| 28         | 12  | 2                                 | -3                               |     |
| 12         | 4   | -5                                | 8                                |     |
| 4          | 0   |                                   |                                  |     |
this gives
$$
- 5 \times 108 + 8 \times 68 = \mathrm{gcd}(108, 8) = 4
$$
## 中国剩余定理
Let $n_1, \ldots ,n_k$ be integers greater than $1$, and $N = \prod_{i=1}^k n_i$. If the $n_i$ are pair-wise co-prime, and if $a_1, \ldots ,a_k$  are any integers, then the system
$$
\begin{aligned}
x &\equiv a_1 \pmod{n_1} \\
&\ \ \vdots  \\
x & \equiv a_k \pmod{n_k}
\end{aligned}
$$
has a solution, and any two solutions, say $x_1$ and $x_2$, satisfy $x_1 \equiv x_2 \pmod{N}$

To construct a solution, let $N_i = N/n_i$ be the product of all moduli but one. As the $n_i$ are pair-wise co-prime, $N_i$ and $n_i$ are co-prime. Thus Bezout's identity applies, and there exist integers $M_i$ and $m_i$ such that
$$
M_i N_i + m_i n_i = 1
$$
A solution of the system of congruences is
$$
x = \sum_{i = 1}^k a_i M_i N_i
$$
In fact, as $N_j$ is a multiple of $n_i$ for $i \neq j$, we have
$$
x \equiv a_i M_iN_i \equiv a_i(1-m_in_i) \equiv a_i \pmod{n_i}
$$
## 原根和离散对数
A *primitive root* module a prime $p$ is an integer $r$ in $\mathbb{Z}_p$ such that every non-zero element of $\mathbb{Z}_p$ is a power of $r$.

We can say here $r$ can **generate** the space of $\mathbb{Z}_p$

An important fact is that there is a primitive root module $p$ for every prime $p$. Suppose this primitive root is $r$, and $a$ is an integer between $1$ and $p-1$ inclusive. If $r^e \operatorname{mod} p = a$ and $0 \leq e \leq p-1$, we say that $e$ is the *discrete logarithm* of $a$ module $p$ to the base $r$ and we write $\log_ra =e$

# 例题
## T1
> Prove that $(0, 1)$ and $[0, 1]$ have the same cardinality

Using Hilbert's Hotel. Let $H = \left\{ \dfrac{1}{n}: n\in \mathbb{N} \right\}$, then define $f:(0, 1) \to[0,1]$ so that
$$
\begin{aligned}
\dfrac{1}{2} \to0, \ \dfrac{1}{3} \to1, \ \dfrac{1}{n} \to \dfrac{1}{n-2}
\end{aligned}
$$
and
$$
x \to x ,\quad x \notin H
$$
> [!Tip]
> We can also construct a bijection from $(0,1)$ to $[0, 1)$ by letting $\dfrac{1}{2} \to0$ and $\dfrac{1}{n}\to \dfrac{1}{n-1}$

## T2
> Let $S \subset \left\{ 1,2,3, \ldots ,98,99,100 \right\}$ where $\left|S\right| = 62$. Prove that there exist $x, y\in S$ such that $x - y = 23$

Let's divide $\left\{ 1,2, \ldots ,100 \right\}$ into threes sections
$$
\left\{ 1,2, \ldots ,100 \right\}  = \underbrace{\left\{ 1,2, \ldots ,46 \right\} }_{A} \cup \underbrace{\left\{ 47,48, \ldots ,69 \right\} }_{B} \cup \underbrace{\left\{ 93,94, \ldots ,100 \right\} }_{C}
$$
First we prove that we can select $23$ elements at most from $A$ such that there are no $x, y$ in this selection satisfying $x - y = 23$. To conclude this, we further divide $A$ into pairs
$$
A = \left\{ 1,24 \right\} \cup \left\{ 2,25 \right\} \cup \cdots \cup \left\{ 23, 46 \right\} 
$$
We can select no more than $1$ element in each pair, so we can select no more than $23$ elements in $A$.

Similarly, we can select no more than $23$ elements in $B$. Therefore, we can select no more than $23 + 23 + 8 = 54$ elements in $\left\{ 1,2, \ldots ,100 \right\}$

## T3

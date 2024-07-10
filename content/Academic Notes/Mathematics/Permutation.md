# Definition
A *permutation* can be defined as a [[Injective, Surjective and Bijective#Bijective (One-to-One Correspondence)|bijection]] from a set $S$ to itself
$$
\sigma: S \to S
$$
The *identity permutation* is defined by $\sigma(x) = x$ for all elements $x \in S$, and can be denoted by the number $1$, by $\mathrm{id} = \mathrm{id}_S$, or by a single 1-cycle $(x)$

# Symmetric Group
The set of all permutations of a set with $n$ elements forms the [[Symmetric Group|symmetric group]] $S_n$, where the [[Group|group]] multiplication is composition of functions. Thus for two permutations m $\sigma$ and $\tau$ in the group $S_n$, their product $\pi = \sigma \tau$ is defined by
$$
\pi(i) = \sigma(\tau(i))
$$
Composition is usually written without a dot or other sign. In general, composition of two permutations is not commutative: $\tau \sigma \neq \sigma \tau$

The *group identity* of the symmetric group $S_n$ is the identity permutation $\mathrm{id}_S$, and the *inverse* of a group element $\sigma$ is denoted as $\pi^{-1}$ such that $\pi \pi^{-1}= \pi^{-1}\pi = \mathrm{id}_S$. 

**Every permutation has an inverse** since if $\sigma\in S_n$ satisfies $\sigma(i) = x_i$ for all $i$ in $1,2, \ldots ,n$ we can simply obtain $\sigma^{-1}$ such that $\sigma^{-1}(x_i)=i$ for all $i$
# Representation
*Cauchy's two-line notation* lists the elements of $S$ in the first row, and the image of each element below it in the second row. For example, the permutation of $S = {1, 2, 3, 4, 5, 6}$ given by the function
$$
\sigma (1)=2,\ \ \sigma (2)=6,\ \ \sigma (3)=5,\ \ \sigma (4)=4,\ \ \sigma (5)=3,\ \ \sigma (6)=1
$$
can be written as
$$
\sigma = \begin{pmatrix}
1 & 2 & 3 & 4 & 5 & 6 \\
2 & 6 & 5 & 4 & 3 & 1
\end{pmatrix}
$$
# Powers of a permutation
Let $\pi$ be a permutation. The positive *powers* of $\pi$ are defined as:
$$
\pi^1 = \pi \text{ and } \pi^{k+1} =\pi\cdot \pi^k \text{ for every integer }  k \geq 1
$$
The negative powers of $\pi$ are defined as the positive powers of its inverse: $\pi^{-k} = (\pi^{-1})^k$ for every positive integer $k$. 

Finally, we set $\pi^0 = \mathrm{id}$
# Order of a Permutation
Lert $\pi$ be a permutation. Then there is a positive integer $m$ such that $\pi^m=\mathrm{id}$. Because if we list the powers of $\pi$ : $\pi,\pi^{2},\pi^3, \ldots$ ,  and there is finite items in $S_n$, so there must exist $0 < r < s$ such that $\pi^r = \pi^s$. Therefore we get $\pi^{s-r} = \pi^s(\pi^r)^{-1} = \mathrm{id}$.

We call the smallest positive integer $m$ such that $\pi^m = \mathrm{id}$ the *order* of a permutation $\pi$, denoted as $\mathrm{ord}(\pi)$

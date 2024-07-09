A *permutation* can be defined as a [[Injective, Surjective and Bijective#Bijective (One-to-One Correspondence)|bijection]] from a set $S$ to itself
$$
\sigma: S \to S
$$
The *identity permutation* is defined by $\sigma(x) = x$ for all elements $x \in S$, and can be denoted by the number $1$, by $\mathrm{id} = \mathrm{id}_S$, or by a single 1-cycle $(x)$

The set of all permutations of a set with $n$ elements forms the [[Symmetric Group|symmetric group]] $S_n$, where the [[Group|group]] multiplication is composition of functions. Thus for two permutations m $\sigma$ and $\tau$ in the group $S_n$, their product $\pi = \sigma \tau$ is defined by
$$
\pi(i) = \sigma(\tau(i))
$$
Composition is usually written without a dot or other sign. In general, composition of two permutations is not commutative: $\tau \sigma \neq \sigma \tau$

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

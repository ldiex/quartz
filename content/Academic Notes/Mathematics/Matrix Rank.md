# Definition:
The *rank* of a matrix $A$, denoted by $\mathrm{rank}(A)$ or $ρ(A)$, **is the maximum number of linearly independent rows or columns in the matrix.**
## Intuitive Explanation
Think of the rank of a matrix as the number of "independent directions" or "degrees of freedom" in the matrix. In other words, it's the maximum number of rows or columns that are not a linear combination of the others.

## Mathematical Definition
Let $A$ be an $m × n$ matrix. The rank of $A$ is the maximum number of linearly independent rows or columns in $A$, denoted by:
$$\mathrm{rank}(A) = \max\{k: \text{there exists } k \text{ linearly independent rows or columns in A}\}$$
## Operator Rank
Let $\mathcal A \in \mathcal{L}(V)$ be a [[Linear Operator|linear operator]]. The rank of  $\mathcal A$ is the dimension of $\mathrm{{im}(\mathcal A)}$, and, by [[Linear Map#线性映射基本定理|Rank-Nullity Theorem]], this also equals to $\mathrm{rank}(A)$, where $A$ is the matrix representation of $\mathcal A$ under any bases.

# Properties
1. **Row Rank = Column Rank**: The number of linearly independent rows is equal to the number of linearly independent columns.
2. The rank of $A$ is equal to the rank of its transpose,$A^T$.
3. The rank of $A$ is less than or equal to the minimum of the number of rows ($m$) and the number of columns ($n$), i.e., $\mathrm{rank}(A) ≤ \min(m, n).$
4. $\dim(\ker \phi) + \dim(\mathrm{im} \phi) = \dim V$, from the [[Linear Map#线性映射基本定理|Rank-Nullity Theorem]]


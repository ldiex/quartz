The *adjugate matrix*, also known as the classical adjugate or adjunct matrix, is a matrix that plays a crucial role in various areas of mathematics, physics, and engineering. 
# Definition
Given a square matrix $A$ of order $n \times n$, the adjugate matrix of $A$, denoted by $\mathrm{adj}(A)$,  $\mathrm{Adj}(A)$, $A^*$ or $A^\vee$ is an $n \times n$ matrix whose elements are the *cofactors* of the elements of $A$.

**Cofactors:**
The cofactor of an element $a_{ij}$ of a matrix $A$ is defined as:
$$
C_{ij} = (-1)^{(i+j)} × M_{ij}
$$
where $M_{ij}$ is the [[Matrix Minor|minor]] of $a_{ij}$, which is the determinant of the $(n-1) × (n-1)$ submatrix obtained by removing the $i$-th row and $j$-th column of $A$.

And we define $\mathrm{adj}(A)$ as the transpose of $C$, that is, $\mathrm{adj}(A) = C^T$ 

# Properties
1. **Inverse**: The adjugate matrix is related to the inverse of $A$ by the formula: $A^{-1} = \dfrac{1}{\det(A)} × \mathrm{adj}(A)$

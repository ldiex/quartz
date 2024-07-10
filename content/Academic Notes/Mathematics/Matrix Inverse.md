# Definition
For a square matrix $A$, its *inverse* (denoted as $A^{-1}$) is a matrix that satisfies:
$$AA^{-1} = A^{-1}A = I$$
where $I$ is the identity matrix. 
# Properties
1. Only square matrices can have inverses.
2. Not all square matrices have inverses. Those that do are called *invertible* or *non-singular*.
3. If $A^{-1}$ exists, it is unique.
4. $A$ is invertible if and only if the [[Determinant|determinant]] $\det{A} \neq0$
5. $A$ is invertible if and only if $A$ have no zero [[Eigenvectors and Characteristic Polynomial#特征值|eigenvalue]]
# Calculation
## Adjugate Matrix
See [[Adjugate Matrix]]
## Polynomials
If $A$ is an invertible matrix, its inverse can sometimes be expressed as a polynomial of $A$. One common method involves the [[Cayley-Hamilton Theorem|Cayley-Hamilton theorem]], which states that every square matrix satisfies its own characteristic equation.

Given the [[Characteristic Polynomial|characteristic polynomial]] of $A$:
$$p(\lambda) = \det(\lambda I - A) = \lambda^n + c_{n-1}\lambda^{n-1} + \cdots + c_1\lambda + c_0$$
By the Cayley-Hamilton theorem, we have:
$$p(A) = A^n + c_{n-1}A^{n-1} + \cdots + c_1A + c_0I = 0$$
If $c_0 \neq 0$, we can rearrange this equation to solve for $A^{-1}$:
$$A^n + c_{n-1}A^{n-1} + \cdots + c_1A + c_0I = 0$$
$$A(A^{n-1} + c_{n-1}A^{n-2} + \cdots + c_1I) = -c_0I$$
Multiplying both sides by $-\frac{1}{c_0}$, we get:
$$A^{-1} = -\frac{1}{c_0} (A^{n-1} + c_{n-1}A^{n-2} + \cdots + c_1I)$$
Thus, $A^{-1}$ can be expressed as a polynomial of $A$.
# Other Computational Methods
For larger matrices, numerical methods such as:
- Gaussian elimination
- LU decomposition
are commonly used to compute the inverse.



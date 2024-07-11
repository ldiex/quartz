# Definition
if $A \in \mathrm{M}_n(F)$, then the *trace* of matrix $A$ is defined as
$$
\mathrm{tr} A = \sum_i^n A_{ii}
$$
# Properties
## Sum of eigenvalues
The trace of a matrix is always the sum of its [[Eigenvectors and Characteristic Polynomial#特征值|eigenvalues]] (including repeated ones). This relationship holds because the trace is invariant under [[Linear Operator#矩阵相似|similarity transformations]] and the [[Characteristic Polynomial|characteristic polynomial]] of the matrix (which has roots equal to the eigenvalues) has coefficients that relate to the trace and [[Matrix Determinant|determinant]] of the matrix.   
## Cyclic property
The trace of a matrix is an invariant under the commutation of matrix multiplication
$$
\mathrm{tr}(AB) = \mathrm{tr}(BA)
$$
Similarly,
$$
\mathrm{tr}(ABC) = \mathrm{tr}(BCA) = \mathrm{tr}(CAB)
$$
## Trace of a product
If $A,B \in F^{m\times n}$, then:
$$
\mathrm{tr}(A^TB) = \mathrm{tr}(AB^{T}) =\mathrm{tr}(B^TA) = \mathrm{tr}(BA^T) = \sum_{i = 1}^n \sum_{j = 1}^n a_{ij}b_{ij}
$$
In particular, if $A,B \in \mathrm{M}_n(F)$, we have
$$
\mathrm{tr}(AB) = \sum_{i = 1}^n\sum_{j = 1}^n a_{ij}b_{ji} =  \sum_{i = 1}^n\sum_{j = 1}^n a_{ji}b_{ij} 
$$





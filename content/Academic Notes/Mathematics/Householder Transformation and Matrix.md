A *Householder transformation* (also known as a *Householder reflection* or *elementary reflector*) is a [[Linear Map|linear transformation]] that describes a reflection about a plane or hyperplane containing the origin.

# Definition
The reflection hyperplane can be defined by its normal vector, a unit vector  $\boldsymbol v$ that is [[Euclidean Space#正交投影和正交补|orthogonal]] to the hyperplane. The reflection of a point $\boldsymbol x$ about this hyperplane is the linear transformation:
$$
Q_{\boldsymbol v}(\boldsymbol x) = \boldsymbol x - 2 (\boldsymbol x \vert \boldsymbol v) \boldsymbol v 
$$
or written as the [[Matrix Representation of Linear Map|matrix form]]
$$
H = E - 2\boldsymbol v\boldsymbol v^t
$$
![[Householder Transformation.png]]

# Properties
It is easy to verify that $H$ is
- [[Euclidean Space#正交矩阵与正交等价|orthogonal]] ($H^tH = E$)
- [[Normal Operator and Normal Matrix#正规算子|symmetric]] ($H^t = P$)
- involutory ($P^{2}= E$)
where the last property follows from the first two.

$H$ has an [[Eigenvectors and Characteristic Polynomial#特征值|eigenvalue]] $-1$ with the eigenvector $\boldsymbol v$, since $H\boldsymbol v = - \boldsymbol v$. And $H$ has $n - 1$ eigenvalues $1$ with eigenvectors any set of $n - 1$ linearly independent vectors orthogonal to $\boldsymbol v$

$H$ has [[Matrix Trace|trace]] $n - 2$ and [[Matrix Determinant|determinant]] $-1$, as can be derived directly or deduced from the facts that the trace is the sum of the eigenvalues and the determinant is the product of the eigenvalues.

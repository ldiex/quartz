In linear algebra, a *diagonal matrix* is a matrix in which **the entries outside the main diagonal are all zero**

A diagonal matrix can be constructed from a vector $\boldsymbol a = (a_1, \ldots, a_n)^t$:
$$
\begin{pmatrix}
a_1 & 0 & \cdots & 0 \\
0 & a_2 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & a_n
\end{pmatrix} = \mathrm{diag}(a_1,a_2,\ldots,a_n)
$$
## Matrix Multiplication
$$
\operatorname {diag} (a_{1},\,\ldots ,\,a_{n})\operatorname {diag} (b_{1},\,\ldots ,\,b_{n})=\operatorname {diag} (a_{1}b_{1},\,\ldots ,\,a_{n}b_{n})
$$
which implies,
$$
\mathrm{diag}(a_1,a_2,\ldots,a_n) = 
\mathrm{diag}(a_1^k,a_2^k,\ldots,a_n^k)
$$

# [[Determinant]]
$$
\mathrm{diag}(a_1,a_2,\ldots,a_n) = a_1a_2\cdots a_n
$$

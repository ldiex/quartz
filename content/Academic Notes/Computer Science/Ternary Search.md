A *ternary search algorithm* is for finding the minimum or maximum of a [[Unimodality|unimodal]] function.

Let $f(x)$ be a unimodal function on some interval $[l,r]$. Take any two points $m_1$ and $m_2$ in this segment $l < m_1 < m_2 < r$. Then,
- if $f(m_1) < f(m_2)$, then the required maximum can not be located on the left side, and we need to look only in the interval $[m_1,r]$
- if $f(m_1) > f(m_2)$, similarly we need to pay attention to the segment $[l,m_2]$
- if $f(m_1) = f(m_2)$, then the search should be conducted in $[m_1,m_2]$

If we chose points $m_1, m_2$ as
$$
m_1 = l+ \dfrac{r-l}{3},\quad m_2 = r- \dfrac{r-l}{3}
$$
then the [[Time Complexity|time complexity]] of this algorithm is $O(\log n)$ 

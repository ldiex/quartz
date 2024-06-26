# Long multiplication
The most straight-forward way to do multiplication is by *long multiplication* as we learned in elementary school

Example
```
      23958233
×         5830
———————————————
      00000000 ( =  23,958,233 ×     0)
     71874699  ( =  23,958,233 ×    30)
   191665864   ( =  23,958,233 ×   800)
+ 119791165    ( =  23,958,233 × 5,000)
———————————————
  139676498390 ( = 139,676,498,390)
```

It's easy to conclude that multiplying two $n$-digit numbers using long multiplication requires $\Theta(n^{2})$ single-digit operations (additions and multiplications)

# Karatsuba multiplication
*Karatsuba multiplication* is an efficient algorithm for multiplying large numbers. The algorithm reduces the multiplication of two $n$-digit numbers to at most $n^{\log_2 3}$ single-digit multiplications in general
## Procedure
Given two numbers $x$ and $y$ represented as:
$$
 x = x_1 \cdot 10^{m} + x_0 ,\quad y = y_1 \cdot 10^{m} + y_0 
$$
where $x_0$ and $y_0$ are the lower halves, and $x_1$ and $y_1$ are the upper halves of the numbers, each of length $m$. 

The product $x \cdot y$ can be computed as follows:
1. **Compute three products:** 
$$
\begin{aligned}
    z_0 &= x_0 \cdot y_0\\
    z_2 &= x_1 \cdot y_1  \\
  z_1 &= (x_0 + x_1) \cdot (y_0 + y_1) - z_0 - z_2  
\end{aligned}
$$
2. **Combine the results:**
$$
    x \cdot y = z_2 \cdot 10^{2m} + z_1 \cdot 10^{m} + z_0  
$$
## Example
If we need to multiply 1234 and 5678 using Karatsuba multiplication.
1. Split the numbers:
$$
    x = 1234 \rightarrow x_1 = 12, x_0 = 34   
$$
$$
    y = 5678 \rightarrow y_1 = 56, y_0 = 78 
$$
2. Compute the three products:
$$
    z_0 = 34 \cdot 78 = 2652  
$$
$$
    z_2 = 12 \cdot 56 = 672   
$$
$$
    z_1 = (12 + 34) \cdot (56 + 78) - 2652 - 672 = 46 \cdot 134 - 2652 - 672 = 6164 - 2652 - 672 = 2840  
$$
3. Combine the results:  
$$
    x \cdot y = 672 \cdot 10^4 + 2840 \cdot 10^2 + 2652 = 6720000 + 284000 + 2652 = 7006652 
$$
Thus, $1234 \cdot 5678 = 7006652$.

# Schönhage–Strassen algorithm
TODO
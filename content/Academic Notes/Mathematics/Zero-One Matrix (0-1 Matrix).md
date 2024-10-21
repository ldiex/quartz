A *0-1 Matrix* is a matrix whose elements are either 0 or 1.

Let $A = (a_{ij})_{m \times n}, \ B = (b_{ij})_{m \times n}$ be 0-1 matrices, we define
$$
A \lor B = (a_{ij} \lor b_{ij})_{m \times n} , \quad A \land B = (a_{ij} \land b_{ij})_{m \times n}
$$
and 
$$
A \odot B = (c_{ij})_{m \times n}, \ \text{where}\ c_{ij} = (a_{i1} \land b_{1j}) \lor (a_{i2} \land b_{2j}) \lor \cdots \lor (a_{ik} \land b_{kj})
$$
which is called the *Boolean Product* of $A$ and $B$

> [!Tip]
> We can see Boolean Product as a normal matrix multiplication with $+$ replaced by $\lor$ and $\times$ replaced by $\land$

Based on this, we can also define the $r$-th *Boolean power* of $A$ as
$$
A^{[r]} = \underbrace{A \odot A \odot \cdots \odot A}_{A \text{ occurs } r \text{ times}}
$$


# Mathematical Induction
$$
\left( P(1) \land \forall \left( P(k) \to P(k + 1) \right)  \right) \to \forall n \ P(n)
$$
# Strong Induction
$$
\left( P(1) \land \forall \left( P(1) \land P(2) \land  \cdots \land P(k) \to P(k + 1) \right)  \right) \to \forall n \ P(n)
$$
# The Well-Ordering Property
> Every non-empty set of non-negative integers has a least element

This principle underpin the principle of mathematical induction

# Structural Induction
- **Base Case**: Prove that the property holds for all base case elements of the recursive definition
- **Induction Step**: Prove that if the property holds for the immediate substructures of a certain structure S, then it must also hold for S itself 

# Extended Induction
Extend mathematical induction from $\mathbb{N}$ to any [[Partially Ordered Set]] with the well-ordering property.


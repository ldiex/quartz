# Boolean Logic
## Value
`True (T)`, `False (F)`

## Operators
$\neg x (\text{or }\bar x)$ , negation, not
$x \land y$, conjunction, and
$x \vee y$, disjunction, or
$x \oplus y$, exclusive or, xor
$x \to y$, material implication
- $(x \to y) = 1 \iff (x = 0) \vee (y = 1)$
## Laws
$(x \land y) \land z = x \land (y \land z)$
$(x \vee y) \vee z = x\vee (y \vee z)$
$(x \land y) \vee z  = (x \vee z) \land (y \vee z)$
$(x \vee y) \land z = (x \land z) \vee (y \land z)$
### De Morgan's Law
$\neg (x \vee y) = \neg x \land \neg y$
$\neg(x \land y) = \neg x \vee \neg y$

$x \oplus y = (\neg x \land y) \vee (x \land \neg y)$
$x \oplus y = (x \vee y) \land (\neg x \vee \neg y)$

# Normal forms
**Any complex proposition can be represented by propositions that only include AND, OR as well as NOTs.**
Given a [[Boolean Function]] $f:\{0,1\}^n \to \{0, 1\};\; (x_1, \cdots, x_n) \to y$
For each line in its truth table
$$
y = f(x_1, \cdots, x_n), \quad \text{where } y = \beta_i;x_{k} = \alpha_{ik}, k \in [n]
$$
Then we have
$$
f = \bigvee_{i:\beta_i = 1} \left(\bigwedge_{k} g(x_k)\right), \text{where } g(x_k) = \begin{cases}x_k, &\alpha_{ik} = 1 \\ \overline{x_k}, & \alpha_{ik} = 0\end{cases}
$$
## Disjunction Normal Form, DNF
Every $n$-variable proposition $F(x_1,x_2, \cdots, x_n)$ can be represented by a *disjunction normal form*
$$
F(x_1,x_2, \cdots, x_n) = Q_1 \vee Q_2 \vee \cdots \vee Q_m
$$
## Conjunction Normal Form, CNF
Similarly, we have
$$
f = \bigwedge_{i:\beta_i = 0} \left(\bigvee_{k} g(x_k)\right), \text{where } g(x_k) = \begin{cases}x_k, &\alpha_{ik} = 0 \\ \overline{x_k}, & \alpha_{ik} = 1\end{cases}
$$

e.g.
$$
(x \oplus y) \to z = (x \vee \bar y \vee z)\wedge(\bar x \vee y \vee z)
$$
This is a natural result of [[Logic Equivalences#De Morgan's laws|De Morgan's Law]]

# Representation with Least Operators
One could use and only use 
1. AND, NOT
2. OR, NOT
3. IMPLICATION
to represent all Boolean expressions.




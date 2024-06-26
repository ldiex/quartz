# Boolean Function
A *Boolean function* is a function $f$ such that: $f:\{0,1\}^n \to \{0, 1\}$

Given two Boolean functions $f_1, f_2$, we say $f_1 = f_2 \iff$ $f_1, f_2$ have the same *truth table*

A $n$-variable Boolean function  has $2^{2^n}$ different types

A $n$-input, $m$-output Boolean function has $(2^m)^{2^n}$ different types
- A Boolean function with n inputs can be represented as a truth table with $2^n$ rows, where each row corresponds to a possible combination of input values. For each row, there are $2^m$ possible output combinations of m bits.

# Monotonic Boolean Function
A *monotonic Boolean function* (*MBF*) is a Boolean function that satisfies the monotonicity condition
$$
f(x_1, \ldots ,x_n) \leq f(y_1, \ldots ,y_n) \iff x_i<y_i,\quad \forall i\in[n] 
$$
In other words, for every combination of inputs, switching one of the inputs from false to true can only cause the output to switch from false to true and not from true to false.

Some examples of MBFs include: The constants $0$ and $1$, The identity function $f(x)=x$, The disjunction $x_1 \vee x_2$, and The conjunction $x_1 \wedge x_2$

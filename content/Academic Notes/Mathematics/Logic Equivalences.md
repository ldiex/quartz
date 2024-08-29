# Definition
Compound propositions that have the same truth values in all possible cases are called *logically equivalent*.

The compound propositions $p$ and $q$ are called *logically equivalent* if $p \leftrightarrow q$ is a *tautology* (i.e. always be true under any circumstances). The notation $p \iff q$ (also $p \equiv q$) denotes that $p$ and $q$ are logically equivalent
# Logic Equivalences
## Distributive laws
$$
\begin{gather}
p \lor (q \land r) \equiv (p \lor q) \land (p \lor r) \\
p \land (q \lor r) \equiv (p \land q) \lor (p \land r)
\end{gather}
$$
## De Morgan's laws
$$
\begin{gather}
\neg (p \land q) \equiv \neg p \lor \neg q \\
\neg (p \lor q) \equiv \neg p \land \neg q
\end{gather}
$$
## Absorption laws
$$
\begin{gather}
p \lor (p \land q) \equiv p \\
p \land (p \lor q) \equiv p
\end{gather}
$$
## Conditional distributive laws
$$
\begin{gather}
(p \lor q) \to r \equiv (p \to r) \land (q \to r) \\
(p \land q) \to r \equiv (p \to r) \lor (q \to r)
\end{gather}
$$
# Normal Forms 
See [[Boolean Logic#Normal forms|Normal Forms]]
The linked page above introduces how to construct basic logic expressions via listing out their truth tables. However, sometimes we could just easily do this work by applying known logic equivalences

For example, $\neg(p \to q) \equiv \neg(\neg p \lor q) \equiv \neg(\neg p) \land \neg q \equiv p \land \neg q$

# Satisfiability
A compound propositions is *satisfiable* if there is an assignment of truth values to its variables that makes it true (that is, when it is a tautology or contingency). When no such assignments exist, that is, when the compound proposition is false for all assignments of truth values to its variables, the compound proposition is *unsatisfiable*

When we find a particular assignment of truth values that makes a compound proposition true, such an assignment is called a *solution* of this particular satisfiability problem




# Direct Proofs
Use [[Rules of Inference]]

# Proof by Contraposition
Proofs by contraposition make use of the fact that the conditional statement $p \to q$ is equivalent to tis contrapositive, $\neg q \to \neg p$. This means that the conditional statement $p \to q$ can be proved by showing that its contrapositive, $\neg q \to \neg p$, is true. In a proof by contraposition of $p \to q$, we take $\neg q$ as a premise, and using axioms, definitions, and previously proven theorems, together with rules of inference, we show that $\neg p$ must follow.

# Proof by Contradiction
Suppose we want to prove that a statement $p$ is true. Furthermore, suppose that we can find a contradiction $q$ such that $\neg p \to q$ is true. Because $q$ is false, but $\neg p \to q$ is true, we can conclude that $\neg p$ is false, which means that $p$ is true.

To find a contradiction $q$, we consider the statement $r \land \neg r$, which is a contradiction whenever $r$ is a proposition. We can prove that $p$ is true if we can show that $\neg p \to (r \land \neg r)$ is true for some proposition $r$. 
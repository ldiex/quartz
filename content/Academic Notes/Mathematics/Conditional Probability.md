*Conditional Probability* is the concept that addresses a fundamental question: how should we update our beliefs in light of the evidence we observe

In real world, a useful perspective is that *all probabilities are conditional* since whether or not it's written explicitly, there is always background knowledge built into every probability

If $A$ and $B$ are events with $P(B)>0$, then the *conditional probability* of $A$ given $B$, denoted by $P(A \vert B)$, is defined as 
$$
P(A \vert B) = \dfrac{P(A \cap B)}{P(B)}
$$
Here $A$ is the event whose uncertainty we want to update, and $B$ is the evidence we observe (or want to treat as given). We call $P(A)$ the *prior* probability of $A$ and $P(A \vert B)$ the *posterior* probability of $A$ ("prior" means before updating based on the evidence, and "posterior" means after updating based on the evidence)

It's natural to conclude that for any event $A$, $P(A \vert A) = P(A \cap A) / P(A) = 1$ since upon observing that $A$ has occurred, out updated probability for $A$ is $1$


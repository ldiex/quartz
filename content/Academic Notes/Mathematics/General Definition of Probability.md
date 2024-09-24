A *probability space* consists of a sample space $S$ and a *probability function* $P$ which takes an event $A \subset S$ as inputs and returns $P(A)$, a real number between $0$ and $1$, as output. The function $P$ must satisfy the following axioms:
1. $P(\emptyset) = 0, P(S) = 1$
2. If $A_1,A_2, \cdots$ are disjoint events, then
$$
P\left( \bigcup_{j = 1}^{\infty} A_j \right) = \sum_{j = 1}^\infty P(A_j)
$$
(Saying that these events are *disjoint* means that they are *mutually exclusive*: $A_i \cap A_j = \emptyset$ for $i \neq j$)

Any function $P$ (mapping events to numbers in the interval $[0,1]$) that satisfies the two axioms is considered a valid probability function. However, the axioms don't tell us how probability should be interpreted; different schools of thought exists

The *frequentist* view of probability is that it represents a long-run frequency over a large number of repetitions of an experiment. The *Bayesian* view of probability is that it represents a degree of belief about the event in question, so we can assign probabilities to hypotheses like "candidate A will win the election" even if it isn't possible to repeat the same election over and over again

We can prove probability has the following properties, for any events $A$ and $B$ : 
1. $P(\bar{A}) = 1 - P(A)$
2. If $A \subset B$, then $P(A) \leq P(B)$
3. $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
The third property is a special case of *inclusion-exclusion*
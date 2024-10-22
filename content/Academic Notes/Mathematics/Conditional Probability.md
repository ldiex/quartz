# Introduction
*Conditional Probability* is the concept that addresses a fundamental question: how should we update our beliefs in light of the evidence we observe

In real world, a useful perspective is that *all probabilities are conditional* since whether or not it's written explicitly, there is always background knowledge built into every probability

# Definition
If $A$ and $B$ are events with $P(B)>0$, then the *conditional probability* of $A$ given $B$, denoted by $P(A \vert B)$, is defined as 
$$
P(A \vert B) = \dfrac{P(A \cap B)}{P(B)}
$$
Here $A$ is the event whose uncertainty we want to update, and $B$ is the evidence we observe (or want to treat as given). We call $P(A)$ the *prior* probability of $A$ and $P(A \vert B)$ the *posterior* probability of $A$ ("prior" means before updating based on the evidence, and "posterior" means after updating based on the evidence)

It's natural to conclude that for any event $A$, $P(A \vert A) = P(A \cap A) / P(A) = 1$ since upon observing that $A$ has occurred, out updated probability for $A$ is $1$

# Bayes' rule and the law of total probability
## Probability of the intersection of two events
$$
P (A \cap B) = P(B)P(A \vert B)=P(A)P(B \vert A)
$$
At first sight this theorem may not seem very useful: it *is* the definition of conditional probability, just written slightly differently. But the theorem is actually very useful, since it often turns out to be possible to **find conditional probabilities without going back to the definition**
## Probability of the intersection of $n$ events
For any events $A_1, \ldots ,A_n$ with $P(A_1A_2 \cdots A_{n-1}) > 0$
$$
P(A_1A_2 \cdots A_n) = P(A_1)P(A_2 \vert A_1)P(A_3 \vert A_1 A_2) \cdots P(A_n \vert A_1 \cdots A_{n-1})
$$
In fact, this is $n!$ theorems in one, since we can [[Permutation|permute]] $A_1, \ldots ,A_n$ however we want without affecting the left-hand side.

## Bayes' rule
$$
P(A \vert B) = \dfrac{P(B \vert A)P(A)}{P(B)}
$$
See also [[Bayes' Theorem]]

## Law of total probability
Let $A_1, \ldots ,A_n$ be a partition of the sample space $S$ (i.e., the $A_i$ are **disjoint** events and their union is $S$), with $P(A_i)>0$ for all $i$. Then
$$
P(B) = \sum_{i = 1}^n P(B \vert A_i)P(A_i)
$$
# Conditional probabilities are probabilities
For conditional probabilities, the [[General Definition of Probability|laws of probability]] operate as well, in particular when we condition on an event $E$:
- Conditional probabilities are in $[0,1]$
- $P(S \vert E) = 1, \ P(\emptyset \vert E) = 0$
- If $A_1, A_2, \ldots$ are disjoint, then $P(\cup_{j = 1}^\infty A_j \vert E) = \sum_{j = 1}^\infty P(A_j \vert E)$
- $P(\bar{A} \vert E) = 1 - P(A \vert E)$
- Inclusion-exclusion:
$$
P(A \cup B \vert E) = P(A \vert E) + P(B \vert E) - P(A \cap B \vert E)
$$
## Baye's rule with extra conditioning
Consider $P(\cdot|E)$ as a **probability function** which assigns probabilities in accordance with the knowledge that $E$ has occurred.
$$
P(A \vert BE)  = \dfrac{P(B\vert AE)P(A \vert E)}{P(B\vert E)}
$$
## LOTP with extra conditioning
$$
P(B \vert E) = \sum_{i = 1}^n P(B \vert A_iE)P(A_i \vert E)
$$
# Independence of events
## Independence of two events
Events $A$ and $B$ are *independent* if 
$$
P(A \cap B) = P(A) P(B)
$$
If $P(A),P(B) > 0$, this is equivalent to 
$$
P(A \vert B) = P(A)
$$
and also equivalent to $P(B \vert A) = P(B)$

Note that independence is a **symmetric relation**: if $A$ is independent of $B$, then $B$ is independent of $A$
> [!Warning]
> Independent is completely different from disjointness

If $A$ and $B$ are independent, then $(A, \bar{B}), (\bar{A},B)$ and $(\bar{A},\bar{B})$ are all independent

## Independence of three events
Events $A, B, C$ are said to be independent if **all** of the equations below hold
$$
\begin{aligned}
P(A \cap B) &= P(A)P(B) \\
P(B \cap C) &= P(B)P(C) \\
P(A \cap C) &= P(A)P(C) \\
P(A \cap B \cap C) &= P(A)P(B)P(C) \\
\end{aligned}
$$
If the first three conditions hold, we say that $A$, $B$, and $C$ are *pairwise independent*. **Pairwise independence does not imply independence**, and neither vice-versa.

## Independence of $n$ events
We say events $A_1, \ldots ,A_n$ are independent if all the subsets of $\left\{ A_1, \ldots ,A_k \right\}$ satisfying $P(A_1\cdots A_k)=P(A_1) \cdots P(A_k)$, where $2 \leq k \leq n$

## Conditional independence
Events $A$ and $B$ are said to be *conditional independence* given $E$ if $P(A \cap B \vert E) = P(A \vert E)P(B \vert E)$

> [!Tip]
> - Two events can be conditionally independent given $E$, but not independent given $\bar{E}$. 
> - Two events can be conditionally independent given $E$, but not independent. 
> - Two events can be independent, but not conditionally independent given $E$.

# Coherency of Bayes' rule
An important property of Bayes' rule is that it is *coherent*: if we receive multiple pieces of information and wish to update our probabilities to incorporate all the information, it does not matter whether we update sequentially, taking each piece of evidence into account one at time, or simultaneously, using all the evidence at once.
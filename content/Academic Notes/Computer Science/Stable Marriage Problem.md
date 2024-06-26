# Problem
*Stable marriage problem* (also *stable matching problem*) is the problem of finding a *stable matching* between two equally sized sets of elements given an ordering of preferences for each element. A *matching* is a [[Injective, Surjective and Bijective#Bijective (One-to-One Correspondence)|bijection]] from the elements of one set to the elements of the other set. 

A matching is *not stable* if there is an element $A$ of the first matched set which prefers some given element $B$ of the second matched set over the element to which A is already matched, and $B$ also prefers $A$ over the element to which B is already matched.

In other words, a matching is *stable* when there does not exist any pair $(A, B)$ which both prefer each other to their current partner under the matching.

The stable marriage problem has been stated as follows:

Given $n$ men and $n$ women, where each person has ranked all members of the opposite sex in order of preference, marry the men and women together such that there are no two people of opposite sex who would both rather have each other than their current partners. When there are no such pairs of people, the set of marriages is deemed stable.

# Algorithm
The *Gale–Shapley algorithm* (also known as the *deferred acceptance algorithm*) involves a number of "*rounds*" (or "*iterations*"):

- In the first round, first a) each unengaged man proposes to the woman he prefers most, and then b) each woman replies "maybe" to her suitor she most prefers and "no" to all other suitors. She is then provisionally "engaged" to the suitor she most prefers so far, and that suitor is likewise provisionally engaged to her.
- In each subsequent round, first a) each unengaged man proposes to the most-preferred woman to whom he has not yet proposed (regardless of whether the woman is already engaged), and then b) each woman replies "maybe" if she is currently not engaged or if she prefers this man over her current provisional partner (in this case, she rejects her current provisional partner who becomes unengaged). The provisional nature of engagements preserves the right of an already-engaged woman to "trade up" (and, in the process, to "jilt" her until-then partner).
- This process is repeated until everyone is engaged.

This algorithm is guaranteed to produce a stable marriage for all participants in time $O(n^{2})$ where $n$ is the number of men or women.

Among all possible different stable matchings, it always yields the one **that is best for all men** among all stable matchings, and **worst for all women**. Because it is a truthful mechanism from the point of view of men (the proposing side), i.e., no man can get a better matching for himself by misrepresenting his preferences. 
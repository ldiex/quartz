# Definition
The indicator r.v. $I_A$ or $I(A)$ for an event $A$ is defined to be $1$ if occurs and $0$ otherwise.

# Properties
Let $A$ and $B$ be events. Then the following properties hold
1. $(I_A)^k = I_A$ for any positive integer $k$
2. $I_{A^c} = 1- I_A$ 
3. $I_{A \cap B} = I_A I_B$
4. $I_{A \cup B} = I_A + I_B - I_A I_B$

# Fundamental Bridge between Probability and Expectation
The probability of an event $A$ is the [[Mathematical Expectation|expected value]] of its indicator r.v. $I_A$:
$$
P(A) = \mathrm{E}[I_A]
$$


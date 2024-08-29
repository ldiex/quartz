# Idea
*Propositional logic*, also known as *propositional calculus*, is a branch of logic that deals with propositions, which are statements that can either be *true* or *false*. It uses logical connectives such as AND, OR, NOT, IMPLIES, and EQUIVALENT to form more complex statements from simpler ones.

The primary concern in propositional logic is the **truth value of these propositions** and **how they can be combined and manipulated to form valid logical arguments and proofs**

The most powerful tool to deal with propositional logic is [[Boolean Logic|Boolean logic]]
# Propositions
## Definition
A *proposition* is a declarative sentence (that is, a sentence that declares a fact) **that is either true or false**

We uses letters to denote *propositional variables* (or *sentential variables*), that is, variables that represent propositions, and the usually adopted variables are $p,a,r,s \cdots$ 

The *truth value* of a proposition is true, denoted by T, if it is a true proposition; and the truth value of a proposition is false, denoted by F, if it is a false proposition
## Operators
See [[Boolean Logic#Operators|Boolean logic operators]], quoted as the followings:
- $\neg x (\text{or }\bar x)$ , negation, not
- $x \land y$, conjunction, and
- $x \vee y$, disjunction, or
- $x \oplus y$, exclusive or, xor
- $x \to y$, material implication (conditional statement)
	- $(x \to y) = 1 \iff (x = 0) \vee (y = 1)$
- $x \leftrightarrow y$, bi-conditional statement
	- $(x \leftrightarrow y) = 1 \iff (x = y = 0) \vee (x = y = 1)$
### Conditional Statement
The statement $p \to q$ is called a conditional statement because $p \to q$ asserts that $q$ is true on the condition that $p$ holds. A conditional statement is also called an implication. 

> [!tip]
> **Conditional statement does not represent causal relationships**, since $p \to q$ can be true whenever $p$ is a false proposition, and in this condition $p$ and $q$ have no causal relationship

The proposition $q \to p$ is called the *converse* of $p \to q$. The *contrapositive* of $p \to q$ is the proposition $\neg q \to \neg p$. The proposition $\neg p \to\neg q$ is called the *inverse* of $p \to q$

The contrapositive $\neg q \to\neg p$ of a conditional statement $p \to q$ always has the same truth value as $p \to q$

When two compound propositions always have the same truth values, regardless of the truth values of its propositional values, we call them *equivalent*
### Precedence of Logical Operators
1. Precedence $1$: $\neg$
2. Precedence $2$: $\land$
3. Precedence $3$: $\vee$ 
4. Precedence $4$: $\to$
5. Precedence $5$: $\leftrightarrow$

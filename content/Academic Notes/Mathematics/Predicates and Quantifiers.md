# Predicates
Statements involving variables, such as $x > 3$ or "Computer $x$ is functioning properly" are neither true nor false when the values of the variables are not specified. In this section, we discuss the way that [[Propositional Logic#Propositions|propositions]] can be **produced** from such statements

The statement "$x$ is greater than $3$" has two parts: the first part is the *variable* $x$ and the second part - the *predicate* - refers to a property that the subject of the statement can have. We can denote the statement "$x$ is greater than $3$" by $P(x)$. The statement $P(x)$ is also said to be the value of the *propositional function* $P$ at $x$. Once a value has been assigned to the variable $x$, the statement $P(x)$ becomes a proposition and has a truth table.

In general, a statement involving the $n$ variables $x_1,x_2, \ldots ,x_n$ can be denoted by $P(x_1,x_2, \ldots ,x_n)$. A statement of the form $P(x_1,x_2, \ldots ,x_n)$ is the value of the **propositional function** $P$ at the $n$-tulle $(x_1, x_2, \ldots ,x_n)$, and $P$ is also called an $n$*-place predicate* or an $n$*-ary predicate*

# Quantifiers
When the variables in a propositional function are **assigned** values, the resulting statement becomes a proposition with a certain truth value.  However, there is another important way, called *quantification*, **to create a proposition from a propositional function**. 

We focus on two types of quantification here
- Universal quantification
- Existential quantification

The area of logic that deals with predicates and quantifiers is called the *predicate calculus*
## The universal quantifier
Many mathematical statements assert that a property is true for all values of a variable in a particular **domain**, called the *domain of discourse*, or just *domain*. The universal quantification of $P(x)$ for a particular domain is the proposition that asserts that $P(x)$ is true for all values of $x$ in this domain.

The notation $\forall x\ P(x)$ denotes the universal quantification of $P(x)$. Here $\forall$ is called the *universal quantifier*

## The existential quantifier
Many mathematical statements assert that there is an element with a certain property. Such statements are expressed using *existential quantification*. With existential quantification, we form a proposition that is true if and only if $P(x)$ is true for at least one value of $x$ in the domain

We use the notation $\exists x \ P(x)$ for the existential quantification of $P(x)$. Here $\exists$ is called the existential quantifier


## The uniqueness quantifier
Besides the two quantifiers mentioned above, we can define infinite number of new quantifiers. One of the most used quantifiers is the *uniqueness quantifier*.

The uniqueness quantifier is denoted as $!\exists$, the statement $!\exists x\ P(x)$ states "There exists a unique $x$ such that $P(x)$ is true." 

# Quantifiers over Finite Domains
When the elements of the domain are $x_1,x_2, \ldots ,x_n$ where $n$ is a positive integer, the universal quantification $\forall x \ P(x)$ is the same as the conjunction
$$
P(x_1) \land P(x_2) \land \cdots \land P(x_n)
$$
And also we have
$$
\exists x \ P(x) \equiv P(x_1) \lor P(x_2) \lor \cdots \lor P(x_n)
$$
# Quantifiers with Restricted Domains
An abbreviated notation is often used to restrict the domain of a quantifier. In this notation, **a condition a variable must satisfy is included after the quantifier**. That is
$$
\forall P(x) \ Q(x) \equiv \forall x \left( P(x) \to Q(x) \right) 
$$
and
$$
\exists P(x) \ Q(x) \equiv \exists x\left( P(x) \land Q(x) \right) 
$$
> [!Tip]
> Note that for existential quantification, here is $P(x) \land Q(x)$ but not $P(x) \to Q(x)$
# Precedence of Quantifiers
The quantifiers $\forall$ and $\exists$ have **higher precedence** than all logic operators from propositional calculus (see [[Propositional Logic#Precedence of Logical Operators|precedence of logical operators]])
# Binding Variables
When a quantifier is used on the variable $x$, we say that this occurrence of the variable is *bound*. An occurrence of a variable that is not bound by a quantifier or set equal to a particular value is said to be *free*. 

**All the variables that occur in a propositional function must be bound or set equal to a particular value to turn it into a proposition.** This can be done using a combination of universal quantifiers, existential quantifiers, and value assignments.

# Logical Equivalences Involving Quantifiers
Statements involving predicates and quantifiers are *logically equivalent* if and only if they have the same truth value no matter which predicates are substituted into these statements and which domain of discourse is used for the variables in these propositional functions.

For example, $\forall x(P(x) \land Q(x)) \equiv \forall x \ P(x) \land \forall x \ Q(x)$

# Negating Quantified Expressions
$$
\begin{aligned}
\neg \exists x \ P(x) &\equiv \forall x \ \neg P(x) \\
\neg \forall x \ P(x) &\equiv \exists x \ \neg P(x)
\end{aligned}
$$
This is called the *De Morgan's law for quantifiers*
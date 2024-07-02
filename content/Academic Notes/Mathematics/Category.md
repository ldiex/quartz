# Definition
A *category* $C$ consists of 
- A collection $C_0$, whose elements are called the objects of $C$ and are usually denoted by uppercase letters $X,Y,Z, \ldots$
- A collection $C_1$, whose elements are called the *morphisms* or *arrows* of $C$ and are usually denoted by lowercase letter $f,g,h, \ldots$
such that
- Each morphism has assigned two objects, called *source* and *target*, or *domain* and *codomain*. We denote the source and target of the morphism $f$ by $s(f)$ and $t(f)$, respectively. If the morphism $f$ has source $X$ and target $Y$, we also write $f: X \to Y$, or more graphically, $X \overset{f}{\to} Y$
- Each object $X$ has a distinguished morphism $\mathrm{id}_X:X \to X$, called *identity morphism*
- For each pair of morphism $f,g$ such that $t(f) = s(g)$ there exists a specified morphism $g \circ f$, called the *composite morphism*, such that $s(g \circ f) = s(f)$ and $t(g \circ f) = t(g)$. More graphically:
$$
f:X \to Y, \ g:Y \to Z \quad \rightsquigarrow \quad g \circ f: X \to Z
$$
These structures need to satisfy the following axioms
- *Unitality*: for every morphism $f: X \to Y$, the compositions $f \circ \mathrm{id}_X$ and $\mathrm{id}_Y \circ f$ are both equal to $f$
- *Associativity*: for $f : X \to Y, \ g: Y \to Z$, and $h : Z \to W$, the composition $h \circ (g \circ f)$ and $(h \circ g) \circ f$ are equal

# Categories as operations
Another way to think about categories is
> A category is a collection of operations which can be composed in a consistent way

An example for this idea is a [[Group|group]]. We can view a group $G$ as a particular category, where
- There is a single object $\bullet$
- There is a morphism $\bullet \to \bullet$ for each element $g\in G$, denoted as $g: \bullet \to \bullet$
- The identity of the object $\bullet$ is the morphism given by $1\in G$
- The composition is given by the multiplication of $G$. That is, the composition $g \circ h$ of the morphisms given by $g, h\in G$ is the morphism given by the element $g\cdot h$ of $G$

Note that we didn't use the inverse $g^{-1}$ of $g\in G$, since this property is unnecessary to form a category. Therefore, if we drop the inverse requirement, we can still get a category, and this means a [[Monoid|monoid]] can also be seen as a category

Sometimes, to distinguish the concept of a group/monoid and a category, we may define the category we get from a group $G$ as the *delooping* of $G$, denoted as $\mathbf{B}G$. Similarly, $\mathbf{B}M$ stands for the *delooping* of monoid $M$

# Categories as spaces and maps with extra structure
By the name, we can consider a category **as a collection of sets or spaces equipped with extra structure, and maps between them which are compatible with that structure**

We can therefore give some examples of category in this idea.
## Category Set
The category $\mathbf{Set}$ is the category whose objects are sets, and whose morphisms are maps (functions) between them.

For each set $X$, the identity function is a function $X \to X$. Functions can be composed, and the composition is associative.
## Category Top
The category $\mathbf{Top}$ is the category whose objects are [[Topological Space|topological spaces]], and whose morphisms are continuous maps between them
## Category Mfd
The category $\mathbf{Mfd}$ is the category whose objects are [[Smooth Manifold|smooth manifolds]], and whose morphisms are [[Smooth Function|smooth maps]] between them
## Category Vect
The category $\mathbf{Vect}$ is the category whose objects are [[Linear Space|vector spaces]], and whose morphisms are [[Linear Map|linear maps]] between them
## Category Meas
The category $\mathbf{Meas}$ is the category whose objects are *measurable spaces*, and whose morphisms are *measurable maps* between them
## Category Grp
The category $\mathbf{Grp}$ is the category whose objects are [[Group|groups]], and whose morphisms are *homomorphisms* between them, i.e. maps $f:G \to H$ such that for each $g, g'\in G$, we have $f(g\cdot g') = f(g)\cdot f(g')$
## Category Poset
The category $\mathbf{Poset}$ is the category whose objects are [[Partially Ordered Set|partially ordered sets]], and whose morphisms are *monotone maps* between them, i.e. maps $f: X \to Y$ such that for each $x,x'\in X$ with $x \leq x'$ in $X$, we have $f(x) \leq f(x')$ in $Y$

## Other examples
### Graph Theory
For [[Graph|graphs]] there are many choices of morphisms, depending on what one wants to do with graphs. For example, for undirected, unweighted graphs, a possible choice of morphisms $f:G \to H$ is function between the sets of vertices which preserve the *adjacency relation*: if the vertices $x$ and $y$ are connected by an edge in $G$, then $f(x)$ and $f(y)$ must be connected by an edge in $H$. With this choice of morphisms, graphs and these morphisms form a category.

# Considerations with Sets
From *Russell's paradox*, we know that there is no such thing as the "set of all sets" since we cannot conclude whether the set contains itself. Therefore, if we want a "category of all sets", the objects of this category cannot form a set. That is why we said *collections* rather than sets in the definition of a category

We call a category $C$ is *small* if $C_0$ and $C_1$ (see the [[Category#Definition|definition]] above) are sets. And a category $C$ is called *locally small* if for every to objects $X$ and $Y$ of $C$, the morphisms $X \to Y$ form a set

Based on this, if we let 


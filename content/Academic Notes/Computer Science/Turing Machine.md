# Basic Idea
Turing's basic idea is to use a machine to simulate the process of people performing mathematical operations with pen and paper. He views this process as consisting of the following two simple actions:

- Writing or erasing a symbol on paper;
- Moving attention from one place on the paper to another;

At each stage, a person decides the next action based on (a) the symbol at the current position they are focusing on and (b) the current state of their mind.

To simulate this human computational process, Turing constructed an imaginary machine consisting of the following parts:

1. An infinitely long tape **TAPE**. The tape is divided into small cells, each containing a symbol from a finite alphabet. There is a special symbol $\displaystyle \square$ representing a blank. The cells on the tape are numbered sequentially from left to right as $0, 1, 2, ...$ and the tape can extend infinitely to the right.
2. A read-write head **HEAD**. It can move left and right on the tape, read the symbol in the current cell, and change it.
3. A finite set of control rules **TABLE** (A finite table of instructions). It determines the next action of the read-write head based on the current state of the machine and the symbol in the current cell, changing the value of the state register and transitioning the machine to a new state.
    The Turing machine instructions are informed in the following order:
    - 1. Write (replace) or erase the current symbol;
    - 2. Move the **HEAD**, 'L' for left, 'R' for right, or 'N' for no movement;
    - 3. Retain the current state or transition to another state.
4. A **state register**. It stores the current state of the Turing machine. The number of all possible states of the Turing machine is finite, and there is a special state called the *halt state*.

## Formal Definition
A *Turing machine* is a seven-tuple $(Q, \Sigma, \Gamma, \delta, q_0, q_\text{accept}, q_\text{reject})$, where $Q, \Sigma, \Gamma$ are finite sets that satisfy:

1. $Q$ is a non-empty finite set of states.
2. $Σ$ is a non-empty finite input alphabet that does not contain the special blank symbol $\square$.
3. $Γ$ is a non-empty finite tape alphabet with $Σ \subset Γ$; $\square \in Γ - Σ$ is the *blank symbol* and is the only symbol allowed to appear infinitely.
4. $δ: (Q - \{q_\text{accept}, q_\text{reject}\}) \times \Sigma \to Q \times Γ \times \{L, R, -\}$ is the transition function where $L, R$ indicate whether the read-write head moves left or right, and $-$ indicates no movement.
5. $q_0 \in Q$ is the initial state.
6. $q_\text{accept}$ is the accepting state.
7. $q_\text{reject}$ is the rejecting state, and $q_\text{reject} \neq q_\text{accept}$.

Initially, the input string $\displaystyle \omega =\omega _{0}\omega _{1}\ldots \omega _{n-1}\in \Sigma ^{*}$ is placed from left to right in the cells numbered $\displaystyle 0,1,\ldots ,n-1$, with the other cells being blank (filled with the blank symbol $\displaystyle \square$). The read-write head of $M$ points to cell 0, and $M$ is in state $q_0$.

After the machine starts, it performs computations according to the rules described by the transition function $δ$. For example, if the current state of the machine is $q$ and the symbol in the current cell is $x$, and if $δ(q,x) = (q',x',L)$, the machine transitions to the new state $q'$, changes the symbol in the current cell to $x'$, and moves the read-write head one cell to the left.

(If at any moment the read-write head points to cell 0 and according to the transition function it is supposed to move left, it stays in place. **In other words, the read-write head never moves off the left edge of the tape**).

If at any moment the Turing machine transitions to state $q_\text{accept}$ according to the transition function, it immediately halts and accepts the input string; if it transitions to state $q_\text{reject}$, it immediately halts and rejects the input string.

# Limitations
A Turing machine cannot solve problems involving second-order logic.

# See Also
[[Church–Turing Thesis]]
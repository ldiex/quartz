We use [[Sequential Circuits|sequential circuits]] to design a 4-bit *serial adder* of unsigned integers. Unlike [[Combinational Circuits|combinational circuits]], the memory feature of [[Flip-flop|flip flops]] allows us to define two *states*
``` mermaid
flowchart LR
	Q0((State Q0)) --> |11/0| Q1((State Q1))
	Q1 --> |00/1| Q0
	Q0 --> |00/0,01/1,10/1| Q0
	Q1 --> |01/0,10/0,11/1| Q1
```
where the `XY/Z` notation stands for *two operands* / *carry-in*. Since the states require only one bit to remember, we only need use one [[Flip-flop#D Flip Flop|D flip-flop]] to hold the states. The organization of the adder are drawn as
``` mermaid
flowchart LR
    In([In]) --> G[Combinational<br> Circuit G]
    G -->|Qnext| D[D Flip-Flop]
	CLK([CLK]) --> D
    D -->|Q| F[Combinational<br> Circuit F]
    D -->|Q| G
    F --> Out([Out])
	In --> F
```
The [[Combinational Circuits|combinational circuit]] G are defined as
$$
\mathrm{Q_{next} = G(X,Y,Q) = (X\cdot Y) + (X \oplus  Y)\cdot Q}
$$
and the circuit F is
$$
\mathrm{Out = F(X,Y,Q) = X \oplus Y \oplus Q}
$$

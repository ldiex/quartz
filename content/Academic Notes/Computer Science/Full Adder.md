A *full adder* is a fundamental [[Combinational Circuits|combinational circuit]] used in [[Computer Science|computer science]] and electronics for performing binary addition.

A full adder adds three binary inputs - two *operands* (A and B) and a *carry-in* (C-in) from a previous addition - and produces two outputs: a *sum* and a *carry-out* (C-out)

We can conclude the outputs using [[Boolean Logic|Boolean logic]]:
$$
\mathrm{Sum = A \oplus  B \oplus  C_{in}, \quad C_{out} = (A \land B) \vee (B \land C_{in}) \vee (A \land C_{in})}
$$


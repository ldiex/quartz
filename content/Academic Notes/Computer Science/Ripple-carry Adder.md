A *ripple-carry adder* is a [[Combinational Circuits|combinational circuit]] used in computer science and digital electronics for **adding multi-bit binary numbers**. A ripple-carry adder consists of multiple [[Full Adder|full adder]] circuits connected in series. Each full adder adds two corresponding bits from the input numbers along with the carry from the previous stage.

The adder works by "rippling" the carry information from one full adder to the next. The carry output from each stage becomes the carry input for the next more significant stage.

It can add two $n$-bit binary numbers by cascading $n$ full adder stages. For example, to add two 4-bit numbers, four full adders would be connected in series.

``` mermaid
graph LR
    A0[A0] --> FA0[FA0]
    B0[B0] --> FA0
    Cin[Cin] --> FA0
    A1[A1] --> FA1[FA1]
    B1[B1] --> FA1
    A2[A2] --> FA2[FA2]
    B2[B2] --> FA2
    A3[A3] --> FA3[FA3]
    B3[B3] --> FA3
    
    FA0 --> S0[S0]
    FA1 --> S1[S1]
    FA2 --> S2[S2]
    FA3 --> S3[S3]
    
    FA0 --Carry--> FA1
    FA1 --Carry--> FA2
    FA2 --Carry--> FA3
    FA3 --Carry--> Cout[Cout]
    
    style FA0 fill:#f9f,stroke:#333,stroke-width:2px
    style FA1 fill:#f9f,stroke:#333,stroke-width:2px
    style FA2 fill:#f9f,stroke:#333,stroke-width:2px
    style FA3 fill:#f9f,stroke:#333,stroke-width:2px
```

The main limitation of a ripple-carry adder is its *propagation delay*. As the carry has to propagate through each full adder stage before reaching the final stage, the delay increases with the number of bits being added. The worst-case delay occurs when the carry has to propagate from the least significant bit to the most significant bit, in which case the total delay counts up to $2n+1$

*Flip Flop* is an electronic device or to be precise a kind of [[Computer Memory|memory]] component that can hold one bit of data. A flip flop has two states, that is “*SET*” and “*RESET*”. Those states are represented with the binary values 0 and 1. **The flip flop remains in its current state until its receives a signal that switches it to opposite state.** A clock or pulse signal may “trigger” the flip flop to change state.
# D Flip Flop
*D flip flop* is an electronic devices that is known as “*delay flip flop*” or “*data flip flop*” which is used to **store single bit of data**. D flip flops are synchronous or asynchronous (see [[Sequential Circuits|sequential circuits]]). The clock single required for the synchronous version of D flip flops but not for the asynchronous one. 

The D flip flop has two inputs, data D and Clock. When Clock input is high, the data is transferred to the output of the flip flop and when the clock input is low, the output of the flip flop is held in its previous state.

``` mermaid
graph LR
    D[D] --> M1[MUX]
    C[Clock] --> M1
    M1 --> S
    M1 --> R
    S[Set] --> Q[Q]
    R[Reset] --> NQ[Q']
    Q --> |Feedback| M1
    NQ --> |Feedback| M1
    style D fill:#f9f,stroke:#333,stroke-width:2px
    style C fill:#ff9,stroke:#333,stroke-width:2px
    style Q fill:#9ff,stroke:#333,stroke-width:2px
    style NQ fill:#9ff,stroke:#333,stroke-width:2px
    style M1 fill:#f96,stroke:#333,stroke-width:2px
    style S fill:#9f9,stroke:#333,stroke-width:2px
    style R fill:#9f9,stroke:#333,stroke-width:2px
```

The following is the truth table of D flip flop

| Clock | D   | Q   | Q'  | Description        |
| ----- | --- | --- | --- | ------------------ |
| Low   | X   | Q   | Q'  | Memory (No Change) |
| High  | 0   | 0   | 1   | Reset (Q = 0)      |
| High  | 1   | 1   | 0   | Set (Q = 1)        |

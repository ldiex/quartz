Every *processor* has an [[Instruction Set|instruction set]], which is the set of all possible instructions of the processor, organized in a systematic way. The *instruction pipeline* is the hardware that executes the instructions. 

A 3-stage instruction pipeline is shown in this figure:
``` mermaid
flowchart LR
    A["Instruction Stream<br>...... I4 I3 I2 I1"] --> IF
    IF["IF"] --> ID["ID"]
    ID --> EX["EX"]
    B["InIF(t)"] --> IF
    C["InID(t)"] --> ID
    D["InEX(t)"] --> EX
    IF --> E["OutIF(t)"]
    ID --> F["OutID(t)"]
    EX --> G["OutEX(t)"]
```
The three stages are *instruction fetch (IF)*, *instruction decode (ID)*, and
*instruction execute (EX)* stages. Every stages can be implemented through [[Sequential Circuits|sequential circuits]]

An instruction is first fetched from the memory to an *instruction register (IR)* in the processor. It is then decoded to generate proper control signals. The control signals are then applied, together with the clock signal, to drive the multiplexers, thus to execute the instruction and produce the result. For instance, the processing of the `MOV 0, R1` (see [[Assembly Language (ASM)|ASM instructions]]) instruction stores an immediate value 0 to register R1. It goes through the following three stages.

- Instruction Fetch (IF): $\mathrm{IR \leftarrow  M[PC]}$
- Instruction Decode (ID): $\mathrm{Signals = Decdoe(IR)}$
- Instruction Execute (EX): $\mathrm{R1 \leftarrow 0; \; PC \leftarrow PC + 1}$

where
- IR stands for *Instruction Register*, a special register in the processor that temporarily holds the instruction that is currently being executed. When an instruction is fetched from memory, it is stored in the IR before being decoded and executed.
- PC stands for *Program Counter*, another special register that holds the memory address of the next instruction to be fetched and executed. It's sometimes also called the *instruction pointer (IP)*. As the program runs, the PC is typically incremented to point to the next instruction in sequence, unless a jump or branch instruction changes its value.

Having more pipeline stages can help increase the clock frequency, thus making
the processor faster. Modern processors have 5–31 pipeline stages.
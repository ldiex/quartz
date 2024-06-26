*Base-indexed addressing mode* is an addressing mode that uses the contents of a *base register* and an *index register* to calculate an operand's offset. The offset is then added to the PC to determine the memory location where the operand will be placed.

$$
\mathrm{address} = \mathrm{base} + \mathrm{index} \times \mathrm{coefficient} + \mathrm{offset}
$$

For example, consider a `int` array in [[C Programing Language|C programing language]], the size of each element is 32 bit (4 Byte), therefore the $\mathrm{coefficient} = 4$, and the $\mathrm{index}$ is the index `i` of `a[i]`


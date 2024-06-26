# Binary Representation of Numbers
## Sign-Magnitude Representation
For example
$$
125= 1 \times 2^6 + 1 \times 2^5+ 1 \times 2^4 + 1 \times 2^3 + 1 \times 2^2 + 0 \times 2^1 + 1 \times 2^0
$$
and
$$
0.6875 = 1 \times 2^{-1} + 0 \times 2^{-2} + 1 \times 2^{-3} + 1 \times 2^{-4} 
$$
Therefore, `bin(125.6875) = 111101.1011`

The *sign-magnitude representation* includes a sign bit, where $0$ represents a positive number and $1$ represents a negative number.
## One's Complement
The one's complement of a positive number is the number itself. For a negative number, all bits except the sign bit are inverted.

## Two's Complement
The two's complement of a positive number is the number itself. For a negative number, it's the one's complement plus 1.

# IEEE 754 Floating-Point Representation
A single-precision floating-point number has 32 bits.
For example:
$$
\begin{aligned}
\pi  & \approx3.1415927\times10^0  \\
 & \approx 1.5707964 \times2^1 \\
 & \approx +1.10010010000111111011011 \times 2^{00000001} \\
& \approx +.10010010000111111011011 \times 2^{00000001} \\
\end{aligned}
$$
The significant digits part is called the **mantissa**, and the exponent part is also called the **exponent**.
The mantissa must start with $1.$, **which allows us to omit the $1$ before the decimal point**.
The exponent has 8 bits, the mantissa has 23 bits after omitting the leading 1, and there's 1 sign bit.
Thus, we get the IEEE 754 single-precision floating-point representation of $\pi$:
$$
\pi = \color{red}\underbracket{0}_{\text{sign}}\color{black}\underbrace{\boldsymbol{10000000}}_{\text{exponent}}\underbrace{10010010000111111011011}_{\text{mantissa}}
$$
- The leftmost (highest) bit is the **sign bit**
- The exponent comes first, note that it needs to add a **bias**, i.e., the exponent part needs to add an **offset** of $127$
- The mantissa follows

Similarly:
$$
\begin{aligned}
-2.5  & \approx -1.25\times 2^1 \\
 & \approx -1.01000000000000000000000 \times 2^{00000001} \\
& \approx -.01000000000000000000000 \times 2^{00000001}
\end{aligned}
$$
Therefore:
$$
-2.5=\color{red}1\color{black}\boldsymbol{10000000}01000000000000000000000
$$
$$
-2.5=1 10000000 01000000000000000000000
$$

## Classification of Floating-Point Numbers
### Normalized Numbers
The exponent bits (after adding 127) are not all 0 or all 1, so the range of the exponent is $[-126,127]$. The range of **normalized numbers** is:
$$
\pm [1,2) \times 2^{[-126,127]}
$$

### Denormalized Numbers
The exponent bits are all 0, but the mantissa is not all 0.
In this case, the actual exponent is **defined** as $-126$, representing the range $\pm (0,1)\times 2^{-126}$

### Zero
Zero has two forms. In denormalized numbers, set all mantissa bits to 0. By changing the sign bit, we have **positive zero** and **negative zero**.

### Infinity
All exponent bits are 1, and all mantissa bits are 0. By changing the sign bit, we get $+\infty$ and $-\infty$.

### Not a Number
All exponent bits are 1, and not all mantissa bits are 0, representing $\text{NaN}$.

# ASCII Table

| Dec | Octal | Hex | Char |
|---|---|---|---|
| $0$  | $000$  | 0x00 | NUL (Null) |
| $9$  | $011$  | 0x09 | HT (Horizontal Tab) |
| $10$ | $012$  | 0x0A | LF (Line Feed) |
| $13$ | $015$  | 0x0D | CR (Carriage Return) |
| $32$ | $040$  | 0x20 | Space |
| $48$ | $060$  | 0x30 | 0 |
| $57$ | $071$  | 0x39 | 9 |
| $65$ | $101$  | 0x41 | A |
| $90$ | $132$  | 0x5A | Z |
| $97$ | $141$  | 0x61 | a |
| $122$ | $176$  | 0x7A | z |

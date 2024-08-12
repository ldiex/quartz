In computer programming, *assembly language*, often referred to simply as assembly and commonly abbreviated as *ASM* or *asm*, is any low-level programming language with a very strong correspondence between the instructions in the language and the architecture's machine code instructions. Assembly language usually has one statement per machine instruction (1:1)

# Basic Instructions

## MOV(Move)
This fundamental instruction is used to transfer data between locations within the computer's memory. It essentially copies data from one place to another.

``` asm
MOV destination, source
```
- **destination:** This specifies where the data will be copied to. It can be a register (a temporary storage location within the CPU) or a memory address.
- **source:** This indicates where the data is being copied from. It can also be a register or a [[Memory Address|memory address]].

For example
``` asm
MOV  AX, 10  ; Move the value 10 into register AX
```
Here the number $10$ (source) is copied into the AX register (destination).

## ADD(Add)
This instruction performs addition on two operands and stores the result in a specified location. It's crucial for performing arithmetic operations within your Assembly program.

There are a few variations depending on the specific architecture and desired operation:

1. Register to register:
``` asm
ADD destination_register, source_register
```
2. Register to immediate value:
``` asm
ADD destination_register, immediate_value
```
3. Memory to register:
``` asm
ADD destination_register, memory_address
```

## INC(Increment)
This instruction efficiently increases the value of an operand by 1.
``` asm
INC operand
```
Here, the `operand` can be:
- A register (like AX, BX, etc.)
- A memory location (accessed through addressing modes)

**Functionality:**
- The INC instruction adds 1 to the value stored in the specified operand.
- The incremented value is then written back to the same operand location.

## CMP(Compare)
The **CMP (Compare)** instruction in Assembly language is a fundamental tool for making decisions within your program. It performs a comparison between two operands but doesn't modify the operands themselves.

``` asm
CMP operand1, operand2
```

where
- **operand1:** This is the first value to be compared. It can be a register or a memory location.
- **operand2:** This is the second value to be compared. It can also be a register or a memory location, or even an immediate value (a constant).

**Functionality:**
1. The CMP instruction subtracts `operand2` from `operand1`.
2. It sets specific flags in the CPU's status register based on the comparison result, but doesn't change the original values.

**Status Flags:**
- **Zero Flag (ZF):** Set to 1 if the result of the subtraction is zero (meaning operand1 equals operand2).
- **Carry Flag (CF):** Set to 1 if there's a borrow operation during the subtraction (relevant for unsigned integer comparison).

**Example:**
``` asm
MOV  AX, 5   ; Move the value 5 to AX register
CMP  AX, 10  ; Compare AX with 10
```
In this example, the CMP instruction subtracts 10 from 5 (stored in AX). Since the result is negative, the Zero Flag (ZF) won't be set. The Carry Flag (CF) might be set depending on the architecture and whether unsigned comparison is assumed.

### Conditional Jumps and CMP
The true power of CMP lies in its synergy with conditional jump instructions. By examining the status flags set after a CMP, you can control program flow based on the comparison outcome. Here are some examples:
- **JE (Jump if Equal):** Jumps to a specific memory location if the Zero Flag (ZF) is set (meaning operand1 equals operand2).
- **JG (Jump if Greater):** Jumps if the comparison indicates operand1 is greater than operand2 (condition for unsigned integers typically involves both the Zero Flag (ZF) and Carry Flag (CF)).
- **JL (Jump if Less):** Jumps if the comparison indicates operand1 is less than operand2 (condition for signed integers typically relies on the Sign Flag (SF) set by the CMP instruction).

**Use Cases:**
- Conditional branching in decision-making logic (e.g., checking if a user input matches a password).
- Sorting algorithms (comparing elements).
- Loop control (checking loop termination conditions).

# Lecture 2: ISA – Storage and Addressing Models

This is the beginning of a series of notes on the ISA – Instruction Set Architecture. The ISA is an architecture that defines the *interface between compilers, and the hardware*. It is the connection layer between microarchitecture (hardware implementation of ISA), and the compilers.

For example, if making a robot whose only function was to follow you around, what instructions would you want? Here are a few ideas:

* `forward(speed)`
* `back(speed)`
* `turn`
* `stop`
* `run`

There are a few things to note here:

* ISA instructions can define **operands**, such as the operand `speed` for the `forward` command.
* ISA instructions can be somewhat overlapping in function - the `forward` and `run` commands are pretty similar in purpose, but one allows you to specify the speed at which it runs. The choice to use more, overlapping instructions for specific purposes, instead of fewer, more general commands, *is actually an active debate!*

## ISA Design – Freedom and Choices

ISA design focuses on 3 main aspects:

#### Functionality

* **Arithmetic functions**: `add`, `multiply`, `divide`, `sqrt`
    * Some of these may be overlapping in function, such as multiply and divide. However, hardware implementation of these functions may differ, so those operations are more efficient.
* **Branching**: Redirecting the flow of execution of code to different paths.
    * This happens in `if` statements, but also conditionals in `for` statements and function calls.
* **Load/store**: Moving data from one place to another. Usually involves moving information from the *processor registers* to the *DRAM*. 
    * The processor registers are memory storage units directly in the processor, that allow for extremely fast read/write times. However, in most computers, the registers only have memory to store about **16 integers**. 
    * The DRAM, on the other hand, can store much, much more, but the read/write speed is on the order of magnitude of hundreds of clock cycles.
    * The compiler usually does the optimization of whether to store a variable in registers or DRAM.
* `mmx_add`
    * higher level vector addition operations, not covered in this EECS 370.

#### Storage

* How many registers should be available?
* How much memory should be available in DRAM?
* What is the architecture of the storage?

#### Operands

* How should instructions be formatted?
* Can you have 0, 1, 2, or more operands?
* How are **immediate operands** handled?

**Side note**: *Immediate operands* are constants in the instruction code, rather than using a variable such as a register.

## Instruction Encoding

#### RISC vs CISC

* A *RISC instruction set* is a Reduced Instruction Set Computer.
    * An instruction set with fewer, more simple commands for general purposes.
    * **Benefits**: More efficient instructions
    * **Drawbacks**: Less specialized commands for programmers; worse backwards compatibility.
    * **Examples**: ARM, LC2K (what we emulate in EECS 370)
* A *CISC isntruction set* is a Complex Instruction Set Computer.
    * Philosophy: More commands are better. "Should we need include a `sqrt` function? Why not?"
    * **Benefits**: More specialized commands for programmers, better backwards compatibility.
    * **Drawbacks**: Reduces efficiency of each instruction.
    * **Examples**: x86 (which we use today!), UAX

In specialized instruction sets, programmers are actually given a CISC instruction set which is internally converted to a RISC instruction set (with the necessary overhead, of course).

## Translation of Software into Machine Code

First, you have a C program. The C program is then compiled into assembly code. This produces platform-specific instructions. For example, while iPhone compilation produces ARM assembly code, Intel compilation produces x86 code.

To see the assembly code produced from a C program, use:

```bash
gcc -S filename.c
```

This produces a file, `filename.s`, which contains the assembly code.

## Assembly Code

Consists of **instructions**, with the following fields:
* **Opcode**: A name of the instruction to perform. Similar to a function name in programming.
* **Source (input)** operand: Which registers or immediate values are input to the instruction.
* **Destination (output)** operand: Which register to store the final value in.

Example:

```
add R2 100 R1
```

This adds 100 to the value of the register `R1`, and stores the final result in `R2`.

### Example

The program is as follows:

```assembly
add R3 R1 R2
mul R3 R3 3
sub R2 R3 R1
```

If the initial value of the registers is the following:
* **R1**: 25
* **R2**: -4
* **R3**: 52

What is the final result of the registers after the program executes?

#### Answer

* **R1**: 25
* **R2**: 38
* **R3**: 63

## Assembly Instruction Encoding

Since EDSAC (1949), all computers store instructions in the same way that they store data. Each instruction is a number:
* Each opcode has a unique number associated with it. For example, `add` may arbitrarily be 53.
* Each register has a binary number associated with its number. For example, if there were sixteen registers, then each register could be enumerated from 0-15 in three bits.

Hence, the following commands are equal:
```
add     r3      r2      r1
11011   011     010     001

= 11011011010001
```

#### Bits and Encoding

\\(m\\) bits can encode \\(2^m\\) different values.
\\(n\\) values can be encoded in \\(\lceil \log_2(n) \rceil\\) bits

## Exercise

What is the max number of registers that can be designed by a machine given:
* 16 bit instructions
* Num opcodes: 100
* All instructions are of form `(reg1, reg2) -> reg3`

Size of opcode: \\(\lceil \log_2 (100) \rceil = 7\\), 9 bits remain. Since there are three arguments, `reg1`, `reg2`, and `reg3`, each register number must have 3 bits. Hence, there are \\(2^3 = 8\\) possible registers.

As a side note, x86 is 64-bit, which means that many bits are unused. This allows for many more opcodes in the future – which helps CISC goals.








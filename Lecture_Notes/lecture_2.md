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







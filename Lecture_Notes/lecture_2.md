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

* Add, multiply, divide, sqrt
* Branching
* Load/store
* `mmx_add`
    * higher level vector addition operations, not covered in this EECS 370.
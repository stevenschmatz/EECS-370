# Discussion 1

#### Communication

How do we communicate? Language. We have a common protocol to communicate. Computer languages like C serve the same purpose – i.e., to connect humans and computers.

The CPU understands binary (0 and 1), so `gcc` or `g++` converts your C code to a binary executable.

#### Binary Representation

* **Two's complement notation**
    * Flip each bit, and add one.
    * Most widely used notation for binary numbers.
* Examples
    * `int x = 5;`. The real storage in the computer is `00000101`, since `int`s are allocated 8 bits.
    * `int x = -5;`. The real storage in the computer is `11111011`, according to two's complement notation.

#### C vs C++ differences

##### C
A racing car that goes incredibly fast, but breaks down every fifty miles.

**Features not in C**:
* Classes and objects
* Namespaces
* `new` and `delete`
* `cout` and `cin`
* Data Structures
* `string` datatype
* Pass by reference (`&`)

##### C++
An advanced version of the C racing car, with lots of improvements and dozens of extra features that increase the breaking down limit to 250 miles.


##### Assembly
You are the car. It breaks down every few feet.
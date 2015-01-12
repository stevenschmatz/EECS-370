# Discussion 1

## Communication

How do we communicate? Language. We have a common protocol to communicate. Computer languages like C serve the same purpose – i.e., to connect humans and computers.

The CPU understands binary (0 and 1), so `gcc` or `g++` converts your C code to a binary executable.

#### Binary Representation

* **Two's complement notation**
    * Flip each bit, and add one.
    * Most widely used notation for binary numbers.
* Examples
    * `int x = 5;`. The real storage in the computer is `00000101`, since `int`s are allocated 8 bits.
    * `int x = -5;`. The real storage in the computer is `11111011`, according to two's complement notation.

## C vs C++ differences

### C
A racing car that goes incredibly fast, but breaks down every fifty miles.

#### Features not in C

* Classes and objects
* Namespaces
* `new` and `delete`
* `cout` and `cin`
* Data Structures
* `string` datatype
* Pass by reference (`&`)

### C++
An advanced version of the C racing car, with lots of improvements and dozens of extra features that increase the breaking down limit to 250 miles.


### Assembly

You are the car. It breaks down every few feet.

## C examples

Hello world:
```c
#include <stdio.h>
int main() {
    printf("Hello World");
}
```

Printing numbers, zero through 9:

```c
#include <stdio.h>
int main() {
    int i;
    for (int i = 0; i < 10; i++) {
        printf("i = %d\n", i);
    }
}
```

### Strings in C

##### Initializing strings

There is no `string` type in C. Use `char *` or `char[]` instead.

```c
char *text = "Hello";
char text[] = {'H', 'e', 'l', 'l', 'o', '\0'};
```

**Do not forget the null sentinel**, if using list initialization!

##### Copying strings

What's wrong with this?

```c
char *text = "Hello";
char *copy;
copy = text;
```

Both `text` and `copy` are pointing to the same address of the string. If `text` is changed, so is `copy`, and you might not want that.

##### String comparison

What's wrong with this?

```c
char *text = "Hello";
if (text == "Hello") {
    // ...
}
```

It is comparing a `char *` of the memory location of the string `text`, to the memory address of a local string `"Hello"`. This would always return false.

### Memory Allocation in C

```
int *foo;
foo = (int *) malloc(sizeof(int)); // Allocates memory for int
*foo = 5;

// ...

free(foo);
```

Use this instead of `new` and `delete`.

## Debugging

##### Common bugs

* Seg faults
* Memory leaks
* Infinite loops

##### Common solutions

###### Bad:
* Shout at computer
* `cout` statements, if you're a noob
    * If you encounter a segfault, `cout` isn't going to save you.

* Breakpoints and `gdb`.












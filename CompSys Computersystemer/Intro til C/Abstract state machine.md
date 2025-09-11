
The program text describes (code) an abstract state machine that regulates how the program switches from one state to the next. These transitions are determined by value, type, and binary representation only.

**Programs execute as if following the abstract state machine.**

How a concrete executable manages to follow the description of the abstract state machine is left to the discretion of the compiler creators.

Most modern C compilers produce code that doesn’t follow the exact code prescription: they cheat wherever they can and only respect the observable states of the abstract state machine.
## Observable state

Observable states consist of the contents of some variables (and similar entities) and the output as they evolve during the execution of the program. This whole mechanism of **change** is called the abstract state machine.

To explain the abstract state machine, we first have to look into the concepts of a **value** (what state are we in), the **type** (what this state represents), and the **representation** (how state is distinguished).

**Once the abstract state machine reaches an undefined state, no further assumption about the continuation of the execution can be made**

**If the program state reaches an operation with undefined behavior, the execution has failed.**

**Signed arithmetic may trap badly (cause undefined state or is terminated abruptly)**
### Value
[[Terminology#Value|Definition from POP]]

A [[Values and data|value]] in C is an abstract entity that usually exists beyond your program, the particular implementation of that program, and the representation of the value during a particular run of the program.
As an example, the value and concept of 0 should and will always have the same effects on all C platforms.

**All values are numbers or translate to numbers!!**
This property really concerns all values a C program is about, whether these are the characters or text we print, truth values, measures that we take, or relations that we investigate.
These numbers are mathematical entities that are independent of the program and its concrete realization.

We don’t want the result of a computation to depend on the executable (which is platform specific) but ideally to depend only on the program [[Terminology#Specification|specification]] itself.
### Type
A [[Terminology#Types|type]] is an additional property that C associates with values.

**1. All values have a type that is statically determined!!**
**2. Possible operations on a value are determined by its type**
**3. A value’s type determines the results of all operations.**


### Representation

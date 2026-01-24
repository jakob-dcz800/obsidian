# Register names

![[Pasted image 20260119180441.png]]

**imm** is immediate value (constant)
rd is destination register
rs1 and rs2 are source registers
## Conventions

x1(ra) holds address which will be jumped to when returning. 
x2(sp) be decreased to allocate stack space for additional arguments, especially important for recursive functions.
x10-x17(a0-a7) contains function arguments. 
Caller writes to these registers, and Callee reads from them.
x5-x7(t0-t2) and x28-x31(t3-t6) are used to hold intermediate values during computations.

NOTE: These are calling CONVENTIONS, not rules, they are typically followed, but not mandatory.
# Pseudo instructions

An instruction allowed in the assembly syntax, but translated into one or more other instructions by the assembler.

> Pseudo instructions are shortcuts


| Pseudo     | Meaning        | Real                 |
| ---------- | -------------- | -------------------- |
| mv xi , xj | Move           | addi xi , xj , 0     |
| li xi , k  | Load immediate | addi xi , zero, k    |
| neg xi     | Negate         | sub xi , zero, xj    |
| nop        | No operation   | add zero, zero, zero |
_Why are they not implemented directly in hardware?_
a: They are clearly redundant...
more instructions mean more complexity in relation to instruction types and so on...
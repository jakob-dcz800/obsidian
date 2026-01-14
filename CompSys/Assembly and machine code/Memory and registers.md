---
tags:
  - Programming
  - Computer
---
## Main differences

[[CompSys/Hardware/Memory hierarchy|Memory]] is **dynamically addressable**, while the registers are statically encoded in instructions.

![[Pasted image 20250904205535.png]]

### Example

Here were are manipulating the memory:

```asm
main:
        addi    sp,sp,-32 // set stack pointer to -32
        sw      ra,28(sp) // store return address
        sw      s0,24(sp) // store saved register
        addi    s0,sp,32 // set sp = 0 and store in s0
        li      a5,5 // load 5 into a5
        sw      a5,-20(s0) // store a5 in memory
        li      a5,0 // load 0 into a5
        mv      a0,a5 // move a5 into a0
        lw      ra,28(sp) // load word into ra
        lw      s0,24(sp) // load var into s0
        addi    sp,sp,32 // add 32 to sp
        jr      ra
```

With code:

```c
int main() {
    int a = 5;
}
```

## Assembly instructions


| Instructions   | Meaning               | Aka.      |
| -------------- | --------------------- | --------- |
| `lb xi, v(xj)` | `xi = Memory[xj + v]` | load byte |
| `sb xi, v(xj)` | `Memory[xj + v] = xi` | save byte |
| `lw xi, v(xj)` | `xi = Memory[xj + v]` | load word |
| `sw xi, v(xj)` | `Memory[xj + v] = xi` | save word |
`v(xj)` is a pointer with some offset: 
	`xj`: [[Pointers|pointer]]
	`v`: some offset
`xi` is the register that were putting the address in

| Instructions     | Meaning | Aka.                |
| ---------------- | ------- | ------------------- |
| `beq x1, x2, L1` |         | Branch if equal     |
| `bne x1, x2, L1` |         | Branch if NOT equal |

### Loop in RISC-V

With code
```c
while(save[i] == k)
	i += 1;
```

```asml
Loop:
	slli x10, x22, 2    // temp reg x10 = i * 4
	add x10, x10, x25   // address of save[i]
	lw x9, 0(x10)       // temp reg x9 = save[i]
	bne x9, x24, Exit   // go to exit if save[i] == k
	addi x22, x22, 1    // i = i + 1
	beq x0, x0, Loop    // go to loop (since x0 == x0)
Exit:
```


## Steps for procedures

When making a sub-procedure of an assembly program (a function for example), follow these steps:
1. Put parameters in a place where procedures can access them
2. Transfer control to the procedure
3. Acquire the storage needed for the procedure
4. Perform the task
5. Put the result in a place where the caller can access it
6. Return control to the point of origin since a procedure can be called from multiple places in a program.

x10-x17 are meant to pass parameters
x1 is the return address

```asm
jal x1, Procedure    // jump-and-link stores the ra to x1
jal x0, Procedure    // doesn't store ra
jalr x0, 0(x1)       // returns to caller
```

## Using more registers

When more values are needed than there are registers - a [[Stakke, køer, lister, hobe|stack]] is used.
When a procedure is called, the current state is stored such that the procedure can set registers to whatever it needs only to restore the original values when done.

### The stack
The stack needs a [[Pointers|pointer]] to where the current space is reserved

![[asm_stack.excalidraw]]

### Preservation

What is preserved during procedures?

| Preserved                           | Not preserved                         |
| ----------------------------------- | ------------------------------------- |
| Saved registers: `x8-x9`, `x18-x27` | Temp registers: `x5-x7`, `x28-x31`    |
| Stack pointer register: `x2(sp)`    | Argument/ result registers: `x10-x17` |
| Frame pointer: `x8(fp)`             |                                       |
| Return address: `x1(ra)`            |                                       |
| Stack *above* the stack pointer     | Stack *below* the stack pointer       |



## Main differences

Memory is **dynamically addressable**, while the registers are statically encoded in instructions.

![[Pasted image 20250904205535.png]]

## Assembly instructions


| Instructions   | Meaning               | Aka.      |
| -------------- | --------------------- | --------- |
| `lb xi, v(xj)` | `xi = Memory[xj + v]` | load byte |
| `sb xi, v(xj)` | `Memory[xj + v] = xi` | save byte |
| `lw xi, v(xj)` | `xi = Memory[xj + v]` | load word |
| `sw xi, v(xj)` | `Memory[xj + v] = xi` | save word |
`v(xj)` is a pointer with some offset: 
	`xj`: pointer
	`v`: some offset
`xi` is the register that were putting the address in

## Example

Here were are manipulating the memory:

```asm
main:
        addi    sp,sp,-32
        sw      ra,28(sp)
        sw      s0,24(sp)
        addi    s0,sp,32
        li      a5,5
        sw      a5,-20(s0)
        li      a5,0
        mv      a0,a5
        lw      ra,28(sp)
        lw      s0,24(sp)
        addi    sp,sp,32
        jr      ra
```

With code:

```c
int main() {
    int a = 5;
}
```

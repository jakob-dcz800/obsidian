---
tags:
  - Computer
banner:
---

| Logical operations    | C operation | [[RISC-V]]  |
| --------------------- | ----------- | ----------- |
| Shift left            | `<<`        | `sll, slli` |
| Shift right           | `>>`        | `srl, srli` |
| Shit right arithmetic | `>>`        | `sra, srai` |
| Bit-by-bit AND        | `&`         | `and, andi` |
| Bit-by-bit OR         | \|          | `or, ori`   |
| Bit-by-bit XOR        | `^`         | `xor, xori` |
| Bit-by-bit NOT        | `~`         | `xori`      |
## Example

### A0

`(A ^ B) & A = (A & ~B)`

| `A` | `B` | `A ^ B` | `(A ^ B) & A` |
| --- | --- | ------- | ------------- |
| `1` | `1` | `1`     | `1`           |
| `1` | `0` | `0`     | `0`           |
| `0` | `1` | `0`     | `0`           |
| `0` | `0` | `1`     | `0`           |

| `A` | `B` | `~B` | `(A & ~B)` |
| --- | --- | ---- | ---------- |
| `1` | `1` | `0`  | `0`        |
| `1` | `0` | `1`  | `1`        |
| `0` | `1` | `0`  | `0`        |
| `0` | `0` | `1`  | `0`        |

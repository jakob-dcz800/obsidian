# Instructions

Functions can be called with the instructions:
JAL (jump and link)
JALR (jump and link register)

> OBS
> JALR x0, x1, 0 does NOT call functions, it returns from functions

Functions can be called with the **pseudo instructions**:
J offset : jump
JAL offset : jump and link
JR rs : jump register 
JALR rs : jump and link register
CALL offset : jump and link to far away address

RET (JALR x0, x1, 0) returns from a function.

## Convention

• Registers a0-7 are used to store arguments. 
• Argument [[registers]] are recognized by using the register in function without first having written to it in that function.

• Caller 
- Passes arguments to Callee, by loading registers a0-a7 
- Jumps to Callee (JAL, JALR, etc.)

• Callee 
- Performs function (read arguments from a0-7) 
- Returns results to Caller (if any) in a0-1 
- Returns to point of call (RET) 
## Example

![[Pasted image 20260120175633.png]]
Full forwarding (a.k.a. _bypassing_) means:

The CPU sends results directly from later pipeline stages (EX/MEM/WB) to earlier ones (EX) so an instruction can use a value without waiting for it to be written back to the register file.

Why it matters:  
It eliminates most [[Hazards|data-hazard]] stalls (e.g., back-to-back `addi`, `add`, `sb`), keeping the pipeline full.

## ALU operations
Result gets forwarded from the Ex stage
![[Pasted image 20260120202952.png]]

## Load operations
Result gets forwarded from the Me stage

![[Pasted image 20260120203056.png]]

## Branch operations
• Backward branch (loop) taken
	• Predicted at De stage 
	• PC gets written after the decode stage (early)
	
> write:
> Here we assume that a backward taken branch is predicted during De
> ![[Pasted image 20260120210252.png]]
> And maybe "*even if De is stalled*". (if the De is actually stalled)
> ![[Pasted image 20260120210305.png]]

• Backward branch not taken 
	• Predicted at Ex stage 
	• PC gets written after the execute stage 
• Forward branch (if/else) taken 
	• Predicted at Ex stage 
	• PC gets written after the execute stage 
• If we guess wrong we lose cycles

### Jump instruction ?

![[Pasted image 20260120222010.png]]

Here, assume that the taken branch is executed during **De**
## Example

Stages:

1. **IF** – Instruction Fetch
2. **ID** – Instruction Decode / Register Read
3. **EX** – Execute / ALU
4. **MEM** – Memory Access
5. **WB** – Write Back
**Full forwarding** means results are forwarded from **EX/MEM** or **MEM/WB** pipeline registers directly to the **EX stage**, avoiding stalls.

```asml
ADD  x5, x1, x2     # x5 = x1 + x2
SUB  x6, x5, x3     # x6 = x5 - x3
AND  x7, x6, x4     # x7 = x6 & x4
```

| Cycle | ADD | SUB         | AND         |
| ----: | --- | ----------- | ----------- |
|     1 | IF  |             |             |
|     2 | ID  | IF          |             |
|     3 | EX  | ID          | IF          |
|     4 | MEM | EX ← fwd x5 | ID          |
|     5 | WB  | MEM         | EX ← fwd x6 |
|     6 |     | WB          | MEM         |
|     7 |     |             | WB          |
```
ADD    IF    ID    EX    MEM   WB
_Sends ex-result to the next ex_
SUB          IF    ID    EX    MEM   WB

AND                IF    ID    EX    MEM    WB
```
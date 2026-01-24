[[Conditional statements]]
[[Function Calls]]

# Exam Example

[slides with good solution](obsidian://open?vault=compSys-e2025&file=material%2FTA-Recap_sessions%2FAssembler-Programming.pdf)

![[Pasted image 20260120180236.png]]

## 1.3.1
*The code snippet is a function. Is this function calling other functions? Argue for your answer*

There is no jump instruction. Therefore it is not calling any functions.

## 1.3.2
*Which registers hold the functions arguments (if any)? Argue for your answer*

We're looking for registers that are written to before they're accessed. Here, it is a0. But it may be more in other cases.

## 1.3.3
*The function contains a loop. Which instructions form the loop? Describe how you identified this.*

On line 5 theres an option to skip L3 if a5 is zero. .L3 is the loop body that is executed repeadetly if a5 is not zero. The BNE instruction on line 10 forms the loop logic.

We can see a do-while loop here:
![[Conditional statements#Do-While Loop]]
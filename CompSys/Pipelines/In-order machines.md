# 


## Example 1

Prerequisites:
- In-order machine
- 5 stage
- [[Forwarding|full forwarding]] (we don't wait for writeback (`Wb`) to use the value from an execute step `Ex`)

![[Pasted image 20260118211046.png]]

> See that line 6 is offset by 1
> This is because of [[Forwarding|full forwarding]] where the result from `Ex` is bypassed

## Example 2

![[Pasted image 20260120202024.png]]

Line 2 staggers on **De**  because loading gives the value after **Me**-stage
	**Fe** from the next operation has already been started:
Line 3 has 2 **Fe** since there can only be one at a time
Line 4 waits until **Fe** is free
Line 6 staggers on **De** since load byte gives value at **Me**

Line 7 only comes after **Wb** because **Me** resolves the correct instruction address
Line 7 is a load instruction, therefore the next must stagger (it needs value) at **De**
Line 8 must then stagger at **Fe**
Line 9 must wait to begin
Line 10 is a load instruction, therefore:
Line 11 must wait for load byte at **De** stage
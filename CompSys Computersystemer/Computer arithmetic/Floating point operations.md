General idea:
1. First calculate the exact result.
2. Then round to the desired result.

## Rounding

![[Pasted image 20250907140856.png]]

### Rounding binary
![[Pasted image 20250907141328.png]]

## Multiplication

$$
((-1)^{S_{3}} \cdot M_{3} \cdot 2^{E_{3}}) = 
((-1)^{S_{1}} \cdot M_{1} \cdot 2^{E_{1}}) \cdot
((-1)^{S_{2}} \cdot M_{2} \cdot 2^{E_{2}})
$$
Where the exact result is:
$$
\begin{align}
S_{3} &= S_{1} \text{ xor } S_{2} &(\text{sign})\\
M_{3} &= M_{1} \cdot M_{2} & (\text{significant}) \\
E_{3} &= E_{1} + E_{2} & (\text{exponent})
\end{align}
$$
![[Pasted image 20250907141923.png]]

## Addition

![[Pasted image 20250907142025.png]]
![[Pasted image 20250907142052.png]]
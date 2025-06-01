# Hamming code

## Problemet

En afsender sender en 4-bit databesked $d = (d_1, d_2, d_3, d_4)$, hvor $d_i ∈ \Bbb{F}_2$, til en modtager.
Beskeden går via en kanal med moderat støj: den modtagne besked $r = (r_1, r_2, r_3, r_4)$ afviger højst én bit fra den afsendte besked.

![[Pasted image 20250429213540.png]]

**Vi vil finde (og rette) den fejlbehæftede bit!**

### Eksempel

Hvis $r = (1, 0, 0, 1)$ er modtaget, så må den afsendte besked have været en blandt følgende: 
$$
d = (1, 0, 0, 1), (0, 0, 0, 1), (1, 1, 0, 1), (1, 0, 1, 1), (1, 0, 0, 0)
$$
## Kodningsmatrix
I stedet for 4 bit $d = (d_1, d_2, d_3, d_4)$ sendes 7 bit:
$$
d = 
(\tilde{d}_1, \tilde{d}_2, \tilde{d}_3, \tilde{d}_4, \tilde{d}_5, \tilde{d}_6, \tilde{d}_7)
:= 
(
\textcolor{green}{p_1},
\textcolor{green}{p_2},
d_1, 
\textcolor{green}{p_3},
d_2, 
d_3, 
d_4
)
$$
De ekstra bit $p_1, p_2, p_3$ kaldes **paritetsbit** og er givet ved
$$
\begin{matrix}
p_{1} = d_{1} + d_{2} + d_{4}\\
p_{2} = d_{1} + d_{3} + d_{4}\\
p_{3} = d_{2} + d_{3} + d_{4}\\
\end{matrix}
$$
Forbindelsen mellem $d$ og $\tilde{d}$ beskrives ved kodningsmatricen $G$
![[Pasted image 20250429214534.png]]

## Afkodningsmatrix

Definition af afkodningsmatrix:
$$
H = \begin{bmatrix}
1 & 0 & 1 & 0 & 1 & 0 & 1 \\
0 & 1 & 1 & 0 & 0 & 1 & 1 \\
0 & 0 & 0 & 1 & 1 & 1 & 1
\end{bmatrix}
$$
Den $i$’te søjle giver tallet $i$ i det bineære talsystem:
![[Pasted image 20250429214750.png]]

---
tags:
  - Assignment
---
# Project B

## Opgave 1
Betragt for hvert $a ∈ \mathbb{R}$ den lineære transformation $T_{a} : \mathbb{R}^3→ \mathbb{R}^3$ givet ved
$$
T_{a}\begin{pmatrix}
x_{1} \\
x_{2} \\
x_{3}
\end{pmatrix}
=
\begin{pmatrix}
ax_{1}-x_{2}-x_{3} \\
(a-1)x_{2}-x_{3} \\
2x_{2}+(a+2)x_{3}
\end{pmatrix}
$$
### (a)
Bestem den matrix $M_a$ som opfylder $T_a(x) = \mathbf{M}_a\mathbf{x}$ for alle $\mathbf{x} ∈ \mathbb{R}^3$

[[Lineære transformationer]]

$T_{a}$ er altså den lineære transformation som behandler de tre koordinater.
Denne ganges på matricen $M_{a}$ for at transformere et input.

Vi har altså slutresultatet i eksemplet herunder:
$M_{a}$ er altså en 3x3 matrix:
$$
T_{a}
\begin{pmatrix}
x_{1} \\
x_{2} \\
x_{3}
\end{pmatrix}
=
\begin{pmatrix}
a & -1 & -1 \\
0 & a-1 & -1 \\
0 & 2 & (a+2)
\end{pmatrix}
\begin{pmatrix}
x_{1} \\
x_{2} \\
x_{3}
\end{pmatrix}
=
\begin{pmatrix}
ax_{1}-x_{2}-x_{3} \\
(a-1)x_{2}-x_{3} \\
2x_{2}+(a+2)x_{3}
\end{pmatrix}
$$

$$
M_{a}=
\begin{pmatrix}
a & -1 & -1 \\
0 & a-1 & -1 \\
0 & 2 & (a+2)
\end{pmatrix}
$$

![[Lineære transformationer#1]]
### (b)
Lad $a\not\in \set{−1,0}$ være vilkårlig. Vis, at $T_a$ er bijektiv og bestem den inverse $T^{−1}_a$ .

[[Injektivitet og surjektivitet]]

Vi starter med at vise, at den er injektiv.
$\text{ker T} = \set{\mathbf{0}}$
Vi ser altså nulrummet af A, da $\text{ker T = null A}$
$$\text{null A} =\text{null }
\begin{pmatrix}
a & -1 & -1 \\
0 & a-1 & -1 \\
0 & 2 & (a+2)
\end{pmatrix}$$

Vi lader a være vilkårlig og sætter $a=1$
$$
\left[\begin{array}{rrr|rrr}
1 & -1 & -1  & 0\\
0 & 0 & -1  & 0\\
0 & 2 & 3 & 0
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
r_{3}\leftrightarrow r_{2} \\
\frac{1}{2}r_{2}\to r_{2} \\
r_{1}+r_{2}\to r_{1} \\
-r_{3}\to r_{3}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 0 & \frac{1}{2}  & 0\\
0 & 1 & \frac{3}{2}  & 0\\
0 & 0 & 1 & 0
\end{array}\right]
$$
$$
\left[\begin{array}{rrr|rrr}
1 & 0 & \frac{1}{2}  & 0\\
0 & 1 & \frac{3}{2}  & 0\\
0 & 0 & 1 & 0
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-\frac{1}{2}r_{3}+r_{1} \to r_{1}\\
-\frac{3}{2}r_{3}+r_{1} \to r_{2}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 0 & 0  & 0\\
0 & 1 & 0  & 0\\
0 & 0 & 1 & 0
\end{array}\right]
$$
Vi får altså, at $\text{ker T} =\text{null A}=\set{0}$
Den er derfor injektiv.

Så viser vi, at den er surjektiv ved at vise $\text{ran T} =\text{col A}=\mathbb{R}^3$
Vi kan se at 
$$\text{col A}=\text{span }\set{
\begin{pmatrix}
1 \\
0 \\
0
\end{pmatrix}
\begin{pmatrix}
0 \\
1 \\
0
\end{pmatrix}
\begin{pmatrix}
0 \\
0 \\
1
\end{pmatrix}
}\in \mathbb{R}^3$$
T er altså bijektiv

**Inverse: stiller med inverse på højre side, og gør compute til at få inverse**

Vi fortsætter med a=1 og benytter compute til at udregne den inverse matrix:

$$
\left[\begin{array}{rrr|rrr}
1 & -1 & -1  & 1 & 0 & 0\\
0 & 0 & -1  & 0 & 1 & 0\\
0 & 2 & 3 & 0 & 0 & 1
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
r_{2}\leftrightarrow r_{3} \\
\frac{1}{2}r_{2}\to r_{2} \\
r_{2}+r_{1}\to r_{1} \\
-r_{3}\to r_{3}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 0 & \frac{1}{2}  & 1 & 0 & \frac{1}{2}\\
0 & 1 & \frac{3}{2}  & 0 & 0 & \frac{1}{2}\\
0 & 0 & 1 & 0 & -1 & 0
\end{array}\right]
$$
$$
\left[\begin{array}{rrr|rrr}
1 & 0 & \frac{1}{2}  & 1 & 0 & \frac{1}{2}\\
0 & 1 & \frac{3}{2}  & 0 & 0 & \frac{1}{2}\\
0 & 0 & 1 & 0 & -1 & 0
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-\frac{1}{2}r_{3}\to r_{1} \\
-\frac{3}{2}r_{3}\to r_{2}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 0 & 0  & 1 & \frac{1}{2} & \frac{1}{2}\\
0 & 1 & 0  & 0 & \frac{3}{2} & \frac{1}{2}\\
0 & 0 & 1 & 0 & -1 & 0
\end{array}\right]
$$
Vi får altså den inverse matrix:
$$
\left[\begin{array}{rrr}
 1 & \frac{1}{2} & \frac{1}{2}\\
 0 & \frac{3}{2} & \frac{1}{2}\\
0 & -1 & 0
\end{array}\right]
$$

[[Nulrum]]
### (c)
[[Underrum]]
[[Dimensioner]]
billede + kerne

For $a=0$ og $a=-1$
Kernen er nulrummet af A
Billedet er søjlerummet af A

Derefter dimensioner

Nulrummet for $A$ når $a = -1$
$$
\left[\begin{array}{rrr|r}
-1 & -1 & -1 \\
0 & -2 & -1 \\
0 & 2 & 1
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-1r_{1}\to r_{1} \\
-\frac{1}{2}r_{2}\to r_{2} \\
r_{1}-r_{2}\to r_{1} \\
r_{3}-2r_{2}\to r_{3}
\end{matrix}
}
\left[\begin{array}{rrr|r}
1 & 0 & \frac{1}{2} \\
0 & 1 & \frac{1}{2} \\
0 & 0 & 0
\end{array}\right]
$$
Nulrummet bliver derfor til


$\begin{pmatrix}-\frac{1}{2}\\-\frac{1}{2}\\1 \end{pmatrix}$

Søjlerummet er pr. definition givet ved:
$$
\text{col A} =
\text{span}
\set{
\begin{pmatrix}
-1 \\
0 \\
0
\end{pmatrix}
\begin{pmatrix}
-1 \\
-2 \\
2
\end{pmatrix}
\begin{pmatrix}
-1 \\
-1 \\
1
\end{pmatrix}
}
$$
Så vi skal finde dimensionen af

$$
\set{
\begin{pmatrix}-\frac{1}{2}\\-\frac{1}{2}\\1 \end{pmatrix}
}
\text{ og }
\set{
\begin{pmatrix}
-1 \\
0 \\
0
\end{pmatrix}
\begin{pmatrix}
-1 \\
-2 \\
2
\end{pmatrix}
\begin{pmatrix}
-1 \\
-1 \\
1
\end{pmatrix}
}
$$
Vi skal undersøge om de faktisk *er* en basis
De er hhv. 1 og 3, da dimensionen er givet ved antallet af vektorer i en basis.

$$
\left[\begin{array}{rrr|r}
0&-1&-1 \\
0&-1&-1 \\
0&2&2
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-r_1\to r_1 \\
r_2-r_1\to r_2 \\
r_3+2r_1\to r_3
\end{matrix}
}
\left[\begin{array}{rrr|r}
0  & 1 & 1 \\
0 & 0 & 0 \\
0 & 0 & 0
\end{array}\right]
$$
### (d)
Vi opskriver først matricerne hvor $a=-1, a= 0$
$$
M_{a}=
\begin{pmatrix}
a & -1 & -1 \\
0 & a-1 & -1 \\
0 & 2 & (a+2)
\end{pmatrix}
$$
#### for $a=-1$
$$
M= 
\begin{pmatrix}
-1 & -1 & -1 \\
0 & -2 & -1 \\
0 & 2 & 1
\end{pmatrix}
$$
Vi antager at følgende udtryk holder for k=1, 2:
$$
M^k=
\begin{pmatrix}
(-1)^k & (-1)^k & (-1)^k \\
0 & 2(-1)^k & (-1)^k \\
0 & 2(-1)^k & -(-1)^k
\end{pmatrix}
$$Induktionsskridt, vi viser for k+1:
$$
M^{k+1}= 
\begin{pmatrix}
-1 & -1 & -1 \\
0 & -2 & -1 \\
0 & 2 & 1
\end{pmatrix}
\begin{pmatrix}
(-1)^k & (-1)^k & (-1)^k \\
0 & 2(-1)^k & (-1)^k \\
0 & 2(-1)^k & -(-1)^k
\end{pmatrix}
$$
$$
M^{k+1}=
\begin{pmatrix}
-(-1)^k & -(-1)^k & -(-1)^k \\
0 & -2(-1)^k & -(-1)^k \\
0 & 2(-1)^k & (-1)^k
\end{pmatrix}
$$
Fordi at alle tal ganges med $(-1)^k$ kan vi omvende alle fortegn således: $-a(-1)^k=a(-1)^{k+1}$
Derfor får vi altså:
$$
M^{k+1}=
\begin{pmatrix}
(-1)^{k+1} & (-1)^{k+1} & (-1)^{k+1} \\
0 & 2(-1)^{k+1} & (-1)^{k+1} \\
0 & -2(-1)^{k+1} & -(-1)^{k+1}
\end{pmatrix}
$$
Udtrykket holder derfor for k+1
#### For a = 0
for $a=0$
$$
M= 
\begin{pmatrix}
0 & -1 & -1 \\
0 & -1 & -1 \\
0 & 2 & 2
\end{pmatrix}
$$
Når vi ganger denne matrice med sig selv opstår der det, at den bliver sig selv $A^1=A$
Vi prøver derfor udtrykket som vi antager holder:
$$
\begin{pmatrix}
0 & -1 & -1 \\
0 & -1 & -1 \\
0 & 2 & 2
\end{pmatrix}^k
=
\begin{pmatrix}
0 & -1 & -1 \\
0 & -1 & -1 \\
0 & 2 & 2
\end{pmatrix}
$$
Vi prøver derefter
### (e)
$\mathcal{L}$
Vi kan starte med at skrive linjen op:
$$
M_{a}=
\left[
\begin{array}{ccc|c}
a & -1 & -1  & t\\
0 & a-1 & -1 & t \\
0 & 2 & (a+2) & -2t
\end{array}
\right]
$$
Vi kan gange vektoren på transformationen.
Så skal vi vise at matricen ligger i spannet af linjen.
Eller så har jeg har fundet et x, så man kan skrive $T_a(t, t, -2t)$, op på formen $(xt,xt,-2xt)$
se [[Underrum]]
## Opgave 2

Betragt følgende vektorer i $\mathbb{R}^4$
![[Pasted image 20250513224944.png]]

### (a)
Bestem basisskiftmatricen $\mathbf{P}_{\mathcal{B}\gets\mathcal{C}}$
[[Baser]]
[[Underrum]]

Vi bestemmer koordinater for $\mathcal{C}$ iht. $\mathcal{B}$ 
$\mathbf{P}_{\mathcal{B}\gets\mathcal{C}}=([\mathbf{C_{1}}]_{\mathcal{B}} \mid \dots \mid[\mathbf{C_{k}}]_{\mathcal{B}} )$

Vi regner altså $[\mathbf{C_{1}}]_{\mathcal{B}},[\mathbf{C_{2}}]_{\mathcal{B}}, [\mathbf{C_{3}}]_{\mathcal{B}}$

$$
\begin{matrix}
[\mathbf{C_{1}}]_{\mathcal{B}}=x_{1}\mathbf{b}_{1}+x_{2}\mathbf{b}_{2}+x_{3}\mathbf{b}_{3} \\
=
7
\begin{pmatrix}
2 \\
1 \\
-1 \\
1
\end{pmatrix}
-2
\begin{pmatrix}
0 \\
1 \\
-1 \\
1
\end{pmatrix}
+3
\begin{pmatrix}
1 \\
-1 \\
2 \\
2
\end{pmatrix}
\end{matrix}
$$
Se Maple (forkert)

Vi stiller alle vektorerne op i en totalmatrix: $\mathbf{P}_{\mathcal{B}\gets\mathcal{C}}=(\mathbf{u}_{1},\dots, \mathbf{u}_{3}\mid\mathbf{v}_{1},\dots,\mathbf{v}_{3})$
Vi får så en rækkereduceret matrix med en nulrække nederst. Den højre matrix er således vores basisskiftmatrice.
$$
\left[\begin{array}{rrr|rrr}
2 & 0 & 1 & 7 & -1 & 3\\
1 & 1 & -1 & -2 & 0 & -1\\
-1 & -1 & 2 & 3 & -1 & 2 \\
1 & 1 & 2 & 1 & -3 & 2
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
r_{1}\leftrightarrow r_{2} \\
-2r_{1}\to r_{1} \\
r_{1}+r_{2}\to r_{2} \\
r_{1}-r_{3}\to r_{3} \\
-\frac{1}{2}r_{2}\to r_{2} \\
r_{1}-r_{2}\to r_{2}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 0 & \frac{1}{2} & \frac{7}{2} & -\frac{1}{2} & \frac{3}{2}\\
0 & 1 & -\frac{3}{2} & -\frac{11}{2} & \frac{1}{2} & -\frac{5}{2}\\
0 & 0 & 1 & 1 & -1 & 1 \\
0 & 0 & 3 & 3 & -3 & 3
\end{array}\right]
$$
$$
\left[\begin{array}{rrr|rrr}
1 & 0 & \frac{1}{2} & \frac{7}{2} & -\frac{1}{2} & \frac{3}{2}\\
0 & 1 & -\frac{3}{2} & -\frac{11}{2} & \frac{1}{2} & -\frac{5}{2}\\
0 & 0 & 1 & 1 & -1 & 1 \\
0 & 0 & 3 & 3 & -3 & 3
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-\frac{1}{2}r_{3}\to r_{1} \\
\frac{3}{2}r_{3}\to r_{2} \\
-3r_{3}\to r_{4}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 0 & 0 & 3 & 0 & 1\\
0 & 1 & 0 & -4 & -1 & -1\\
0 & 0 & 1 & 1 & -1 & 1 \\
0 & 0 & 0 & 0 & 0 & 0
\end{array}\right]
$$

Vi får altså basisskiftmatricen:
$$
\mathbf{P}_{\mathcal{B}\gets\mathcal{C}}=
\left[\begin{array}{ccc}
3 & 0 & 1 \\
-4 & -1 & -1 \\
1 & -1 & 1  \\
0 & 0 & 0
\end{array} 
\right]
$$

### (b)
Bestem koordinaterne for vektoren $x = v_1 +v_2 +v_3$ mht. basen $\mathcal{B}$ og mht. basen $\mathcal{C}$.
Vi finder så først vektoren:

$$
x
=
\begin{pmatrix}
7 \\
-2 \\
3 \\
1
\end{pmatrix}
+
\begin{pmatrix}
-1 \\
0 \\
-1 \\
-3
\end{pmatrix}
+
\begin{pmatrix}
3 \\
-1 \\
2 \\
2
\end{pmatrix}
=
\begin{pmatrix}
9 \\
-3 \\
4 \\
0
\end{pmatrix}
$$
Vi har allerede givet linearkombinationen $x = v_{1}+v_{2}+v_{3}$ koefficienterne er alle 1, og derfor skriver vi x's koordinater iht. C som $\begin{pmatrix}1 \\ 1 \\ 1\end{pmatrix}$
For at finde x's koordinater må vi finde linearkombinationen a vektorerne sådan at $au_{1}+a_{2}u_{2}+a_{3}u_{3}=x$
$$
\mathbf{x}=
a_{1}
\begin{pmatrix}
2 \\
1 \\
-1 \\
1
\end{pmatrix}
+a_{2}
\begin{pmatrix}
0 \\
1 \\
-1 \\
1
\end{pmatrix}
+a_{3}
\begin{pmatrix}
1 \\
-1 \\
2 \\
2
\end{pmatrix}
=
\begin{pmatrix}
9 \\
-3 \\
4 \\
0
\end{pmatrix}
$$
Det kan vi udtrykke som en totalmatrix:

$$
\left[\begin{array}{rrr|r}
2 & 0 & 1 & 9 \\
1 & 1 & -1 & -3 \\
-1 & -1 & 2 & 4 \\
1 & 1 & 2 & 0
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
r_{1}\leftrightarrow r_{2} \\
-2r_{1}\to r_{2} \\
r_{3}+r_{1}\to r_{3} \\
r_{4}-r_{1}\to r_{4} \\
-\frac{1}{2}r_{2}\to r_{2} \\
-r_{2}+r_{1}\to r_{1}
\end{matrix}
}
\left[\begin{array}{rrr|r}
1 & 0 & \frac{1}{2} & \frac{9}{2} \\
0 & 1 & -\frac{3}{2} & -\frac{15}{2} \\
0 & 0 & 1 & 1 \\
0 & 0 & 3 & 3
\end{array}\right]
$$
$$
\left[\begin{array}{rrr|r}
1 & 0 & \frac{1}{2} & \frac{9}{2} \\
0 & 1 & -\frac{3}{2} & -\frac{15}{2} \\
0 & 0 & 1 & 1 \\
0 & 0 & 3 & 3
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-\frac{1}{2}r_{3}+r_{1}\to r_{1} \\
\frac{3}{2}r_{3}+r_{2}\to r_{2} \\
-r_{3}\to r_{4}
\end{matrix}
}
\left[\begin{array}{rrr|r}
1 & 0 & 0 & 4 \\
0 & 1 & 0 & -6 \\
0 & 0 & 1 & 1 \\
0 & 0 & 0 & 0
\end{array}\right]
$$

Vi får altså koordinaterne mht. basen B til at være:
$$
\begin{pmatrix}
4 \\
-6 \\
1 \\
0
\end{pmatrix}
$$
[[Koordinater]]
[[Baser]]
### (c)
Gør rede for, at $v_2$ tilhører $\text{span}\set{u_2,u_3}$

Vi skal kunne udspænde u2 og 3 sådan at de giver v2
Vi skriver det om som en totalmatrix
$$
\left[ \begin{array}{cc|c}
0 & 1 & -1 \\
1 & -1 & 0 \\
-1 & 2 & -1 \\
1 & 2 & -3
\end{array} \right] 
$$
Vi laver gauss jordan
$$
\left[\begin{array}{rr|r}
0 & 1 & -1 \\
1 & -1 & 0 \\
-1 & 2 & 1 \\
1 & 2 & -3
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
r_{2}\leftrightarrow r_{1} \\
r_{3}+r_{1}\to r_{3} \\
-r_{1}+r_{4}\to r_{4} \\
r_{1}+r_{2}\to r_{1} \\
r_{3}-r_{2}\to r_{3} \\
-3r_{2}\to r_{4}
\end{matrix}
}
\left[\begin{array}{rr|r}
1 & 0 & -1 \\
0 & 1 & -1 \\
0 & 0 & 0 \\
0 & 0 & 0
\end{array}\right]
$$
Vi får altså at $-u_{2}-u_{3}=v_{2}$

Gør rede for, at $v_1$ hverken tilhører $\text{span}\set{u_1,u_2}$, $\text{span}\set{u_1,u_3}$ eller $\text{span}\set{u_2,u_3}$.

Vi skriver op på totalmatrixform span u1,u2:
$$
\left[ \begin{array}{cc|c}
2 & 1 & 7 \\
1 & -1 & -2 \\
-1 & 2 & 3 \\
1 & 2 & 1
\end{array} \right] 
$$
Vi laver Gauss-Jordan for at finde mængden af løsninger

$$
\left[\begin{array}{rr|r}
2 & 1 & 7 \\
1 & -1 & -2 \\
-1 & 2 & 3 \\
1 & 2 & 1
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
r_{1} \leftrightarrow r_{2} \\
-2r_{1}+r_{2}\to r_{2} \\
r_{1}+r_{3}\to r_{3} \\
r_{1}-r_{4}\to r_{4} \\
r_{3}\leftrightarrow r_{2} \\
r_{1}+r_{2}\to r_{1} \\
-3r_{2}+r_{3}\to r_{3} \\
-3r_{2}+r_{4}\to r_{4}
\end{matrix}
}
\left[\begin{array}{rr|r}
1 & 0 & -1 \\
0 & 1 & 1 \\
0 & 0 & 8 \\
0 & 0 & 0
\end{array}\right]
$$
$$
\left[\begin{array}{rr|r}
1 & 0 & -1 \\
0 & 1 & 1 \\
0 & 0 & 8 \\
0 & 0 & 0
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
\frac{1}{8}r_{3}\to r_{3} \\
r_{1}+r_{3}\to r_{1} \\
r_{2}-r_{3}\to r_{2}
\end{matrix}
}
\left[\begin{array}{rr|r}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
0 & 0 & 0
\end{array}\right]
$$

Her er der nul løsninger til systemet, v1 ligger altså ikke i spannet af u1 og u2.
### (d)
Bestem for ethvert $x ∈ \mathbb{R}$ dimensionen af underrummet $\mathcal{V}_x = \text{span}\set{xu_1 +u_2, u_{1} + xu_{2}}$

Vi skal først undersøge om der er tale om en base. Antallet af basevektorer afgør dimensionen af underrummet. Vi undersøger om vektorerne er lineært uafhængige. 
$$
xu_{1}+u_{2}=u_{1}+xu_{2}
$$
Vi antager at der er en lineær afhængighed $a$ som opfylder
$$
\begin{matrix}
a(xu_{1}+u_{2})=u_{1}+xu_{2} \\
\implies axu_{1}+au_{2}=u_{1}+xu_{2}
\end{matrix}
$$
Vi kan se, at for at ligningen holder må $a=1$, da $ax=1$, må nødvendigvis $a=x$. Altså, $x^2\implies x\pm1$.
Ligningen holder altså kun for $x=1$, for alle andre værdier af $x$ holder den ikke. Altså $\text{dim }\mathcal{V}_{x}=1$ for $a \in \mathbb{R} \backslash \set{1}$, hvor $\text{dim }\mathcal{V}_{x}=2$ for $a=1$.

[[Dimensioner]]
[[Underrum]]
[[Span]]

### (e)

![[Pasted image 20250513225537.png]]
Vi betragter $x_{3}x_{4}$-planen i $\mathbb{R}^4$, dvs. underrummet $\mathcal{W}=\set{(0,0,x_{3},x_{4})\in \mathbb{R}^4\mid x_{3},x_{4}\in \mathbb{R}}$
$\mathcal{U}$ er underrummet $\mathcal{U}\in \mathbb{R}^4$
Vis, at fællesmængden $\mathcal{U}∩\mathcal{W}$ er en linje gennem orego og bestem en retningsvektor for denne

Vi kan skrive underrummet op som en linearkombination af basen, f.eks. base 
$$
x_{1}u_{1}+x_{2}u_{2}+x_{3}u_{3}=
x_{1}
\begin{pmatrix}
2 \\
1 \\
-1 \\
1
\end{pmatrix}
+x_{2}
\begin{pmatrix}
0 \\
1 \\
-1 \\
1
\end{pmatrix}
+x_{3}
\begin{pmatrix}
1 \\
-1 \\
2 \\
2
\end{pmatrix}
$$
Vi skal altså have en vektor sådan at:
$p=\begin{pmatrix}0 \\ 0 \\ p_{3} \\ p_{4}\end{pmatrix}$, for $p_{3},p_{4}\in \mathbb{R}$. Dvs. at de to første værdier i matricen skal give nul.
Vi stiller ligningssystemet op:
$$ 
\begin{align}
   2x_{1}+x_{3}&=0 \\
   x_{1}+x_{2}-x_{3}&=0
\end{align}
\implies
\begin{matrix}
x_{3}=-2x_{1} \\
3x_{1}+x_{2}=0
\end{matrix}
\implies
\begin{matrix}
x_{3}=-2x_{1} \\
x_{2}=-3x_{1}
\end{matrix}
$$
Ved at sætte $x_{2},x_{3}$ til en parameter $t$ kan vi udtrykke hele linearkombinationen:
$$
\begin{matrix}
t
\begin{pmatrix}
2 \\
1 \\
-1 \\
1 \\
\end{pmatrix}
+(-3t)
\begin{pmatrix}
0 \\
1 \\
-1 \\
1
\end{pmatrix}
+(-2t)
\begin{pmatrix}
1 \\
-1 \\
2 \\
2
\end{pmatrix} \\
=t
\begin{pmatrix}
2 \\
1 \\
-1 \\
1 \\
\end{pmatrix}
+t
\begin{pmatrix}
0 \\
-3 \\
3 \\
-3
\end{pmatrix}
+t
\begin{pmatrix}
-2 \\
2 \\
-4 \\
-4
\end{pmatrix} \\
=t
\begin{pmatrix}
0 \\
0 \\
-2 \\
-6
\end{pmatrix}
\end{matrix}
$$
Vi kan altså udtrykke fællesmængden som en linje. Reducerer vi denne, får vi retningsvektoren:
$$
\begin{pmatrix}
0 \\
0 \\
1 \\
3
\end{pmatrix}
$$
## Opgave 3

![[Pasted image 20250513225729.png]]
![[Pasted image 20250513225757.png]]
### (a)
Bestem en $4×4$ matrix $\mathbf{F}$ som opfylder
$$a
\begin{pmatrix}
c_{1}^F \\
c_{2}^F \\
s_{1}^F \\
s_{2}^F
\end{pmatrix}
=
\mathbf{F}
\begin{pmatrix}
c_{1} \\
c_{2} \\
s_{1} \\
s_{2}
\end{pmatrix}
$$
![[Pasted image 20250513225936.png]]

Vi ser at vektoren parallelforskydes med $\vec{CS}$, som vi udtrykker i et ligningssystem:
$$
\begin{matrix}
c_{1}+(s_{1}-c_{1}) = c^F_{1} \\
c_{2}+(s_{2}-c_{2}) = c^F_{2} \\
s_{1}+(s_{1}-c_{1}) = s^F_{1} \\
s_{2}+(s_{2}-c_{2}) = s^F_{2}
\end{matrix}
\to
\begin{matrix}
s_{1} = c^F_{1} \\
s_{2} = c^F_{2} \\
2s_{1}-c_{1} = s^F_{1} \\
2s_{2}-c_{2} = s^F_{2}
\end{matrix}
$$
Dette kan vi udtrykke som matricen:
$$
F=
\begin{bmatrix}
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
-1 & 0 & 2 & 0 \\
0 & -1 & 0 & 2
\end{bmatrix}
$$
### b)
Vi kan hurtigt afklare at $c^L_{1},c^L_{2}$ kan udtrykkes som 
$$
\begin{matrix}
c^L_{1} =c_{1}\\
c^L_{2} =c_{2}
\end{matrix}
$$
Vi opskriver resten af ligningerne:
Vi ganger først vektoren ind i matricen, og adderer derefter:
$$
\begin{matrix}
s^L_{1}= c_1 + \cos(\theta)\cdot(s_{1} - c_{1}) - \sin(\theta)\cdot(s_{2} - c_{2}) \\
s^L_{2}= c_2 + \sin(\theta)\cdot(s_{1} - c_{1}) + \cos(\theta)\cdot(s_{2} - c_{2})
\end{matrix}
$$
Således kan vi omskrive $s^L_{1},s^L_{2}$ til lineære udtryk:
$$
\begin{matrix}
s^L_{1}= c_1 + \cos(\theta)\cdot(s_{1} - c_{1}) - \sin(\theta)\cdot(s_{2} - c_{2}) \to \\
s^L_{1}= c_{1}-c_{1}\cos \theta-c_{2}\sin \theta+s_{1}\cos{\theta}-s_{2}\sin \theta 
\end{matrix}
$$
$$
\begin{matrix}
s^L_{2}= c_2 + \sin(\theta)\cdot(s_{1} - c_{1}) + \cos(\theta)\cdot(s_{2} - c_{2}) \to \\
s^L_{2}=-c_{1}\sin \theta+c_{2}-c_{2}\cos \theta+s_{1}\sin \theta+s_{2}\cos \theta
\end{matrix}
$$
Vi omskriver ligningssystemet til en matrix:
$$
L_{\theta}=
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
1-\cos \theta & \sin \theta & \cos \theta & -\sin \theta \\
-\sin \theta & 1-\cos \theta & \sin \theta & \cos \theta
\end{bmatrix}
$$
For at finde $R_{\theta}$ benytter vi $R_{\theta}=L_{-\theta}$. Derfor indsætter vi blot $-\theta$ i systemet og omskriver hvor nødvendigt:
$$
\begin{matrix}
L_{-\theta}=R_{\theta}=
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
1-\cos (-\theta) & \sin (-\theta) & \cos (-\theta) & -\sin (-\theta) \\
-\sin (-\theta) & 1-\cos (-\theta) & \sin (-\theta) & \cos (-\theta)
\end{bmatrix}\\
=\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
1-\cos \theta & -\sin \theta & \cos \theta & \sin \theta \\
\sin \theta & 1-\cos \theta & -\sin \theta & \cos \theta
\end{bmatrix}
\end{matrix}
$$
### c)
Vi har de tre matricer

$$
\begin{matrix}
L_{\theta}=
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
1-\cos \theta & \sin \theta & \cos \theta & -\sin \theta \\
-\sin \theta & 1-\cos \theta & \sin \theta & \cos \theta
\end{bmatrix} \\
R_{\theta}=\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
1-\cos \theta & -\sin \theta & \cos \theta & \sin \theta \\
\sin \theta & 1-\cos \theta & -\sin \theta & \cos \theta
\end{bmatrix} \\
F=
\begin{bmatrix}
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
-1 & 0 & 2 & 0 \\
0 & -1 & 0 & 2
\end{bmatrix}
\end{matrix}
$$

disse ganger vi på en for en.
Når vi sammensætter lineære transformationer gør vi det som at gange matricer. Sammensætningen af lineære transformationer er givet ved: $S(T(\mathbf{x}))=(\mathbf{BA})\mathbf{x}$ for $T(\mathbf{x)=}\mathbf{Ax}$ og $S(\mathbf{y})=\mathbf{By}$
Derfor kan vi skrive rækkefølgen op:
$$
FLLLFFRRF
$$
Alle matricer er kvadratiske, så vi reducerer udtrykket: $FL^3F^2R^2F$
Vi ganger selvfølgelig rumskibets startkoordinater på udtrykket, sådan at resultatet bliver rumskibets rotation og position. Resultatet bliver efter udregning:
$$
\begin{bmatrix}
~2.17~ \\
~3.64~ \\
~1.36~ \\
~1.28~
\end{bmatrix}
$$
### d)

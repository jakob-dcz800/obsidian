---
tags:
  - Assignment
---
# 1

## a
$$
\begin{align}
ax_{1}+x_{2}+2ax_{3} & =1 \\
4x_{1}+ax_{2}+12x_{3} & =-a
\end{align}
$$
Når $a=2$
$$
\left[
\begin{array}{ccc|c}
2 &  1 & 4 & 1 \\
4 & 2 & 12 & -2 \\
\end{array}
\right]
\xrightarrow[]{
\begin{matrix}
2r_{1}-r_{2}\to r_{2}
\end{matrix}
}
\left[
\begin{array}{ccc|c}
2 &  1 & 4 & 1 \\
0 & 0 & 4 & -4 \\
\end{array}
\right]
$$
$$
\left[
\begin{array}{ccc|c}
2 &  1 & 4 & 1 \\
0 & 0 & 4 & -4 \\
\end{array}
\right]
\xrightarrow[]{
\begin{matrix} \\
r_{2}-r_{1}\to r_{1}
\end{matrix}
}
\left[
\begin{array}{ccc|c}
2 &  1 & 0 & 5 \\
0 & 0 & 4 & -4 \\
\end{array}
\right]
$$

$$
\left[
\begin{array}{ccc|c}
2 &  1 & 0 & 5 \\
0 & 0 & 4 & -4 \\
\end{array}
\right]
\xrightarrow[]{
\begin{matrix}
\end{matrix}
}
\left[
\begin{array}{ccc|c}
1 &  1/2 & 0 & 5/2 \\
0 & 0 & 1 & -1 \\
\end{array}
\right]
$$
$$
\begin{align}
x_{1} & = 5/2-1/2t\\
x_{2} & = t\\
x_{3} & = -1
\end{align}
$$
$$
\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3}
\end{bmatrix}
=
\begin{bmatrix}
5/2-1/2t \\
t \\
-1
\end{bmatrix}
$$
## b

$$
\left[
\begin{array}{ccc|c}
a &  1 & 2a & 1 \\
4 & a & 12 & -a \\
\end{array}
\right]
$$
1. få ligningen på [[Rækkeechelonform|echelonform]]
2. vis at [[Rang af matricer|rangen]] altid er mindre end antal kolonner

$$
\left[
\begin{array}{ccc|c}
a &  1 & 2a & 1 \\
4 & a & 12 & -a \\
\end{array}
\right]
\xrightarrow[]{
\begin{matrix}
r_{1}\leftrightarrow r_{2} \\
-a/4r_{1}\to r_{2}
\end{matrix}
}
\left[
\begin{array}{ccc|c}
4 & a & 12 & -a \\
0 &  1-\left( \frac{a^2}{4} \right) & -a & 1+\left( \frac{a^2}{4} \right) \\
\end{array}
\right]
$$
Da 1-(a^2/4) og -a aldrig kan være lig nul på samme tid er rangen af matricen 2
Da rangen er mindre end antallet af søjler vil der altid være uendeligt mange løsninger
Thm. 1.3

## c

$$
\left[
\begin{array}{ccc|c}
0 &  1 & 0 & 1 \\
4 & 0 & 12 & 0 \\
\end{array}
\right]
$$
Bestem den højreinverse a matricen
$$
AX=I_{m}
$$
$$
\left[
\begin{array}{ccc|c}
0 &  1 & 0 \\
4 & 0 & 12 \\
\end{array}
\right]
\begin{bmatrix}
x_{1} & x_{2} \\
x_{3} & x_{4} \\
x_{5} & x_{6}
\end{bmatrix}
=
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$
Skriv det op som ligninger

$$
\begin{align}
1 & = x_{3} \\
0 & = x_{4} \\
0 & = 4x_{1} +12x_{5} \\
1 & = 4x_{2} + 12x_{6}
\end{align}
$$
$$
\left[
\begin{array}{cccccc|c}
0 & 0 & 1 & 0 & 0 & 0 & 1 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 \\
4 & 0 & 0 & 0 & 12 & 0 & 0 \\
0 & 4 & 0 & 0 & 0 & 12 & 1 \\
\end{array}
\right]
$$
$$
\begin{align}
0  & = 4x_{1} + 12x_{5} \\
1  & = 4x_{2} + 12x_{6} \\
x_{3} & = 1 \\
x_{4} & = 0
\end{align}
$$
Vi får matricen 
$$
\begin{bmatrix}
-3t & 1/4-3s \\
1 & 0 \\
t & s
\end{bmatrix}
$$
# 2

## a

Vi udregner $(BA)x=Cx$

$$
\begin{bmatrix}
1 & -1 & -1 & 3 \\
2 & -2 & 3 & -4 \\
-1 & 1 & 0 & -1
\end{bmatrix}
\begin{bmatrix}
-1 & 1 \\
0 & 1 \\
2 & 0 \\
1 & 0
\end{bmatrix}
=
\begin{bmatrix}
0 & 0 \\
0 & 0 \\
0 & 0
\end{bmatrix}
$$
## b

Vi finder kernen af T (matrix B)
$$
\text{ker T} = \text{null B}
$$
$$
\begin{bmatrix}
1 & -1 & -1 & 3 \\
2 & -2 & 3 & -4 \\
-1 & 1 & 0 & -1
\end{bmatrix}
\begin{bmatrix}
0
\end{bmatrix}
$$
$$
\begin{bmatrix}
1 & -1 & -1 & 3 \\
2 & -2 & 3 & -4 \\
-1 & 1 & 0 & -1
\end{bmatrix}
\xrightarrow[]{
\begin{matrix}
r_{1}+r_{3}\to r_{3} \\
2r_{1}-r_{2}\to r_{2} \\
\end{matrix}
}
\begin{bmatrix}
1 & -1 & -1 & 3 \\
0 & 0 & 5 & -10 \\
0 & 0 & -1 & 2
\end{bmatrix}
$$
$$
\begin{bmatrix}
1 & -1 & -1 & 3 \\
0 & 0 & 5 & -10 \\
0 & 0 & -1 & 2
\end{bmatrix}
\xrightarrow[]{
\begin{matrix}
1/5r_{2}\to r_{2} \\
r_{2}\to r_{3} \\
r_{2}\to r_{1}
\end{matrix}
}
\begin{bmatrix}
1 & -1 & 0 & 1 \\
0 & 0 & 1 & -2 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$
2, 4 er frie variable

$$
\begin{align}
x_{1}-x_{2}+x_{4} & =0 \\
x_{3}-2x_{4} & =0
\end{align}
$$
$$
\begin{align}
x_{2} & =s \\
x_{4} & =t \\
x_{1} & =s-t \\
x_{3} & =2t
\end{align}
$$

$$
\begin{pmatrix}
x_{1} \\
x_{2} \\
x_{3} \\
x_{4}
\end{pmatrix}
=
s
\begin{pmatrix}
1 \\
1 \\
0 \\
0
\end{pmatrix}
+ t
\begin{pmatrix}
-1 \\
0 \\
2 \\
1
\end{pmatrix}
$$
x2 og x4 viser os at de to vektorer er lineært uafhængige. derfor er basen for nulrummet: 
$$
\text{ker T} =
\text{null a} = 
\text{de to vektorer}
$$
Vi finder så billedet af S (søjlerum af A)
Vi har spannet af søjlerummet:
$$
\text{col A}=
(\begin{pmatrix}
-1 \\
0 \\
2 \\
1
\end{pmatrix}
\begin{pmatrix}
1 \\
1 \\
0 \\
0
\end{pmatrix}
)
$$
Dette er det samme som kernen af T

# 3

## a

$$
M=
\begin{bmatrix}
1 & 3 & 4 \\
2 & 0 & -1 \\
-2 & 6 & 1
\end{bmatrix}
$$
$$
\begin{align}
r_{11} & =\|u_{1}\| \\
 & =\sqrt{ 1+4+4 } \\
 & =\sqrt{ 9 } \\
 & =3
\end{align}
$$
$$
q_{1}=
\frac{1}{3}u_{1}=
\begin{pmatrix}
1/3 \\
2/3 \\
-2/3
\end{pmatrix}
$$
$$
\begin{align}
r_{12} & =q_{1}\bullet u_{2} \\
 & = 1/3\cdot 3-2/3 \cdot 6 \\
 & = -3
\end{align}
$$
$$
q_{2}'=
\begin{pmatrix}
3 \\
0 \\
6
\end{pmatrix}
-(-3)
\begin{pmatrix}
1/3 \\
2/3 \\
-2/3
\end{pmatrix}
=
\begin{pmatrix}
4 \\
2 \\
-2
\end{pmatrix}
$$
$$
\begin{align}
r_{22} &  = \|q_{2}'\| \\
 & = \sqrt{ 16 } \\
 & = 4
\end{align}
$$

$$
q_{2}=\frac{1}{4}\begin{pmatrix}
4 \\
2 \\
-2
\end{pmatrix}
=
\begin{pmatrix}
1 \\
1/2 \\
-1/2
\end{pmatrix}
$$

$$
\begin{align}
r_{13}  & = q_{1} \bullet u_{3} \\
 & =1/3 \cdot 4 + 2/3 \cdot(-1) -2/3 \cdot 1 \\
 & = 4/3 -2/3-2/3 \\
 & = 0
\end{align}
$$
$$
\begin{align}
r_{23} & = q_{2} \bullet u_{3}\\
 & =4-1/2-1/2 \\
 & =3
\end{align}
$$

$$
\begin{align}
q_{3}'  & = u_{3}-0q_{1}-3q_{2} \\
 & = \begin{pmatrix}
4 \\
-1 \\
1
\end{pmatrix}
-3 \begin{pmatrix}
1 \\
1/2 \\
-1/2
\end{pmatrix} \\
& = \begin{pmatrix}
4 \\
-1 \\
1
\end{pmatrix}
-\begin{pmatrix}
3 \\
3/2 \\
-3/2
\end{pmatrix} \\
 & =
\begin{pmatrix}
1 \\
-5/2 \\
5/2
\end{pmatrix}
\end{align}
$$

$$
\begin{align}
r_{33}  & =\|q_{3}'\| \\
 & = \sqrt{ 1^2-(\frac{5}{2})^2+(\frac{5}{2})^2 } \\
 & = 1
\end{align}
$$

$$
\begin{align}
q_{3}  & = \frac{1}{1} q_{3}' \\
 & = q_{3}'
\end{align}
$$

$$
QR=
\begin{bmatrix}
1/3  & 1 & 1\\
2/3  & 1/2 & -5/2 \\
-2/3 & -1/2 &  5/2 
\end{bmatrix}
\begin{bmatrix}
3 & -3 & 0 \\
0 & 4 & 3\\
0 & 0 & 1
\end{bmatrix}
$$
Rigtigt svar:
![[Pasted image 20250615151734.png]]

## b

$$
\begin{align}
\text{proj}_{\mathcal{U}}(\begin{pmatrix}
4 \\
-1 \\
1
\end{pmatrix})  & = (u_{3}*u_{1})u_{1} + (u_{3}*u_{2})u_{2} \\
 & = (1\cdot (-4)+2\cdot(-1)+(-2)\cdot 1)\begin{pmatrix}
1 \\
2 \\
-2
\end{pmatrix}+
(u_{3}*u_{2})u_{2} \\
 & = \set{0}+(3\cdot 4 + 6 \cdot 1)
\begin{pmatrix}
3 \\
0 \\
6
\end{pmatrix} \\
 & =18\begin{pmatrix}
3 \\
0 \\
6
\end{pmatrix} \\
 & =\begin{pmatrix}
54 \\
0 \\
108
\end{pmatrix}
\end{align}
$$
FORKERT!
Rigtig:
![[Pasted image 20250615154708.png]]

## c

![[Pasted image 20250615154957.png]]

# 4

Vi indsætter lambda i matricen:
$$
\mathbf{M}=
\begin{bmatrix}
0 & a & 2 \\
a & 2 & 0 \\
2 & 0 & a
\end{bmatrix}
$$
$$
\lambda I-M=
\begin{bmatrix}
\lambda & -a & -2 \\
-a & \lambda-2 & 0 \\
-2 & 0 & \lambda-a
\end{bmatrix}
$$Vi kan prøve at indsætte i 
$$Ax = \lambda x$$
$$\begin{bmatrix}
0 & a & 2 \\
a & 2 & 0 \\
2 & 0 & a
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3}
\end{bmatrix}
=
(a+2)
\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3}
\end{bmatrix}
$$
$$\left[\begin{array}{ccc|c}
0 & a & 2 & a+2\\
a & 2 & 0 & a+2\\
2 & 0 & a & a+2 
\end{array}
\right]
$$

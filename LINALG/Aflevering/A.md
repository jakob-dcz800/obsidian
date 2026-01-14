---
tags:
  - Assignment
---
## Opgave 1

### A
$$
\begin{matrix}
x_{1}+2x_{2}+8x_{3} = a \\
ax_{1}+ax_{2}+4ax_{3} = a \\
2x_{1}+2x_{2}+2a^2x_{3} = 0

\end{matrix}
$$


Den reducerede rækkeechelonform af totalmatricen er:
$$
\left[
\begin{array}{ccc|c}
1 &  0 & 0 & 2-a\\
0 & 1 & 0 & (a^3−a^2−4a+8)/(a^2−4)\\
0 & 0 & 1 & 1/(4-a^2)
\end{array}
\right]
$$
#### Vi sætter resultater ind i ligningssystemet
$$
\begin{matrix}
x_{1}=2-a \\
x_{2}=\frac{a^3−a^2−4a+8}{a^2−4}\\
x_{3}=\frac{1}{4-a^2}
\end{matrix}
$$
Vi starter med den første ligning:
$$
x_{1}+2x_{2}+8x_{3}=a \to
(2-a) + 2\left( \frac{a^3−a^2−4a+8}{a^2−4} \right)+8\left( \frac{1}{4-a^2} \right)=a
$$
Actual løsning er:
$$
\begin{matrix}
\frac{r_{2}}{a}\to r_{2} \\
2r_{2}\to r_{2} \\
r_{2}-r_{1}\to r_{1} \\
r_{1}*-1\to r_{1} \\
r_{3}-r_{2}\to r_{3} \\
-\frac{r_{3}}{2} \to r_{3}\\
\frac{r_{3}}{4-a^{2}}\to r_{3} \\
2r_{1}-r_{2}\to r_{2} \\
8r_{3}-r_{2}\to r_{2} \\
\frac{r_{2}}{2}\to r_{2} \\
\text{faktoriser række to til at være at alle brøker får i tælleren: }(a^2-4) 
\end{matrix}
$$

![[Pasted image 20250505151346.png]]

$$
\begin{matrix}
r_{2}\to r_{2} \\
2r_{2}\to r_{2} \\
-r_{2}+r_{1}\to r_{1} \\
-r_{1}\to r_{1} \\
-r_{2}+r_{3}\to r_{3} \\
-\frac{r_{3}}{2}>r_{3} \\
\frac{r_{3}}{4-a^2}\to r_{3} \\
-2r_{1}+r_{2}\to r_{2} \\
-8r_{3}+r_{2}\to r_{2} \\
\text{omskriv } r_{2} \text{ til } \frac{2 a^3 - 2 a^2 - 8 a + 16}{a^2-4}\\
½r_{2}\to r_{2} \\
\text{done}
\end{matrix}
$$
### B
Her er det en [[Homogene ligningssystemer|homogen]] totalmatrix
Hvis rank $A = n$ så har ($S$) kun **nulløsningen**. 
Her er det altså kun nulløsningen

### C
Løs alle tre ligninger på højre side af totalmatrixen
for $a = 2$ og $2-a = 0$ 
$(a^3-a^2-4a+8)/(a^2-4)=(8-4-8+8)/(4-4)=4/0$
! division med nul, kan ikke bruges
**Kun hvis altså rækkeechelonformen er givet ved a)**



### D

Vi bruger computation for $a=1$:
$$
\left[\begin{array}{rrr}
1&2&8\\
1&1&4\\
2&2&2
\end{array}\right]
=
\left[\begin{array}{rrr|r}
1&2&8&  a\\
a&a&4a& a\\
2&2&2a^2& 0
\end{array}\right]
$$
$$
\left[\begin{array}{rrr|rrr}
1 & 2 & 8 & 1 & 0 & 0 \\
1 & 1 & 4 & 0 & 1 & 0 \\
2 & 2 & 2 & 0 & 0 & 1
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-r_{1}+r_{2}\to r_{2} \\
-2r_{1}+r_{3}\to r_{3}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 2 & 8 & 1 & 0 & 0 \\
0 & -1 & -4 & -1 & 1 & 0 \\
0 & -2 & -14 & -2 & 0 & 1
\end{array}\right]
$$
$$
\left[\begin{array}{rrr|rrr}
1 & 2 & 8 & 1 & 0 & 0 \\
0 & -1 & -4 & -1 & 1 & 0 \\
0 & -2 & -14 & -2 & 0 & 1
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-2r_{2}+r_{3}\to r_{3} \\
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 2 & 8 & 1 & 0 & 0 \\
0 & -1 & -4 & -1 & 1 & 0 \\
0 & 0 & -10 & 0 & -2 & 1
\end{array}\right]
$$
$$
\left[\begin{array}{rrr|rrr}
1 & 2 & 8 & 1 & 0 & 0 \\
0 & -1 & -4 & -1 & 1 & 0 \\
0 & 0 & -10 & 0 & -2 & 1
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
\frac{r_{3}}{10}\to r_{3} \\
-1\cdot r_{2}\to r_{2} \\
-1\cdot r_{3}\to r_{3}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 2 & 8 & 1 & 0 & 0 \\
0 & 1 & 4 & 1 & -1 & 0 \\
0 & 0 & 1 & 0 & \frac{1}{5} & -\frac{1}{10}
\end{array}\right]
$$
$$
\left[\begin{array}{rrr|rrr}
1 & 2 & 8 & 1 & 0 & 0 \\
0 & 1 & 4 & 1 & -1 & 0 \\
0 & 0 & 1 & 0 & \frac{1}{5} & -\frac{1}{10}
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-2r_{2}-r_{1}\to r_{1}\\
-4r_{3}+r_{2}\to r_{2}
\end{matrix}
}
\left[\begin{array}{rrr|rrr}
1 & 0 & 0 & -1 & 2 & 0 \\
0 & 1 & 0 & 1 & -\frac{9}{5} & \frac{4}{10} \\
0 & 0 & 1 & 0 & \frac{1}{5} & -\frac{1}{10}
\end{array}\right]
$$
A's inverse matrix er derved givet ved:
$$
[I_{3}\mid X]=
\left[\begin{array}{rrr|rrr}
-1 & 2 & 0 \\
1 & -\frac{1}{3} & \frac{2}{3} \\
0 & \frac{1}{3} & -\frac{1}{6}
\end{array}\right]
$$
Så regner vi $A\begin{bmatrix}x \\ y \\ z\end{bmatrix}=\begin{bmatrix}1 \\ 2 \\ 3\end{bmatrix}$, ved at gange den inverse matrix på begge sider
$$
A^{-1}A\begin{bmatrix}
x \\
y \\
z
\end{bmatrix}
=
\begin{bmatrix}
-1 & 2 & 0 \\
1 & -\frac{1}{3} & \frac{2}{3} \\
0 & \frac{1}{3} & -\frac{1}{6}
\end{bmatrix}
\begin{bmatrix}
1 \\
2 \\
3
\end{bmatrix}
$$

$$
\begin{bmatrix}
-1 & 2 & 0 \\
1 & -\frac{1}{3} & \frac{2}{3} \\
0 & \frac{1}{3} & -\frac{1}{6}
\end{bmatrix}
\begin{bmatrix}
1 \\
2 \\
3
\end{bmatrix}
=\begin{bmatrix}
x \\
y \\
z
\end{bmatrix}
=
\begin{bmatrix}
3 \\
\frac{7}{3} \\
\frac{1}{6}
\end{bmatrix}
$$
## Opgave 2

Det oplyses, at en ukendt $3×3$ matrix $A$, hvori der indgår en parameter $a \not= 0$ ved rækkeoperationerne ero1, ero2, ero3 og ero4 i denne rækkefølge kan omformes til enhedsmatricen.

ero1: $−2ar_1 +r_2 → r_2$ ($2a$ gange første række fratrækkes anden række), 
ero2: $5r_3 → r_3$ (tredje række ganges med 5),
ero3: $r_1 ↔ r_3$ (første og tredje række ombyttes), 
ero4: $(1/a^2)r_3 +r_1 → r_1$ ($1/a^2$ gange tredje række lægges til første række).
Vi lader $E_i$ betegne den elementære matrix, som svarer til rækkeoperationen $ero_i$ (for $i = 1,2,3,4$).
$$
E_{1}=
−2ar_1 +r_2 → r_2
=
\begin{bmatrix}
1 & 0 & 0 \\
-2a & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
$$

E_{2}=
5r_3 → r_3 =

\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 5
\end{bmatrix}
$$
$$

E_{3}=
r_1 ↔ r_3
=
\begin{bmatrix}
0 & 0 & 1 \\
0 & 1 & 0 \\
1 & 0 & 0
\end{bmatrix}
$$
$$

E_{4}=
\left( \frac{1}{a^2} \right)r_3 +r_1 → r_1 = 

\begin{bmatrix}
1 & 0 & \frac{1}{a^2} \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
$E_{4}E_{3}E_{2}E_{1}A = I_{3}$ er lig [[Kvadratmatricer#Enhedsmatrix|enhedsmatricen]] som er defineret ved
$$
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
$$
E_{4}E_{3}E_{2}E_{1}A = I_{3} = A(E_{4}E_{3}E_{2}E_{1}A)
$$
drop ovenstående
Vi starter med:
$$
E_4E_3E_2E_1A=I_{3}
$$
Isolerer A ved at gange med [[Invers matrix|inverse matrix]] efter at have sat $A$ udenfor parentesen, hvilket vi godt må pga. [[LINALG/Matricer/Matrixmultiplikation#Regneregler|associativitet]]
$$
(E_4E_3E_2E_1A)^{-1} \cdot (E_4E_3E_2E_1)A=I_{3} \cdot (E_4E_3E_2E_1A)^{-1}
$$
Så får vi $(E_4E_3E_2E_1)^{-1}$ på begge sider.
Da $matrix \cdot inverse = I$ får vi på venstre side $IA=A$ (altså $A$)
Og på højreside $(E_4E_3E_2E_1)^{-1}$
Aka. $A=(E_4E_3E_2E_1A)^{-1}$

Derfor kan vi også skrive $A(E_4E_3E_2E_1A)^{-1}=I_{3}$

Derfor gælder option 1 & 4

---
Dette kan i næste opgave omskrives til at være
$A=E_{1}^{-1}E_{2}^{-1}E_{3}^{-1}E_{4}^{-1}$

For inverse matricer gælder: $AA^{-1}=I$
Vi bestemmer først inverse matricer $E_{i}^{-1}$:

$$
E_{1}^{-1}=
\begin{bmatrix}
1 & 0 & 0 \\
2a & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
$$
E_{2}^{-1}=
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & \frac{1}{5}
\end{bmatrix}
$$
$$
E_{3}^{-1}=
\begin{bmatrix}
0 & 0 & 1 \\
0 & 1 & 0 \\
1 & 0 & 0
\end{bmatrix}
$$
$$
E_{4}^{-1}=
\begin{bmatrix}
1 & 0 & -\frac{1}{a^2} \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
For at finde invers matrix:
- Ved diagonalen findes  $\frac{1}{d}$ for $d$
- Ellers findes $-d$ for $d$

Nu finder vi $A$
Da vi har at $A=E_{1}^{-1}E_{2}^{-1}E_{3}^{-1}E_{4}^{-1}$
Skriver vi følgende
$$
A= 
\begin{bmatrix}
1 & 0 & 0 \\
2a & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}

\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & \frac{1}{5}
\end{bmatrix}

\begin{bmatrix}
0 & 0 & 1 \\
0 & 1 & 0 \\
1 & 0 & 0
\end{bmatrix}

\begin{bmatrix}
1 & 0 & -\frac{1}{a^2} \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
---
![[Pasted image 20250430101728.png]]

Lad X være den 2x3 (2 rækker, 3 kolonner) matrix hvor
Række 1 i X er række 1 i E4E3E2E1
Række 2 i X er række 3 i E4E3E2E1

$$
V = \begin{bmatrix}
0 & 1 \\
0 & 2a \\
\frac{1}{5} & \frac{-1}{(5a^2)}
\end{bmatrix}
$$
$$
\begin{bmatrix}
1 & 0 & \frac{1}{a^2} \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
0 & 0 & 1 \\
0 & 1 & 0 \\
1 & 0 & 0
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 5
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 \\
-2a & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
=
\begin{bmatrix}
\frac{1}{a^2} & 0 & 5 \\
-2a & 1 & 0 \\
1 & 0 & 0
\end{bmatrix}
$$
AKA.
$$
X=
\begin{bmatrix}
\frac{1}{a^2} & 0 & 5 \\
1 & 0 & 0
\end{bmatrix}
$$

#### Vis, at X er en venstreinvers til V. 
• $X$ er en venstreinvers til $m × n$ matricen $A$ hvis $XA = I_n$ 
$$
\begin{bmatrix}
\frac{1}{a^2} & 0 & 5 \\
1 & 0 & 0
\end{bmatrix}
\begin{bmatrix}
0 & 1 \\
0 & 2a \\
\frac{1}{5} & \frac{-1}{5a^2}
\end{bmatrix}
=
\begin{bmatrix}
0+0+1 & \frac{1}{a^2}+5\cdot \frac{-1}{5a^2} \\
0 & 1
\end{bmatrix}
=
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$
Vi får altså en n\times n enhedsmatrice. Her konkluderer vi, at X er venstreinvers til A.
#### Bestem endvidere alle venstreinverser til V. 

$$
\begin{bmatrix}
x_{1} & x_{2} & x_{3} \\
x_{4} & x_{5} & x_{6}
\end{bmatrix}
\begin{bmatrix}
0 & 1 \\
0 & 2a \\
\frac{1}{5} & \frac{-1}{5a^2}
\end{bmatrix}
=
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$
Vi får et ligningssystem med 4 ligninger og 6 ubekendte:
$$
\begin{matrix}
\frac{1}{5}x_{3}=1 \\
\frac{1}{5}x_{6}=0 \\
x_{1}+2ax_{2}+\frac{-1}{5a^2}x_{3} = 0\\
x_{4}+2ax_{5}+\frac{-1}{5a^2}x_{6} = 1
\end{matrix}
$$
Vi skriver op som totalmatrix:
$$
\left[\begin{array}{rrrrrr|r} 
1 & 2a & \frac{-1}{5a^2} & 0 & 0 & 0 & 0 \\
0 & 0 & \frac{1}{5} & 0 & 0 & 0 & 1 \\
0 & 0 & 0 & 1 & 2a & \frac{-1}{5a^2} & 1 \\
0 & 0 & 0 & 0 & 0 & \frac{1}{5} & 0 \\
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
5r_{1}\to r_{1} \\
5r_{2}\to r_{2} \\
5r_{3}\to r_{3} \\
5r_{4}\to r_{4} \\
\end{matrix}
}
\left[\begin{array}{rrrrrr|r} 
5 & 10a & \frac{-1}{a^2} & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0 & 5 \\
0 & 0 & 0 & 1 & 10a & \frac{-1}{a^2} & 5 \\
0 & 0 & 0 & 0 & 0 & 1 & 0 \\
\end{array}\right]
$$
$$
\left[\begin{array}{rrrrrr|r} 
5 & 10a & \frac{-1}{a^2} & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0 & 5 \\
0 & 0 & 0 & 1 & 10a & \frac{-1}{a^2} & 5 \\
0 & 0 & 0 & 0 & 0 & 1 & 0 \\
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
\frac{1}{a^2}r_{2}+r_{1}\to r_{1} \\
\frac{1}{a^2}r_{4}+r_{3}\to r_{3}  \\
\frac{1}{5}r_{1}\to r_{1} \\
\end{matrix}
}
\left[\begin{array}{rrrrrr|r} 
1 & 2a & 0 & 0 & 0 & 0 & \frac{1}{a^2} \\
0 & 0 & 1 & 0 & 0 & 0 & 5 \\
0 & 0 & 0 & 1 & 10a & 0 & 5 \\
0 & 0 & 0 & 0 & 0 & 1 & 0 \\
\end{array}\right]
$$

$$
\begin{matrix} \\
x_{1} =\frac{1}{a^2}-2as \to2ax_{2}+x_{1}=\frac{1}{a^2} \to 
x_{1}=\frac{1}{a^2} -2ax_{2}   \\
x_{2}=s\\
x_{3}=5 \\
x_{4}+10ax_{5}=5 \to x_{4}=5-10ax_{5}  \\
x_{5}=t \\
x_{6}=0 \\

\end{matrix}
$$
Svaret er:

$$
\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3} \\
x_{4} \\
x_{5} \\
x_{6}
\end{bmatrix}
=
t
\begin{bmatrix}
0 \\
0 \\
0 \\
-10a \\
1 \\
0
\end{bmatrix}
+
s
\begin{bmatrix}
-2a  \\
1 \\
0 \\
0 \\
0 \\
0 \\
\end{bmatrix}
+
\begin{bmatrix}
\frac{1}{a^2} \\
0 \\
5 \\
-5 \\
0 \\
0
\end{bmatrix}
$$
#### Har matricen V også en højreinvers?

Matricen $V$ har ingen højreinvers da $m>n$ (theorem 2.10). 

Derfor **gælder dette ikke:**
$$
\begin{bmatrix}
0 & 1 \\
0 & 2a \\
\frac{1}{5} & \frac{-1}{5a^2}
\end{bmatrix}
\begin{bmatrix}
x_{1} & x_{2} & x_{3}
\end{bmatrix}
=
\begin{bmatrix}
1 \\
0 \\
0
\end{bmatrix}
\text{ osv...}
$$
$$
\left[\begin{array}{rr|rr} 
0 & 1 & 1 & 0 & 0 \\
0 & 2a  & 0 & 1 & 0\\
\frac{1}{5} & \frac{-1}{5a^2} & 0 & 0 & 1
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
r_{1}\leftrightarrow r_{3} \\
-\frac{1}{2a}r_{2}+r_{3}\to r_{3}
\end{matrix}
}
\left[\begin{array}{rr|rr}
\frac{1}{5} & \frac{-1}{5a^2} & 0 & 0 & 1 \\
0 & 2a  & 0 & 1 & 0\\
0 & 0 & 1 & -\frac{1}{2a} & 0
\end{array}\right]
$$
$$
\left[\begin{array}{rr|rr}
\frac{1}{5} & \frac{-1}{5a^2} & 0 & 0 & 1 \\
0 & 2a  & 0 & 1 & 0\\
0 & 0 & 1 & -\frac{1}{2a} & 0
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
5r_{1}\to r_{1} \\
\frac{{1}}{2a}r_{2}\to r_{2}
\end{matrix}
}
\left[\begin{array}{rr|rr}
1 & \frac{-1}{a^2} & 0 & 0 & 5 \\
0 & 1  & 0 & \frac{1}{2a} & 0\\
0 & 0 & 1 & -\frac{1}{2a} & 0
\end{array}\right]
$$
$$
\left[\begin{array}{rr|rr}
1 & \frac{-1}{a^2} & 0 & 0 & 5 \\
0 & 1  & 0 & \frac{1}{2a} & 0\\
0 & 0 & 1 & -\frac{1}{2a} & 0
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
\frac{{1}}{a^2}r_{2}+r_{1}\to r_{1}
\end{matrix}
}
\left[\begin{array}{rr|rr}
1 & 0 & 0 & \frac{1}{2a^3} & 5 \\
0 & 1  & 0 & \frac{1}{2a} & 0\\
0 & 0 & 1 & -\frac{1}{2a} & 0
\end{array}\right]
$$
Her har vi ikke bestemt den højreinverse matrix for A.

## Opgave 3

### a)
Link fra a til b -> 1-tal på række a søjle b
Der står 1 i i’te række, j’te søjle hvis der er et link fra side i til side j

række = fra
søjle = til

$$
\begin{bmatrix}
0 & 1 & 1 & 0 & 0 \\
1 & 0 & 0 & 0 & 1 \\
1 & 0 & 0 & 0 & 0 \\
1 & 1 & 1 & 0 & 1\\
1 & 0 & 0 & 1 & 0 \\
\end{bmatrix}
$$

a.2) Angiv antallet af veje fra knude 4 til knude 1 af længde netop 8
Så finder vi $N_8$, da vi har $N_{7}$, skriver vi:
$$
N^7N=N^8
$$
$$
\begin{bmatrix}
30 & 17 & 17 & 8 & 12 \\
39 & 28 & 28 & 10 & 17 \\
15 & 10 & 10 & 2 & 8 \\
69 & 45 & 45 & 18 & 29\\
53 & 32 & 32 & 9 & 26 \\
\end{bmatrix}
\begin{bmatrix}
0 & 1 & 1 & 0 & 0 \\
1 & 0 & 0 & 0 & 1 \\
1 & 0 & 0 & 0 & 0 \\
1 & 1 & 1 & 0 & 1\\
1 & 0 & 0 & 1 & 0 \\
\end{bmatrix}
$$
Fordi vi ikke gider udregne 25 regnestykker, udregner vi kun den vi har behov for
![[Pasted image 20250430161635.png]]

Udtryk det matematisk
[[LINALG/Matricer/Matricer|Matricer]]

summen af række 4 N^7
$$
\sum^n_{k\in n}{N^{7}_{1,k}N_{k,1}}
$$
### b)
Opskriv linkmatricen $A$ for grafen ovenfor.
Byt om på rækker og søjler
På række n, noter 1/a for udgangene
Værdierne er udgående pile på `knude[søjle]`
$$
\begin{bmatrix}
0 & 1/2 & 1 & 1/4 & 1/2 \\
1/2 & 0 & 0 & 1/4 & 0 \\
1/2 & 0 & 0 & 1/4 & 0 \\
0 & 0 & 0 & 0 & 1/2\\
0 & 1/2 & 0 & 1/4 & 0 \\
\end{bmatrix}
$$
### C)
Linkmatricen bliver til [[Lineære systemer|ligningssystemet]]:
$$
\begin{matrix}
x_{1}=\frac{1}{2}x_{2}+x_{3}+\frac{1}{4}x_{4}+\frac{1}{2}x_{5} \\
x_{2}=\frac{1}{2}x_{1}+\frac{1}{4}x_{4} \\
x_{3}=\frac{1}{2}x_{1}+\frac{1}{4}x_{4} \\
x_{4}=\frac{1}{2}x_{5} \\
x_{5}=\frac{1}{2}x_{2}+\frac{1}{4}x_{4}
\end{matrix}
$$
Dette kan vi omskrive til en totalmatrix ved at rykke alle x'er over på den samme side
$$
\left[\begin{array}{ccccc|c}
-1 & 1/2 & 1 & 1/4 & 1/2  & 0\\
1/2 & -1 & 0 & 1/4 & 0  & 0\\
1/2 & 0 & -1 & 1/4 & 0  & 0\\
0 & 0 & 0 & -1 & 1/2 & 0\\
0 & 1/2 & 0 & 1/4 & -1  & 0\\
\end{array}\right]
$$
Vi ganger rækker med heltal for at fjerne brøker
$$
\left[\begin{array}{ccccc|c}
-1 & 1/2 & 1 & 1/4 & 1/2  & 0\\
1/2 & -1 & 0 & 1/4 & 0  & 0\\
1/2 & 0 & -1 & 1/4 & 0  & 0\\
0 & 0 & 0 & -1 & 1/2 & 0\\
0 & 1/2 & 0 & 1/4 & -1  & 0\\
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
4r_{1} +r_{1}\to r_{1} \\
4r_{2} +r_{2}\to r_{2} \\
4r_{3} +r_{3}\to r_{3} \\
4r_{4} +r_{4}\to r_{4} \\
4r_{5} +r_{5}\to r_{5} \\
\end{matrix}
}
\left[\begin{array}{ccccc|c}
-4 & 2 & 4 & 1 & 2  & 0\\
2 & -4 & 0 & 1 & 0  & 0\\
2 & 0 & -4 & 1 & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 2 & 0 & 1 & -4  & 0\\
\end{array}\right]
$$
$$
\left[\begin{array}{ccccc|c}
-4 & 2 & 4 & 1 & 2  & 0\\
2 & -4 & 0 & 1 & 0  & 0\\
2 & 0 & -4 & 1 & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 2 & 0 & 1 & -4  & 0\\
\end{array}\right]
\xrightarrow[]{
\begin{matrix} \\
r_{1}+r_{5}\to r_{5} \\
r_{2}+r_{5}\to r_{5} \\
r_{3}+r_{5}\to r_{5}  \\
r_{4}+r_{5} \to r_{5}
\end{matrix}
}
\left[\begin{array}{ccccc|c}
-4 & 2 & 4 & 1 & 2  & 0\\
2 & -4 & 0 & 1 & 0  & 0\\
2 & 0 & -4 & 1 & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
$$
$$
\left[\begin{array}{ccccc|c}
-4 & 2 & 4 & 1 & 2  & 0\\
2 & -4 & 0 & 1 & 0  & 0\\
2 & 0 & -4 & 1 & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
½r_{1}+r_{2}\to r_{2} \\
½r_{1}+r_{3}\to r_{3} \\
r_{2}\leftrightarrow r_{3} \\
2r_{2}+r_{3}\to r_{3}
\end{matrix}
}
\left[\begin{array}{ccccc|c}
-4 & 2 & 4 & 1 & 2  & 0\\
0 & 1 & -2 & \frac{3}{2} & 1  & 0\\
0 & 0 & -2 & \frac{9}{2} & 3  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
$$
$$
\left[\begin{array}{ccccc|c}
-4 & 2 & 4 & 1 & 2  & 0\\
0 & 1 & -2 & \frac{3}{2} & 1  & 0\\
0 & 0 & -2 & \frac{9}{2} & 3  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
2r_{2}\to r_{2}  \\
2r_{3}\to r_{3} \\
-\frac{1}{4}r_{1}\to r_{1}
\end{matrix}
}
\left[\begin{array}{ccccc|c}
1 & -½ & -1 & -\frac{1}{4} & -½  & 0\\
0 & 2 & -4 & 3 & 2  & 0\\
0 & 0 & -4 & 9 & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
$$
$$
\left[\begin{array}{ccccc|c}
1 & -½ & -1 & -\frac{1}{4} & -½  & 0\\
0 & 2 & -4 & 3 & 2  & 0\\
0 & 0 & -4 & 9 & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
½r_{2}\to r_{2} \\
½r_{2}+r_{1}\to r_{1} \\
-\frac{1}{4}r_{3}\to r_{3}
\end{matrix}
}
\left[\begin{array}{ccccc|c}
1 & 0 & -2 & ½ & 0  & 0\\
0 & 1 & -2 & \frac{3}{2} & 1 & 0\\
0 & 0 & 1 & -\frac{9}{4} & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
$$
$$
\left[\begin{array}{ccccc|c}
1 & 0 & -2 & ½ & 0  & 0\\
0 & 1 & -2 & \frac{3}{2} & 1 & 0\\
0 & 0 & 1 & -\frac{9}{4} & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
2r_{3}+r_{1}\to r_{1} \\
2r_{3}+r_{2}\to r_{2}
\end{matrix}
}
\left[\begin{array}{ccccc|c}
1 & 0 & 0 & -4 & 0  & 0\\
0 & 1 & 0 & -3 & 1 & 0\\
0 & 0 & 1 & -\frac{9}{4} & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
$$
$$
\left[\begin{array}{ccccc|c}
1 & 0 & 0 & -4 & 0  & 0\\
0 & 1 & 0 & -3 & 1 & 0\\
0 & 0 & 1 & -\frac{9}{4} & 0  & 0\\
0 & 0 & 0 & -4 & 2 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-\frac{1}{4}r_{4}\to r_{4} \\
4r_{4}+r_{1}\to r_{1}  \\
3r_{4}+r_{2}\to r_{2} \\
\frac{9}{4}r_{4}+r_{3}\to r_{3} \\
-r_{4}+r_{3}\to r_{3}
\end{matrix}
}
\left[\begin{array}{ccccc|c}
1 & 0 & 0 & 0 & -2  & 0\\
0 & 1 & 0 & 0 & -½ & 0\\
0 & 0 & 1 & 0 & \frac{9}{8} & 0\\
0 & 0 & 0 & 1 & 0 & 0\\
0 & 0 & 0 & 0 & 0  & 0\\
\end{array}\right]
$$
Således har vi echelonformen af matricen. Vi har en fri variabel $x_{5}$

$$
\begin{matrix}
x_{5}=t \\
 \\
x_{1} -4x_{5}=0 \\
x_{2}-½x_{5}=0 \\
x_{3}+\frac{9}{8}=0 \\
x_{4}=0
\end{matrix}
$$

$$
\begin{matrix}
x_{1}=4t\\
x_{2}=½t \\
x_{3}=-\frac{9}{8} \\
x_{4}=0 \\
x_{5}=t
\end{matrix}
$$
$$
\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3} \\
x_{4} \\
x_{5}
\end{bmatrix}
=
t
\begin{bmatrix}
4 \\
½ \\
\frac{9}{8} \\
0 \\
1
\end{bmatrix}
$$
TJEK MED VALDEMAR

**Der skal være frie variable**

---
Vi bør ende på med:
$$
v = 
\begin{bmatrix}
x_{1} \\
x_{2} \\ 
x_{3} \\
x_{4} \\
x_{5} \\
\end{bmatrix}
$$
Ganget med en variabel t

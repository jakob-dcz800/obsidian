---
tags:
  - Math
  - Matrices
  - LINALG
---
# Søjlerum

Søjlerummet er spannet af alle søjler i en matrix.
Søjlerummet er et underrum af $\Bbb{R}^n$
Søjlerummet er spannet af søjlerne.
Søjlerummet skrives som $\text{col }A=\text{span}\set{A_{1}, \dots, A_{n}}$

## Definition

![[Pasted image 20250507134041.png]]
## Theorem

### 3.10
![[Pasted image 20250506213055.png]]

### 3.13
![[Pasted image 20250506213134.png]]

* Vi finder søjlerne som har ledende 1-taller i den reducerede form
* Så finder vi de tilsvarende søjler i A. Basen udgøres af disse.
## Eksempel

### 1
![[Pasted image 20250506213105.png]]
![[Pasted image 20250506213113.png]]

"Med $x_{3}=1$ og $x_{5}=0$ fås"
Fordi at der er samtlige løsninger til ligningssystemet:
$$
\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3} \\
x_{4} \\
x_{5}
\end{bmatrix}
=
s
\begin{bmatrix}
-1 \\
1 \\
1 \\
0 \\
0
\end{bmatrix}
+t
\begin{bmatrix}
-2 \\
-1 \\
0 \\
1 \\
2
\end{bmatrix}
$$
Vi vælger så en af mange løsninger, her vælger vi $s=1, t=0$.
I det tilfælde frafalder den højre matrix 
$$
0
\begin{bmatrix}
-2 \\
-1 \\
0 \\
1 \\
2
\end{bmatrix}
=\mathbf{0}
$$
Dvs. vi får:
$$
A
\begin{bmatrix}
-1 \\
1 \\
1 \\
0 \\
0
\end{bmatrix}
=0
$$
Vælger vi $s=0,t=1$, bliver det omvendt:
$$
A
\begin{bmatrix}
-2 \\
-1 \\
0 \\
1 \\
2
\end{bmatrix}
=\mathbf{0}
$$
Da $s = x_{3}, t=x_{5}$ er det det som er meningen med valget af $x_{3}, x_{5}$
Eksemplet viser, at $A_{3}$ er en linearkombination af de to første søjler.
Fordi vi kan udvide spannet med flere søjler, er det også $\text{span}\set{A_{1},A_{2},A_{4}}$
Det omvendte valg af $x_{3}, x_{5}$ viser at $A_{5}$ er en linearkombination af de tre søjler i eksemplet.
Alle søjler er en linearkombination af søjle 1,2 og 4
![[Pasted image 20250506213122.png]]

Alt hvad vi kan få frem af linearkombinationer kan vi udtrykke som spannet af søjle 1, 2 og 4.
Dvs. de tre søjler udspænder søjlerummet.
Det er ikke sikkert at de tre søjler er lineært uafhængige, men det er de i eksemplet.
Vi laver Gauss-Jordan elimination på den fulde matrix A, men glemmer lige søjle 3 og 5.
Her ser vi at de er uafhængige fordi den kommer på reduceret rækkeechelonform

![[Pasted image 20250506213145.png]]
# 1

## a)

$$
\mathbf{A} = \begin{bmatrix}
3 & 1 & 19 \\
0 & 2 & 14 \\
-2 & 6 & -15 \\
6 & -2 & 10
\end{bmatrix}
$$
Bestem en [[Gram-Schmidt processen#QR-faktorisering|QR-faktorisering]] af A.
Vi har søjlerne i $\mathbb{R}^4$
$$
u_{1}=\begin{pmatrix}
3 \\
0 \\
-2 \\
6
\end{pmatrix}
,u_{2}=\begin{pmatrix}
1 \\
2 \\
6 \\
-2
\end{pmatrix}
,u_{3}=\begin{pmatrix}
19 \\
14 \\
-15 \\
10
\end{pmatrix}
$$
Vi bestemmer $\mathbf{q}_{1},\mathbf{q}_{2},\mathbf{q}_{3}$ og bestemmer matricen $\mathbf{Q}$ på baggrund af disse. Vi begynder med at bestemme normen af $\mathbf{u}_{1} = r_{11}$
$r_{11}=\lVert \mathbf{u}_{1} \rVert=\sqrt{ 3^2+0^2+(-2)^2+6^2 } = 7$
Vi bestemmer så $\mathbf{q}_{1}$ på baggrund af $r_{11}$:
$$
\mathbf{q}_{1}
=\frac{\mathbf{u}_{1}}{7}=
\begin{pmatrix}
\frac{3}{7} \\
0 \\
-\frac{2}{7} \\
\frac{6}{7}
\end{pmatrix}
$$
Dernæst bestemmer vi $r_{12}$ på vha. $\mathbf{q}_{1}$:
$$
r_{12}
= \mathbf{q}_{1}\bullet \mathbf{u}_{2}
= 1\left( \frac{3}{7} \right)+6\left( -\frac{2}{7} \right)-2\left( \frac{6}{7} \right)
=-3
$$
Vi projicerer $\mathbf{u}_{2}$ på $\mathbf{q}_{1}$:
$$
\mathbf{q}'_{2}
= \mathbf{u}_{2}-r_{12}\mathbf{q}_{1}
= \begin{pmatrix}
1 \\
2 \\
6 \\
-2
\end{pmatrix}
-(-3)
\begin{pmatrix}
3/7 \\
0 \\
-2/7 \\
6/7
\end{pmatrix}
=
\begin{pmatrix}
1 \\
2 \\
6 \\
-2
\end{pmatrix}
-
\begin{pmatrix}
-\frac{9}{7} \\
0 \\
\frac{6}{7} \\
-\frac{18}{7}
\end{pmatrix}
=\begin{pmatrix}
\frac{16}{7} \\
2 \\
\frac{36}{7} \\
\frac{4}{7}
\end{pmatrix}
$$
Vi bestemmer så lænden $r_{22}$ af projiceringen.
$$
r_{22}=\|\mathbf{q}'_{2}\|
=
\sqrt{ \left( \frac{16}{7} \right)^2+2^2+\left( \frac{36}{7} \right)^2 +\left( \frac{4}{7} \right)^2 }
= 6
$$
Denne benytter vi til at normere $\mathbf{q}'_{2}$, og får $\mathbf{q}_{2}$
$$
\mathbf{q}_{2}
= \frac{\mathbf{q}'_{2}}{6}
= \frac{1}{6}
\begin{pmatrix}
\frac{16}{7} \\
2 \\
\frac{36}{7} \\
\frac{4}{7}
\end{pmatrix}
=
\begin{pmatrix}
\frac{8}{21} \\
\frac{1}{3} \\
\frac{6}{7} \\
\frac{2}{21}
\end{pmatrix}
$$
Vi bestemmer $r_{13}$ vha. $\mathbf{q}_{1}, \mathbf{u}_{3}$
$$
r_{13}
= \mathbf{q}_{1} \cdot \mathbf{u}_{3} 
= 19\left( \frac{3}{7} \right)+14(0)-15\left( -\frac{2}{7} \right)+10\left( \frac{6}{7} \right)
= \frac{147}{7}
= 21
$$
Vi bestemmer $r_{23}$ vha. $\mathbf{q}_{2}, \mathbf{u}_{3}$
$$
r_{23}
= \mathbf{q}_{2} \cdot \mathbf{u}_{3} 
= 19   \left( \frac{8}{21} \right)
  + 14 \left( \frac{1}{3} \right)
  - 15 \left( \frac{6}{7} \right)
  + 10 \left( \frac{2}{21} \right)
= 0
$$
Så regner vi $\mathbf{q}'_{3}$
$$
\begin{align}
\mathbf{q}'_{3} =\\
\mathbf{u}_{3}-r_{13}\mathbf{q}_{1}-r_{23}\mathbf{q}_{2} =\\ \mathbf{u}_{3}-r_{13}\mathbf{q}_{1}
\end{align}
$$
$$
\mathbf{q}'_{3}=
\begin{pmatrix}
19 \\
14 \\
-15 \\
10
\end{pmatrix}
-
21
\begin{pmatrix}
\frac{3}{7} \\
0 \\
-\frac{2}{7} \\
\frac{6}{7}
\end{pmatrix}
=
\begin{pmatrix}
19 \\
14 \\
-15 \\
10
\end{pmatrix}
-
\begin{pmatrix}
9 \\
0 \\
-6 \\
12
\end{pmatrix}
=
\begin{pmatrix}
10 \\
14 \\
-9 \\
-8
\end{pmatrix}
$$
Dernæst regner vi $r_{33}$
$$
r_{33}
= \|\mathbf{q}'_{3}\|
= \sqrt{ 10^2+14^2+(-9)^2+(-8)^2 }
= \sqrt{ 441 }
= 21
$$
Og således får vi den sidste søjle i $\mathbf{A}$: $\mathbf{q}_{3}=\frac{\mathbf{q}'_{3}}{r_{33}}$
$$
\mathbf{q}_{3}=
\frac{1}{21}
\begin{pmatrix}
10 \\
14 \\
-9 \\
-8
\end{pmatrix}
=
\begin{pmatrix}
\frac{10}{21} \\
\frac{2}{3} \\
-\frac{3}{7} \\
-\frac{8}{21}
\end{pmatrix}
$$
Vi får altså matricen $\mathbf{A}$:
$$
\mathbf{A}=\mathbf{QR}=
\begin{pmatrix}
\mathbf{q}_{1} & \mathbf{q}_{2} & \mathbf{q}_{3}
\end{pmatrix}
\begin{bmatrix}
r_{11} & r_{12} & r_{13} \\
0 & r_{22} & r_{23} \\
0 & 0 & r_{33}
\end{bmatrix}
$$
Vi udregner:
$$
\begin{bmatrix}
\frac{3}{7} & \frac{8}{21} & \frac{10}{21} \\
0  & \frac{1}{3} & \frac{2}{3} \\
-\frac{2}{7} & \frac{6}{7} & -\frac{3}{7} \\
\frac{6}{7} & \frac{2}{21} & -\frac{8}{21}
\end{bmatrix}
\begin{bmatrix}
7 & -3 & 21 \\
0 & 6 & 0 \\
0 & 0 & 21
\end{bmatrix}
\to
\begin{bmatrix}
0.43 & 0.38 & 0.48 \\
0.00 & 0.33 & 0.67 \\
-0.29 & 0.86 & -0.43 \\
0.86 & 0.10 & -0.38
\end{bmatrix}
\begin{bmatrix}
7 & -3 & 21 \\
0 & 6 & 0 \\
0 & 0 & 21
\end{bmatrix}
$$
Når vi regner efter får vi den originale matrice
$$
\mathbf{A} =
\begin{bmatrix}
0.43 & 0.38 & 0.48 \\
0.00 & 0.33 & 0.67 \\
-0.29 & 0.86 & -0.43 \\
0.86 & 0.10 & -0.38
\end{bmatrix}
\begin{bmatrix}
7 & -3 & 21 \\
0 & 6 & 0 \\
0 & 0 & 21
\end{bmatrix}
= 
\begin{bmatrix}
3 & 1 & 19 \\
0 & 2 & 14 \\
-2 & 6 & -15 \\
6 & -2 & 10
\end{bmatrix}
$$
## b)

Givet vores QR faktorisering er vi givet en ortonormal basis $\mathbf{Q}$ for underrummet $\mathcal{U}$.
Projektionsmatricen er derfor givet ved 
$$
\mathbf{P}=\mathbf{QQ}^T
$$
$$
\begin{align}
\mathbf{P}=
\begin{bmatrix}
0.43 & 0.38 & 0.48 \\
0.00 & 0.33 & 0.67 \\
-0.29 & 0.86 & -0.43 \\
0.86 & 0.10 & -0.38
\end{bmatrix}
\begin{bmatrix}
0.43 & 0.38 & 0.48 \\
0.00 & 0.33 & 0.67 \\
-0.29 & 0.86 & -0.43 \\
0.86 & 0.10 & -0.38
\end{bmatrix}
^T \\
=\begin{bmatrix}
0.43 & 0.38 & 0.48 \\
0.00 & 0.33 & 0.67 \\
-0.29 & 0.86 & -0.43 \\
0.86 & 0.10 & -0.38
\end{bmatrix}
\begin{bmatrix}
0.43 & 0.00 & -0.29 & 0.86 \\
0.38 & 0.33 & 0.86 & 0.10 \\
0.48 & 0.67 & -0.43 & -0.38
\end{bmatrix}
\\=
\begin{bmatrix}
0.56 & 0.44 & 0.00 & 0.22 \\
0.44 & 0.56 & 0.00 & -0.22 \\
0.00 & 0.00 & 1.00 & 0.00 \\
0.22 & -0.22 & 0.00 & 0.89
\end{bmatrix}
\end{align}
$$
Vi har nu bestemt projektionsmatricen for A.
P er en kvadratisk matrix. 

Søjlerne i matricen $\mathbf{Q}$ er parvist ortonormale hvis $\mathbf{Q}^T\mathbf{Q}=I_{n}$
Siden vi har en ortonormal basis gælder ovenstående også (definition 4.8).
Hvis søjlerne er ortonormale, er de også ortogonale, derfor gælder:
$\mathbf{Q}^T=\mathbf{Q}^{-1}$
Derfor kan vi skrive
$\mathbf{P}=\mathbf{QQ}^{-1}$
Med dette følger naturligvis:
$\mathbf{P}^2=(\mathbf{QQ}^{-1})(\mathbf{QQ}^{-1})$
Den associative regel gælder, og vi må derfor sætte vores parenteser hvorend vi har lyst:
$$
\mathbf{P}^2
= \mathbf{Q}(\mathbf{Q}^{-1}\mathbf{Q})\mathbf{Q}^{-1}
= \mathbf{Q}(I_{n})\mathbf{Q}^{-1}
= \mathbf{QQ}^{-1}
= \mathbf{P}
$$
Vi viser altså at  $\mathbf{P}^2=\mathbf{P}$, vi kan altså drage, at $\mathbf{P}^n=\mathbf{P}$ for $n \geq 1$.

## c)

[[Ortogonal projektion#3 Ortogonal projektion på en plan]]
Vi regner $\mathbf{x}$ til at være 
$$
\mathbf{x}=
\left[\begin{array}{c}
0 \\
0 \\
1 \\
0
\end{array}\right]
$$
Da $\set{\mathbf{q}_{1},\mathbf{q}_{2},\mathbf{q}_{3}}$ er en ortogonal basis for underrummet for underrumet $\mathcal{U}$ er:
$$
\text{proj }_{\mathcal{U}}(\mathbf{x})
= \frac{\mathbf{x\cdot q}_{1}}{\|\mathbf{q}_{1}\|^2}\mathbf{q}_{1}
+ \frac{\mathbf{x\cdot q}_{2}}{\|\mathbf{q}_{2}\|^2}\mathbf{q}_{2}
+ \frac{\mathbf{x\cdot q}_{3}}{\|\mathbf{q}_{3}\|^2}\mathbf{q}_{3}
$$
Da $\set{\mathbf{q}_{1},\mathbf{q}_{2},\mathbf{q}_{3}}$ også er en ortonormal basis, er alle vektornormer lig 1.
$$
\text{proj }_{\mathcal{U}}(\mathbf{x})
= (\mathbf{x\cdot q}_{1})\mathbf{q}_{1}
+ (\mathbf{x\cdot q}_{2})\mathbf{q}_{2}
+ (\mathbf{x\cdot q}_{3})\mathbf{q}_{3}
$$
$$
\left(
\begin{pmatrix}
0 \\
0 \\
1 \\
0
\end{pmatrix}
\cdot
\begin{pmatrix}
0.43 \\
0.00 \\
-0.29 \\
0.86
\end{pmatrix}
\right)
\begin{pmatrix}
0.43 \\
0.00 \\
-0.29 \\
0.86
\end{pmatrix}
+
\left(
\begin{pmatrix}
0 \\
0 \\
1 \\
0
\end{pmatrix}
\cdot
\begin{pmatrix}
0.38 \\
0.33 \\
0.86 \\
0.10
\end{pmatrix}
\right)
\begin{pmatrix}
0.38 \\
0.33 \\
0.86 \\
0.10
\end{pmatrix}
+
\left(
\begin{pmatrix}
0 \\
0 \\
1 \\
0
\end{pmatrix}
\cdot
\begin{pmatrix}
0.48 \\
0.67 \\
-0.43 \\
-0.38
\end{pmatrix}
\right)
$$
$$
-0.29\mathbf{q}_{1}+0.86\mathbf{q}_{2}-0.43\mathbf{q}_{3}
=
\left[\begin{array}{c}
- 0.0014285715 \\
0.0 \\
1.004285714 \\
- 0.0028571429 
\end{array}\right]
$$
Ikke sikker på at den er korrekt.
Spejlingen er givet ved:
$\text{refl }_{\mathcal{U}}(\mathbf{x})=2\text{ proj }_{\mathcal{U}}(\mathbf{x})-\mathbf{x}$
Vi regner:
$$
\text{refl }_{\mathcal{U}}(\mathbf{x})
= 2 \left[\begin{array}{c}
- 0.0014 \\
0.0000 \\
1.0043 \\
- 0.0028
\end{array}\right]
-
\begin{bmatrix}
0 \\
0 \\
1 \\
0
\end{bmatrix}
=
\begin{bmatrix}
-0.0028 \\
0.0000 \\
1.0086 \\
-0.0056
\end{bmatrix}
$$
## d)

[[Ortogonalt underrum#Ortogonalt komplement]]
[[Nulrum]]

Vi ved, at $\text{dim }\mathcal{U}+\text{dim }\mathcal{U}^\perp = n$, derfor har det ortogonale komplement dimension 1.

Vi bestemmer det ortogonale komplement til $\mathcal{U}$ således:
$$
\mathcal{U}^\perp
= (\text{col }\mathbf{A})^\perp
= \text{null } \mathbf{A}^T
$$
Vi bestemmer først $\mathbf{A}^T$
$$
\mathbf{A}^T =
\mathbf{A} = \begin{bmatrix}
3 & 1 & 19 \\
0 & 2 & 14 \\
-2 & 6 & -15 \\
6 & -2 & 10
\end{bmatrix}^T
=
\left[\begin{array}{cccc}
3 & 0 & -2 & 6 \\
1 & 2 & 6 & -2 \\
19 & 14 & -15 & 10 
\end{array}\right]
$$
Derefter nulls-space ved at sætte $\mathbf{Ax}=\mathbf{0}$

## e) 

Hvis B fortsat er en ortonormal basis er den transponerede matrix den inverse


# 2


## a)

Det karakteristiske polynomium er givet ved:
$$
p(\lambda)=\text{det }(\lambda \mathbf{I}-\mathbf{M})
$$
Vi indsætter lambda i matricen: 
$$
\lambda \mathbf{I}-\mathbf{M}
=
\begin{bmatrix}
\lambda+2 & 6 & 3 \\
-3 & \lambda -7 & -3 \\
6 & 12 & \lambda+5
\end{bmatrix}
$$
Vi udfører så rækkeoperationer på $\lambda \mathbf{I}-\mathbf{M}$
$$
\begin{bmatrix}
\lambda+2 & 6 & 3 \\
-3 & \lambda -7 & -3 \\
6 & 12 & \lambda+5
\end{bmatrix}
\xrightarrow[]{
\begin{matrix} \\
r_{2}+r_{1}\to r_{1}
\end{matrix}
}
\begin{bmatrix}
\lambda-1 & \lambda-1 & 0 \\
-3 & \lambda -7 & -3 \\
6 & 12 & \lambda+5
\end{bmatrix}
$$
$$
\begin{bmatrix}
\lambda-1 & \lambda-1 & 0 \\
-3 & \lambda -7 & -3 \\
6 & 12 & \lambda+5
\end{bmatrix}
\xrightarrow[]{
\begin{matrix}
2r_{2}+r_{3}\to r_{3}
\end{matrix}
}
\begin{bmatrix}
\lambda-1 & \lambda-1 & 0 \\
-3 & \lambda -7 & -3 \\
0 & 2(\lambda-1) & \lambda-1
\end{bmatrix}
$$


Vi ved fra thm. 5.3 at hvis $\mathbf{B}$ fremkommer fra $\mathbf{A}$ ved rækkeoperation $r_{i}+mr_{j}\to r_{i}$ for $i \not=j$, så gælder $\text{det }\mathbf{B}=\text{det }\mathbf{A}$. 
Derfor er $\text{det }\lambda \mathbf{I}-\mathbf{M}$ uændret.

Vi kan altså rykke (\lambda-1) udenfor matricen når vi regner determinanten:

$$
\begin{align}
\text{det}\begin{bmatrix}
\lambda-1 & \lambda-1 & 0 \\
-3 & \lambda -7 & -3 \\
0 & 2(\lambda-1) & \lambda-1
\end{bmatrix}
 \\=
(\lambda-1)
\text{ det}
\begin{bmatrix}
1 & 1 & 0 \\
-3 & \lambda -7 & -3 \\
0 & 2(\lambda-1) & \lambda-1
\end{bmatrix}
\\=
(\lambda-1)^2 \text{ det}
\begin{bmatrix}
1 & 1 & 0 \\
-3 & \lambda -7 & -3 \\
0 & 2 & 1
\end{bmatrix}
\end{align}
$$
Ikke sikker på, at man bare må sætte $\lambda-1$ i potens?
Vi udvikler efter 1. række
$$
\begin{align}
p(\lambda)
=
(\lambda-1)^2
\left(
\text{det}\begin{pmatrix}
-3 & \lambda-7 \\
0 & 2
\end{pmatrix}
-1\cdot
\text{det}\begin{pmatrix}
-3 & -3 \\
0 & 1
\end{pmatrix}
\right) \\
=
(\lambda-1)^2 ((\lambda-7)(1)-(-3)(2)-(-3)(1)-(-3)(0)) \\
= (\lambda-1)^2(λ−7+6-(-3)) \\
= (λ−1)^2⋅ \\
= (\lambda-1)^2(\lambda+2)
\end{align}
$$
Vi har altså givet det karakteristiske ligning ved $(\lambda-1)^2(\lambda+2)$. 
Vi kan omskrive ligningen til at være det karakteristiske polynomium:
$$
\lambda^3-3\lambda+2
$$
## b) Bestem alle egenværdierne for M.

Vi kan hurtigt aflæse rødderne som værende $\lambda=1,\lambda=(-2)$ når vi kigger på den karakteristiske ligning $(\lambda-1)^2(\lambda+2)$. 

## c)
Bestem for hver egenværdi for $\mathbf{M}$ en basis for det tilhørende [[egenrum]]. Angiv for hver egenværdi for $\mathbf{M}$ dens geometriske multiplicitet.

Vi skal altså bestemme egenrummet givet ved $E_{\lambda}=\text{null }(\mathbf{M}-\lambda \mathbf{I})$ for begge egenværdier $\lambda=1,\lambda=-2$

Vi starter med $\lambda=1$ og indsætter i matricen:
$$
\mathbf{M}-\mathbf{I}
=
\begin{bmatrix}
-3 & -6 & -3 \\
3 & 6 & 3 \\
-6 & -12 & -6
\end{bmatrix}
$$
Vi udregner så nulrummet ved at udføre Gauss-Jordan eliminering på matricen:
$$
\begin{bmatrix}
-3 & -6 & -3 \\
3 & 6 & 3 \\
-6 & -12 & -6
\end{bmatrix}
\xrightarrow[]{
\begin{matrix}
r_{1}+r_{2}\to r_{2} \\
2r_{1}-r_{3}\to r_{3} \\
-\frac{1}{3}r_{1}\to r_{1}
\end{matrix}
}
\begin{bmatrix}
1 & 2 & 1 \\
0 & 0 & 0 \\
0 & 0 & 0
\end{bmatrix}
$$
Vi får så ligningen $x_{1}+2x_{2}+x_{3}=0$, og sætter $x_{2}=s, x_{3}=t$
Vi får således:
$$
\mathbf{Mx}
= s
\begin{pmatrix}
-2 \\
1 \\
0
\end{pmatrix}
+ t
\begin{pmatrix}
-1 \\
0 \\
1
\end{pmatrix}
$$
Nulrummet og derved også egenrummet for $\lambda=1$ er derfor:
$$
E_{\lambda=1}
= \text{null }(\mathbf{M}-\lambda \mathbf{I})
= \text{span } \begin{Bmatrix}
\begin{pmatrix}
-2 \\
1 \\
0
\end{pmatrix}
,
\begin{pmatrix}
-1 \\
0 \\
1
\end{pmatrix}
\end{Bmatrix}
$$
Den geometriske multiplicitet er $\text{dim null }(\mathbf{A}-\lambda \mathbf{I})=2$
Vi gør nu det samme for $\lambda=(-2)$
Vi har matricen
$$
\mathbf{M}-(-2)\mathbf{I}
=
\left[\begin{array}{ccc}
0 & -6 & -3 \\
3 & 9 & 3 \\
-6 & -12 & -3
\end{array}\right]
$$
Vi udfører Gauss Jordan
$$
\left[\begin{array}{ccc}
0 & -6 & -3 \\
3 & 9 & 3 \\
-6 & -12 & -3
\end{array}\right]
\xrightarrow[]{
\begin{matrix} \\
r_{1}\leftrightarrow r_{2} \\
\frac{1}{3}r_{1}\to r_{1}
\end{matrix}
}
\left[\begin{array}{ccc}
1 & 3 & 1 \\
0 & -6 & -3 \\
-6 & -12 & -3
\end{array}\right]
$$
$$
\left[\begin{array}{ccc}
1 & 3 & 1 \\
0 & -6 & -3 \\
-6 & -12 & -3
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
6r_{1}+r_{3}\to r_{3} \\
-\frac{1}{6}r_{2}\to r_{2}
\end{matrix}
}
\left[\begin{array}{ccc}
1 & 3 & 1 \\
0 & 1 & \frac{1}{2} \\
0 & 6 & 3
\end{array}\right]
$$
$$
\left[\begin{array}{ccc}
1 & 3 & 1 \\
0 & 1 & \frac{1}{2} \\
0 & 6 & 3
\end{array}\right]
\xrightarrow[]{
\begin{matrix}
-3r_{2}+r_{1} \\
-6r_{2}+r_{3}
\end{matrix}
}
\left[\begin{array}{ccc}
1 & 0 & -\frac{1}{2} \\
0 & 1 & \frac{1}{2} \\
0 & 0 & 0
\end{array}\right]
$$
Vi får altså ligningerne:
$$
\begin{align}
x_{1}-\frac{1}{2}x_{3} & = 0 \\
x_{2}+\frac{1}{2}x_{3} & = 0
\end{align}
$$
Vi får altså basen for egenrummet
$$
E_{\lambda=(-2)}
= \text{null }(\mathbf{M}-\lambda \mathbf{I})
= \text{span } \begin{Bmatrix}
\begin{pmatrix}
1/2 \\
-1/2 \\
1
\end{pmatrix}
\end{Bmatrix}
$$
Den geometriske multiplicitet er givet ved antallet af frie variable som aflæses af den reducerede rækkeechelonform, her er den 1.

## d)

Vi har de to baser: $E_{\lambda_{1}}=E_{\lambda=(-2)}, E_{\lambda_{2}}=E_{\lambda=1}$
Deres geometriske multipliciteter er givet ved:
$$
\begin{align}
g_{\lambda1}=g_{1}=1 \\
g_{\lambda2}=g_{-2}=2 \\ \\

n=g_{\lambda1}+g_{\lambda_{2}}=3
\end{align}
$$
Dimensionen er lig summen af de geometriske multipliciteter og matricen M er derfor diagonalisérbar. Den invertible $\mathbf{P}$ matrice er givet ved søjlerne af de før-definerede egenrum. 
$$
P=
\begin{bmatrix}
-2 & -1 & 1/2 \\
1 & 0 & -1/2 \\
0 & 1 & 1
\end{bmatrix}
$$
Vi finder således den diagonaliserede matrix. De første to søjler består af egenrummet for $\lambda_{1}=1$ og ligeledes for egenværdien $\lambda_{2}=(-2)$
**Udregn evt. P^-1**
$$
\begin{align}
\mathbf{P}^{-1}\mathbf{MP}
=
\begin{bmatrix}
\lambda_{1} & 0 & 0 \\
0 & \lambda_{1} & 0 \\
0 & 0 & \lambda_{2}
\end{bmatrix} \\
= \begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & -2
\end{bmatrix}
\end{align}
$$
Vi kan tjekke efter, og validere at resultatet er korrekt ved at udregne den diagonaliserede matrice:
$$
\begin{align}
\mathbf{D}=P^{-1}MP
=
\begin{bmatrix}
1 & 3 & 1 \\
-2 & -4 & -1 \\
2 & 4 & 2
\end{bmatrix}
\begin{bmatrix}
-2 & -6 & -3 \\
3 & 7 & 3 \\
-6 & -12 & -5
\end{bmatrix}
\begin{bmatrix}
-2 & -1 & 1/2 \\
1 & 0 & -1/2 \\
0 & 1 & 1
\end{bmatrix}
=\\\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & -2
\end{bmatrix}
\end{align}
$$
## e)


For diagonalisérbare matricer gælder det for potenser af matricen:
$$
\begin{align}
\mathbf{A}   & = \mathbf{PDP}^{-1} \\
\mathbf{A}^2 & = \mathbf{PD}^2\mathbf{P}^{-1} \\
\mathbf{A}^3 & = \mathbf{PD}^3\mathbf{P}^{-1} \\
 & \vdots \\
\mathbf{A}^k & =\mathbf{PD}^k\mathbf{P}^{-1}
\end{align}
$$
Vi skal altså kun bekymre os om at finde et generelt udtryk for matricen 
$$
\mathbf{D}=
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & -2
\end{bmatrix}
$$
Vi udtrykker $\mathbf{D}^n$
$$
\mathbf{D}^n=
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & (-2)^n
\end{bmatrix}
$$
Vi kan altså bestemme et generelt udtryk for $\mathbf{M}^n$ som:
$$
M^n = 
\begin{bmatrix}
-2 & -1 & 1/2 \\
1 & 0 & -1/2 \\
0 & 1 & 1
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & (-2)^n
\end{bmatrix}
\begin{bmatrix}
1 & 3 & 1 \\
-2 & -4 & -1 \\
2 & 4 & 2
\end{bmatrix}
$$
**ELLERS UDREGN**
$$
\left[\begin{array}{ccc}
 1.0 \left(-2\right)^{n} & - 2.0+ 2.0 \left(-2\right)^{n} & - 1.0+ 1.0 \left(-2\right)^{n} 
\\
  1.0- 1.0 \left(-2\right)^{n} &  3.0- 2.0 \left(-2\right)^{n} &  1.0- 1.0 \left(-2\right)^{n} 
\\
 -2+2 \left(-2\right)^{n} & -4+4 \left(-2\right)^{n} & -1+2 \left(-2\right)^{n} 
\end{array}\right]
$$
**EVT VALIDER FOR 1,2,3,4,5**

# 3

## a)

Vi kan opskrive alle målingerne i et ligningssystem $\mathbf{Ax}=\mathbf{b}$
$$
\begin{cases}
a\cdot 2008+b=34.564\\
a\cdot 2009+b=35.104\\
a\cdot 2010+b=35.481\\
a\cdot 2011+b=36.891\\
a\cdot 2012+b=37.331\\
a\cdot 2013+b=38.061\\
a\cdot 2016+b=39.071\\
a\cdot 2018+b=39.345\\
a\cdot 2020+b=40.568\\
a\cdot 2021+b=41.544
\end{cases}
$$
hvor
$$
\mathbf{A}=
\begin{bmatrix}
2008 & 1 \\
2009 & 1 \\
2010 & 1 \\
2011 & 1 \\
2012 & 1 \\
2013 & 1 \\
2016 & 1 \\
2018 & 1 \\
2020 & 1 \\
2021 & 1
\end{bmatrix}
\space\space\space
,
\space\space\space
\mathbf{x}=\begin{pmatrix}
a \\
b
\end{pmatrix}
$$
og
$$
\mathbf{b}=
\begin{pmatrix}
34.564\\
35.104\\
35.481\\
36.891\\
37.331\\
38.061\\
39.071\\
39.345\\
40.568\\
41.544
\end{pmatrix}
$$
Den bedste tilnærmede løsning til ligningen er
$$
\overline{\mathbf{x}}=\begin{pmatrix}
\overline{a} \\
\overline{b}
\end{pmatrix}
=(\mathbf{A}^T\mathbf{A})^{-1}\mathbf{A}^T\mathbf{b}
$$

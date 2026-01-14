---
tags:
  - LINALG
  - Math
---
# Lineære systemer

## Definition

Er på formen
$a_{1}x_{1}+a_{2}x_{2} + \dots + a_{n}x_{n}=b$

## Lige store koefficienter og totalmatrix


$a_{1}x_{1}+a_{2}x_{2} + \dots + a_{n}x_{n}=c_{1}$
$b_{1}x_{1}+b_{2}x_{2} + \dots + b_{n}x_{n}=c_{2}$

Skrives op i [[LINALG/Matricer/Matricer|matrice]], vi fjerner konstanterne

$$
\left[\begin{array}{ccc|c}
a_{1} &  \dots & a_{n} & c_{1}\\
b_{1} & \dots & b_{n} & c_{2} \\
\end{array}\right]
$$
![[Pasted image 20250429175248.png]]

### Eksempel
![[Pasted image 20250429201725.png]]
![[Pasted image 20250429201738.png]]

[[Rækkeoperationer]]
## Alternativ notation
$$
Ax = 
\left[\begin{array}{ccc}
a_{11} &  \dots &a_{1n} \\
\vdots & \ddots  & \vdots \\
a_{m1} & \dots & a_{mn} \\
\end{array}\right]

\begin{bmatrix}
x_{1} \\
\vdots \\
x_{n} \\
\end{bmatrix}
=
\left[\begin{array}{c}
a_{11}x_{1}+a_{12}x_{2}+\dots+a_{1n}x_{n} \\
\vdots \\
a_{m1}x_{1}+a_{m2}x_{2}+\dots+a_{mn}x_{n} \\
\end{array}\right]
$$
Vi vil skrive det som $Ax = b$, hvor vi tænker på at koefficientmatricen $A$ “ganges” med vektoren $x$ (tallene $x_1, . . . , x_n$ skrevet som en vektor) og hvor $b$ er højresiden skrevet som en vektor.

### Eksempel
![[Pasted image 20250429201939.png]]

## Theorem

### 5.8 Cramer’s formel
[[Determinant]]
![[Pasted image 20250519144351.png]]

### Eksempel
![[Pasted image 20250519144622.png]]
## Eksempel

### 1

![[Pasted image 20250615120451.png]]

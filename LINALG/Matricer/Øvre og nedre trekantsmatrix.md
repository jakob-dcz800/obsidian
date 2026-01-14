---
tags:
  - Math
  - Matrices
  - LINALG
---
# Øvre og nedre trekantsmatrix

## Definition

En $m × n$ [[LINALG/Matricer/Matricer|matrix]] $A$ er en **øvre trekantsmatrix** hvis $a_{ij} = 0$ for $i > j$. 
Hvis $m = n$ ser en øvre trekantsmatrix ud som følger

$$
A = \begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n}\\
0 & a_{22} & \cdots & a_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
0 & 0 & \cdots & a_{nn}
\end{bmatrix}
$$
(Alle elementer under diagonalen skal være 0)
En $m × n$ matrix $A$ er en **nedre trekantsmatrix** hvis $A^T$ er en øvre trekantsmatrix

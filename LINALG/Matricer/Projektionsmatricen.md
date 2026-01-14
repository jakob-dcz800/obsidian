---
tags:
  - Matrices
  - Math
  - LINALG
---
# Projektionsmatricen

Lad $0 \not= \mathbb{R}^n$ og sæt $\mathcal{U} = \text{span}\set{\mathbf{u}}$. 
Det er geometrisk klart, at
$$
\text{proj }_{\mathcal{U}}(-), \space\text{comp }_{\mathcal{U}}(-), \space\text{refl }_{\mathcal{U}}(-): \mathbb{R}^n \to \mathbb{R}^n
$$
er [[Lineære transformationer#Definition|lineære transformationer]]. Derfor findes $n \times n$ [[LINALG/Matricer/Matricer]].

$\mathbf{P}$ – projektionsmatricen for $\mathcal{U}$
$\mathbf{C}$ – komponentmatricen for $\mathcal{U}$
$\mathbf{R}$ – spejlingsmatricen for $\mathcal{U}$

![[Pasted image 20250511170545.png]]
## Definition

![[Pasted image 20250511170037.png]]
![[Pasted image 20250514103924.png]]

## Eksempel

### 1 Bestemmelse af projektionsmatrix

![[Pasted image 20250511170623.png]]

[[Underrum]]
[[Underrum#Begreber|Begreber]]
[[Transponering]]

### 2 Bestemmelse af projektionsmatrix
![[Pasted image 20250513221014.png]]

Vi har brug for en [[Ortonormale baser|ortonormal basis]].

![[Pasted image 20250513221057.png]]

Matricen projicerer altså vektorer ned i underrummet U.

[[Span]]
[[Norm]]
[[Ortonormale baser]]

Øvelsen er koblet til, og underrummet er den grå plan i:
![[Ortogonal projektion#3 Ortogonal projektion på en plan]]
### 3 Øvelse
![[Pasted image 20250513221127.png]]

U er x, y planen.
$$
\text{proj }_{\mathcal{U}}\begin{pmatrix}
a \\
b \\
c
\end{pmatrix}
=
P
\begin{pmatrix}
a \\
b \\
c
\end{pmatrix}
=\begin{pmatrix}
a \\
b \\
0
\end{pmatrix}
$$

---
tags:
  - Vectors
  - Math
  - LINALG
---
# Vektorrum

## Vektorrummet $\Bbb{R}^n$
Mængden af vektorer med n koordinator, R^3 er med 3 koordinator osv...
R^n er sættet og er et vektorrum. 
Der gælder pæne regneregler for vektorrum.
Lad $\Bbb{R}^{n}$ være mængden af alle (søjle)vektorer. Eksponenten afgør antallet af rækker i søjlen.
$$
u=
\begin{bmatrix}
u_{1} \\
\vdots \\
u_{n}
\end{bmatrix}
\space\space
\text{ for }
\space\space
u_{1},\dots,u_{n}\in\Bbb{R}
$$

## Vektoraddition

$$
u \pm v=
\begin{bmatrix}
u_{1} \\
\vdots \\
u_{n}
\end{bmatrix}
+
\begin{bmatrix}
v_{1} \\
\vdots \\
v_{n}
\end{bmatrix}
=
\begin{bmatrix}
u_{1}\pm v_{1} \\
\vdots \\
u_{n} \pm v_{n}
\end{bmatrix}
$$
![[Pasted image 20250504171137.png]]
## Skalarmultiplikation

$$
\mathbf{s}u=\mathbf{s}
\begin{bmatrix}
u_{1} \\
\vdots \\
u_{n}
\end{bmatrix}
=
\begin{bmatrix}
\mathbf{s}u_{1} \\
\vdots \\
\mathbf{s} u_{n}
\end{bmatrix}
$$
![[Pasted image 20250504171149.png]]

## Regneregler

For alle vektorer $u, v, w = \Bbb{R}^n$ og alle skalarer $s, t \in \Bbb{R}$

$$
\begin{gather}
u+v=v+u \\
(u + v) + w = u + (v + w) \\
v + 0 = v \\
v+(-v)=0 \\
s(u + v) = su+sv \\
(s+t)v=sv+tv \\
s(tv)=(st)v \\
1v=v
\end{gather}
$$

## Abstrakte vektorrum

En mængde $V$ hvis elementer vi omtaler "vektorer" med
- Vektoraddition: $V \times V\to V, (u, v)\to u+v$
- Skalarmultiplikation: $\Bbb{R}\times V\to V, (s, u)\to su$

Vi vil udelukkende fokusere på vektorrummet $V=\Bbb{R}^n$
Men alt hvad vi skal lære om $\Bbb{R}^n$ (fx [[Underrum]], [[Span]], [[Lineær uafhængighed|lineær uafhængighed]], [[Baser]], ...) gælder også i et abstrakt vektorrum $V$.
### Theorem 3.1
Mængden $V=\Bbb{R}^n$ er et (reelt) vektorrum

#### Eksempel
Alle disse er vektorrum:
$$
\begin{matrix}
V = \Bbb{R}^{m\times n}=\set{m\times n \text{ matricer med indgange fra }\Bbb{R}} \\
V = \mathbf{F}(-\infty, \infty) = \set{\text{funktioner }f:\Bbb{R} \to \Bbb{R}} \\
V = \mathbf{P}_{n}= \set{\text{polynomier }p(t)=a_{0}+a_{1}t+\dots+a_{n}t^{n}\text{ hvor }a_{i}\in\Bbb{R}}
\end{matrix}
$$
# Matrixmultiplikation


## Definition

$$
A = \begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n}\\
a_{21} & a_{22} & \cdots & a_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
+

\begin{bmatrix}
b_{11} & b_{12} & \cdots & b_{1n}\\
b_{21} & b_{22} & \cdots & b_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
b_{m1} & b_{m2} & \cdots & b_{mn}
\end{bmatrix}
=

\begin{bmatrix}
c_{11} & c_{12} & \cdots & c_{1n}\\
c_{21} & c_{22} & \cdots & c_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
c_{m1} & c_{m2} & \cdots & c_{mn}
\end{bmatrix}
$$

Aka.

$$
c_{ij} = \sum^{n}_{k=1}=a_{ik}b_{kj}=a_{i1}b_{1j}+\dots+a_{in}b_{nj}
$$
ij’te element i AB = i’te række i A “gange” j’te søjle i B
**Bemærk, at matrix gange vektor er et specialtilfælde (p = 1).**
## Regneregler

**Gælder**
Associativitet: $A(BC) = (AB)C$ 
Distributivitet: $A(B+C) = AB + AC$

**Gælder ikke generelt**
Kommunikativitet: $AB=BA$
$AB = 0 \Rightarrow A = 0$ eller $B = 0$

![[Excalidraw/matrixmultiplikation]]

### Eksempel

![[Pasted image 20250429202646.png]]

# Underrum

Et underrum er en pæn delmængde af R^n. aka. skal følge definitionen:
## Definition 3.2
En delmængde $U\subseteq \Bbb{R}^n$ kaldes et underrum såfremt:
- $0 \in U$
- For alle $u,v \in U$ gælder $u + v \in U$ (forbliver i underrummet)
- For alle $s \in \Bbb{R}$ og $u \in U$ gælder $su \in U$ (forbliver i underrummet)

## Illustration

![[Pasted image 20250504173251.png]]
Sjældent at opgaver skal vises er et udnerrum, opgaver er som regel inforstået med, at de er!
### Eksempel
Følgende delmængde af $\Bbb{R}^4$ er et underrum:
$$
U = \set{(x_{1}, x_{2}, x_{3}, x_{4}) \in \Bbb{R}^4 \mid x_{1}+x_{2} = 0 \text{ og }x_{2}+x_{3}+x_{4}= 0}
$$
En måde at indse dette på er ved at bemærke at:
$$
\mathbf{x}= \begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3} \\
x_{4}
\end{bmatrix}
\in U \iff
\begin{bmatrix}
1 & 1 & 0 & 0 \\
0 & 1 & 1 & 1
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3} \\
x_{4}
\end{bmatrix}
=
\begin{bmatrix}
0 \\
0
\end{bmatrix}
\iff
\mathbf{Ax}=
\mathbf{0}
$$
![[Pasted image 20250504173807.png]]

![[Pasted image 20250505134042.png]]

## Begreber

$\text{null A}$ [[Nulrum]]
$\text{col A}$: [[Søjlerum]]
$\text{row A}$: [[Rækkerum]]
$\text{nullity A}$: nullity = dimensionen af nulrummet = dimensionen af ortogonalkomplementet til rækkerummet
$\text{proj }_{\mathcal{U}}(\mathbf{v})$: 

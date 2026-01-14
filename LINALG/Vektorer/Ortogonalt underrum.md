---
tags:
  - Math
  - Vectors
  - Matrices
  - LINALG
---
# Ortogonalt underrum

Det ortogonale underrum er
## Definition

![[Pasted image 20250513210127.png]]

## Ortogonalt komplement
![[Pasted image 20250513213601.png]]
[[Ortogonale vektorer]]
Vi har ét underrum

Komplementet er ALLE vektorer i $\mathbb{R}^n$ som er vinkelret på $\mathcal{U}$.
Vi har set, at der for enhver matrix $\mathbf{A}$ gælder:
$$
(\text{null }\mathbf{A})^{\perp}=\text{null A}
$$
Og derfor og derfor vil $\text{null A} ⊆ (\text{row A})^⊥$
Det følger at:
$$
\begin{matrix}
(\text{col A})^{\perp}=\text{null A}^{\text{T}}\\
(\text{null A})^{\perp}=\text{col A}^{\text{T}}
\end{matrix}
$$

![[#4.10]]

Bemærkning:
For enhver m × n matrix A gælder
$$
\text{rank A}+\text{nullity A} = n
\space\space\space
\text{dvs.}
\space\space\space
\text{dim}(\text{row A})+\text{dim}((\text{row A})^\perp) = n
$$
Vi skal senere se, at der for ethvert underrum $\mathcal{U}$ af $\mathbb{R}^n$ gælder
$$
\text{dim }\mathcal{U}+\text{dim }\mathcal{U}^\perp = n
$$

## Theorem

### 4.8
![[Pasted image 20250513213235.png]]

For at tjekke ortogonalitet af to underrum, er det nok at tjekke om de to frembringersæt (span-sæt) er ortogonale på hinanden.
Det kan også være basen som vi har fat i.

### 4.9
![[Pasted image 20250513213550.png]]

2. de to underrum har kun nulvektoren til fælles da de er ortogonale på hinanden.
### 4.10
![[Pasted image 20250513214315.png]]

Hvis den første er sand, følger alle de andre sætninger
Nulrummet ligger inde i ortogonalkomplementet for A
nulrummet er præcist ortogonalkomplementet for rækkerummet er nulrummet

![[Pasted image 20250514094506.png]]

nullity = dimensionen af nulrummet = dimensionen af ortogonalkomplementet til rækkerummet
n = antal søjler
### 4.11 Dimension af ortogonalt komplement
![[Pasted image 20250513215845.png]]

Med ord: Hvis man samler baserne for $U$ og $U^⊥$ så fås en basis for $\mathbb{R}^n$


## Ortogonalitet af nulrum og rækkerum

![[Pasted image 20250513213804.png]]

[[Nulrum]]
[[Rækkerum]]
[[Søjlerum]]
[[Ortogonale matricer]]

Med andre ord: 
## Eksempel

### 1 Ortogonale underrum
[[Underrum]]
[[Ortogonale vektorer]]

![[Pasted image 20250513210150.png]]
![[Pasted image 20250513213025.png]]
### 2 Underrum som *ikke* er ortogonale

![[Pasted image 20250513213015.png]]
![[Pasted image 20250513213037.png]]

### 3 Underrum som *ikke* er ortogonale

![[Pasted image 20250513213123.png]]
![[Pasted image 20250513213147.png]]

Det ligner at de er vinkelrette.
(1,0,0) ligger dog i begge underrum
To vinkelrette underrum kan kun have nulvektoren til fælles
### 4 Ortogonale "span-underrum"

![[Pasted image 20250513213417.png]]
![[Pasted image 20250513213428.png]]

Eksemplet illustrerer følgende generelle fænomen: [[#Ortogonalitet af nulrum og rækkerum]]
[[#Ortogonalt komplement]]
[[#4.9]]
### 5 Ortogonalt komplement

[[Underrum]]

![[Pasted image 20250513213930.png]]
![[Pasted image 20250513214123.png]]

w er planen til højre
v er ikke det ortogonale komplement, da det består af ALLE ortogonale vektorer på U
w er altså vinkelret på den sorte linje U
De er altså ortogonal komplement for hinanden (w og u)
Underrum skal igennem orego
### 6 Basis for ortogonalt komplement
![[Pasted image 20250513215053.png]]

Basis er kompaktificering af underrummet.
Vi kan ikke beskrive en plan med alle dets vektorer. 
Basen beskriver planen for den kan give os alle vektorer i planen via. lineær transformering.

![[Pasted image 20250513215113.png]]

(brøken, altså basen har ganget den frie variabel med 2)
Ortogonalkomplementet for v er altså en ret linje. 1 dimension + 3 dimensioner giver R^4

[[Gauss elimination#Gauss-Jordan elimination|Gauss-Jordan]]
### 7 Øvelse
![[Pasted image 20250513215233.png]]

vi kigger på [[#4.10]]
A er nulrummet af $\mathcal{U}$

[[Nulrum]]
[[Baser]]

### 8 Baser for ortogonale komplementer
![[Pasted image 20250513220037.png]]

Påstanden er fra eksempel [[#6 Basis for ortogonalt komplement]]

![[Pasted image 20250513220058.png]]



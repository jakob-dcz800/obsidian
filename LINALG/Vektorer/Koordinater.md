---
tags:
  - Math
---
# Koordinater

Vi vil gerne ud fra en vektor bestemme, hvordan kommer vi frem til vektoren?

![[Pasted image 20250506212516.png]]

Forklaring
Koordinaterne for vektoren $v$ med hensyn til basen $\mathcal{B}$ er givet ved $[\mathbf{v}]_{\mathcal{B}} = \begin{pmatrix}x_{1} \\ \vdots \\ x_{k} \end{pmatrix}$
Det er altså $x_{1},\dots,x_{k}$ fra formen af vektoren: $\mathbf{v}=x_{1}b_{1}+\dots+x_{k}b_{k}$
Hvor meget skal vi gange basisvektorerne med for at få $\mathbf{v}$ lavet?
For langt skal vi gå i retning af $b_{1}$ osv. for at komme til vektoren 

Hvorfor findes der entydigt bestemte tal $x_1, ..., x_k$?
Jo, $v$ ligger i spannet for $b_1, ..., b_k$

![[Pasted image 20250507111241.png]]

## Eksempel

### 1
![[Pasted image 20250506212545.png]]

### 2
![[Pasted image 20250506212622.png]]

De tre vektorer $b$ ER en basis da de er lineært uafhængige ([[Baser#3.10|3.10]])
Vi ser at de er lineært uafhængige da vi får $I$ efter [[Gauss elimination#Gauss-Jordan elimination|Gauss-Jordan elimination]]

Vi vil altså finde [[Span#Eksempel på linearkombination|linearkombinationen]] af sættet $\mathcal{B}$ sådan at vi får $\mathbf{v}$
Vi har fundet en basis uden et [[Underrum|underrum]]

![[Pasted image 20250506212631.png]]

Forklaring:
Vi får koordinaterne: $[\mathbf{v}]_{\mathcal{B}}$

### 3
![[Pasted image 20250506212645.png]]

Forklaring:

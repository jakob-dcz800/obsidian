# Blokmatricer

Man kan opdele en stor [[LINALG Lineær algebra/Matricer/Matricer|matrix]] i mindre dele eller blokke
Det er smart (hvis fx der er mange 0’er i matricen) – så bruges meget **mindre lagerplads**
### Eksempel
Her ganger vi matricen med sig selv. [[LINALG Lineær algebra/Matricer/Matrixmultiplikation|Multiplikationen]] kan omskrives på følgende måde:

![[Pasted image 20250429203746.png]]

## Blokmultiplikation

### Eksempel
Hvis blokkenes størrelser passer sammen gælder. 
Her er der **delelementer** i matricen og ikke nødvendigvis elementer (som tal). 
Blokkenes størrelser skal passe sammen. 

$$
\begin{bmatrix}
A_{11} & A_{12}\\
A_{21} & A_{22}
\end{bmatrix}

\begin{bmatrix}
B_{11} & B_{12}\\
B_{21} & B_{22}
\end{bmatrix}
=
\begin{bmatrix}
C_{11} & C_{12}\\
C_{21} & C_{22}
\end{bmatrix}
$$
Hvor
$$
\begin{matrix}
C_{11} = A_{11}B_{11} + A_{12}B_{21}\\
C_{21} = A_{21}B_{11} + A_{22}B_{21}\\
C_{12} = A_{11}B_{12} + A_{12}B_{22}\\
C_{22} = A_{21}B_{12} + A_{22}B_{22}\\
\end{matrix}
$$

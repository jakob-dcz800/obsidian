---
tags:
  - Matrices
  - Math
  - LINALG
---
# Rækkeechelonform

En matrix er på *rækkeechelonform* hvis der gælder følgende: 
1. Alle **nulrækker** findes i **bunden** af matricen.
2. Det **første element**, forskellig fra 0, i en given **ikke-nulrække**, findes til højre for det tilsvarende element i rækken lige over. 
## Pivotelement


Det første element, forskellig fra 0, i en given ikke-nulrække kaldes et **pivotelement** og den række og søjle det står i kaldes en pivotrække og pivotsøjle.
$$
\begin{bmatrix}
0 & \textcolor{red}{1} & 0 & 0\\
0 & 0 & \textcolor{red}{1} & 0\\
0 & 0 & 0 & 0
\end{bmatrix}
$$
## Reduceret rækkeechelonform

En matrix er på **reduceret rækkeechelonform** hvis 
1. den er på rækkeechelonform
2. det første element, forskellig fra 0, i en given ikke-nulrække er lig med 1 og alle andre elementer i den tilsvarende søjle er lig med 0

![[Pasted image 20250429181348.png]]

## Bestemmelse af samtlige løsninger

![[Pasted image 20250507120040.png]]

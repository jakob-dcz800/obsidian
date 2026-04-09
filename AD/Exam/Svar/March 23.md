# Multiple-choice
## 1 Mergesort og sammenligninger

![[Pasted image 20260406173618.png]]

❌ 5: 7 sammenligninger.
Korrekt svar: 3: 5 sammenligninger
![[Pasted image 20260406174433.png|264]]
## 2 Mergesort

![[Pasted image 20260406173638.png]]

Det er ikke 2 - hvorfor?
Det er 4.
![[Pasted image 20260406175041.png|436]]
## 3 Korteste-veje træ

![[Pasted image 20260406173653.png]]
![[Pasted image 20260406173702.png]]

1: $G′$ forbinder kun s med de knuder knuder i $V$ hvortil der findes en vej i $G$. 
2: Der er kun udgående kanter fra s fordi træet ikke har nogen cykler. 
3: $G′$ er et træ, og derfor er antal kanter lig med antal knuder minus 1. 
4, 5: En lav vægt er ikke en garanti for at være med i en korteste vej fra $s$ - for eksempel kan visse kanter ikke nås fra $s$.
## 4 Korteste veje

![[Pasted image 20260406173726.png]]

![[Pasted image 20260406180916.png|235]]

✅ **1, 3, 9, 11, 7**
## 5 Mindste udspændte træ

![[Pasted image 20260406173745.png]]

![[Pasted image 20260406181113.png|343]]

✅ **2, 1, 4, 9, 10**
## 6 Rød-sorte søgetræer

![[Pasted image 20260406173758.png]]
![[Pasted image 20260406173814.png]]

✅ **1, den overholder invarianten**
Svar: RB-Insert finder det rette sted i træet til nøglen 9, som det højre barn under knude 8. Knuden farves rød og derefter kaldes RB-Insert-Fixup, men den terminerer uden at ændre noget fordi forældreknuden 8 er sort.
## 7 Køretid for rød-sorte søgetræer

![[Pasted image 20260406173830.png]]

✅ 1: umiddelbart ikke, søgning er $O(\lg n)$
✅ 2: ja
❌ 3: nej
✅ 4: ja
5: nej
6: nej
![[Pasted image 20260407161948.png]]
## 8 Amortiseret analyse 2.5p

![[Pasted image 20260406173847.png]]
![[Pasted image 20260406173856.png]]

✅ **1, 4**
Mangler 6
$\Phi_i = 2 · num_i −size_i$ , hvor $num_i = i$ og $size_i ≥ 1$ er den aktuelle kapacitet. 
Vi har altid $\Phi_i ≤ i/2$, så $\Phi_i = O(i)$, men lige efter en tabeludvidelse har vi $\Phi_i ≤ 2$, 
dvs. det gælder ikke at $\Phi_i = Ω(i)$. 
Lige efter en tabeludvidelse har vi $\Phi_i < \Phi_{i−1}$. 
Potentialfunktionen er defineret så den er ikke-negativ, og den er positiv fra første skridt og fremefter.
## 9 Del og hersk

![[Pasted image 20260406173910.png]]

1: den har theta n^2
2: n^2 lg n
3: n^2
4: n^3
5: nej, højere pga. n-1
6: den er sgu nok n^2

✅ **Derfor: 1, 3, 6**
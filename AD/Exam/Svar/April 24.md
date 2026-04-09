# Multiple-choice 52p
## 1 Sortering 4p

![[Pasted image 20260406105043.png]]

✅ **6: merge sort kaldes tre gange på en tredjedel af n**
![[Pasted image 20260406110128.png]]
	
## 2 Rekursionsligninger 4p

![[Pasted image 20260406105106.png]]
![[Pasted image 20260406105118.png]]

Skal være **O(n^2)**

1: case 1 - $\Theta(n^{2})$ ✅ 
2: case 2 - $\Theta(n^{2}\log n)$ ❌
3: case 3 - $\Theta(n^{\log_{2}(3)})$✅
4: case 1 - $\Theta(n)$ ✅
5: case 1 - $\Theta(n)$ ✅
6: den tager noget i retning af $2^{n}$❌
## 3 Nedre grænser for sortering 1p

![[Pasted image 20260406105139.png]]

1: ❌ - gættede forkert
2: ❌ - gættede forkert
3: ✅
4: ✅
5: ❌
6: ❌
![[Pasted image 20260406111527.png]]
## 4 Løkkeinvarianter 4p

![[Pasted image 20260406105157.png]]
![[Pasted image 20260406105207.png]]

1: nej, hvis A[i] < 1, bliver r mindre end s
2: nej, $A[i]$ kan være negativ
✅ 3: ja, $A[i]^{2}$ kan aldrig være negativ
✅ 4: ja, $i$ er et stigende tal
5: nej, sumtegnet skal gå mod i, ikke n
✅ 6: ja
✅ 7: ja
## 5 Invarianter for dynamiske tabeller 3p

![[Pasted image 20260406105230.png]]
> s. 469 i CLRS

1: nej, størrelsen varierer
2: nej, størrelsen (kapacitet), er større en antallet deri
❌ 3: nej, $2 \cdot T.num$ kan godt komme under $½T.size$ 
	Da vi ikke har `TABLE-DELETE` er dette sandt. Det ville være forkert hvis der var `TABLE-DELETE`
4: nej, disse er næste aldrig ens
✅ 5: ja, $T.size$ er altid større end $T.num$
✅ 6: ja, $T.size$ er altid større end $T.num$

![[Pasted image 20260406135943.png]]
## 6 Amortiseret analyse 1p

![[Pasted image 20260406105250.png]]
![[Pasted image 20260406105302.png]]

❌ 1: en dollar lægges i, når et element tilføjes - nej
❌ 4: det gør den vel? - nej
✅ 6: når værdien af potentialefunktionen bliver lig med size, fordobles size

Udsagn 1-4 er falske fordi effekten på potentialet af en operation afhænger af $α(T)$, med en mindskning i det ene tilfælde og en øgning i det andet tilfælde.
Udsagn 5 er sandt da $2T.num ≥ T.size ≥ T.num$. 
Udsagn 6 er sandt da $2(T.num − T.size/2) ≤ 2(T.size − T.size/2) = T.size$
## 7 Fibonaccihobe 4p

![[Pasted image 20260406105321.png]]

✅ **1, 4, 5, 6**
## 8 Tidskompleksitet for Fibonaccihobe -2

![[Pasted image 20260406105342.png]]
![[Pasted image 20260406105351.png]]

❌ **2, 4**
Rigtig svar: 1, 3
![[Pasted image 20260406113415.png]]
## 9 Stavudskæring 4p

![[Pasted image 20260406105405.png]]

1: slutter på 48 som ikke kan laves af de forudgående tal inden for n=6
2: slutter på 48 som ikke kan laves af de forudgående tal inden for n=6
3: slutter på 49 som ikke har nummer 4 i rækken
✅ **4: det må være denne, da maximum er 49, som har nummer 6 i rækken**
## 10 Paradigmer 4p

![[Pasted image 20260406105425.png]]

✅ **1**, der vælges ikke imellem inputs
## 11 Huffman-koder 4p

![[Pasted image 20260406105451.png]]

nej: 5
✅ **ja 4**
![[Pasted image 20260406114116.png]]
## 12 Rød-sorte søgetræer 3p

![[Pasted image 20260406105508.png]]

Skal være sorte børn af røde knuder.
1: nej, den ville skulle være til højre for roden men er for lille
✅ 2: ja
3: nej
✅ 4: ja
❌ 5: ja - forkert pga. den skal selvfølgelig være sort - **LÆS SVARET ORDENTLIGT**
✅ 6: ja
## 13 Rotationer i rød-sorte søgetræer 4p

![[Pasted image 20260406105525.png]]
![[Pasted image 20260406105534.png]]

Gæt på hvordan det ser ud (ikke omfarvet):
![[Pasted image 20260406122240.png]]

✅ **Derfor 2, 4**
## 14 Mindste udspændende træ 4p

![[Pasted image 20260406105557.png]]
![[Pasted image 20260406115219.png|333]]

✅ **1, 3, 5, 8, 9**
## 15 Snit og sikre kanter 3p

![[Pasted image 20260406105613.png]]

✅ **1, 2, 4**
Mangler 6: 
![[Pasted image 20260406132617.png|302]]
## 16 Kruskal’s algoritme 4p

![[Pasted image 20260406105631.png]]
![[Pasted image 20260406105644.png]]

✅ **2**, da kanterne vælges efter sorteret rækkefølge.
## 17 Korteste veje 4p

![[Pasted image 20260406105658.png]]
![[Pasted image 20260406105707.png]]
Gæt:
![[Pasted image 20260406132805.png|270]]

✅ **1, 2, 4, 6, 8**
❌ Mangler 9!
> Kør ikke Kruskal, men Dijkstra i stedet
> Derfor vil 8 og 9 fremgå, da begge veje er lige lange (19 lang)


## 18 Valg af algoritmer og datastrukturer -1p

![[Pasted image 20260406105725.png]]

nej: 1, 5
❌ ja: 2
måske: 3, 4
Korrekte svar: **merge sort**

![[Pasted image 20260406120134.png]]
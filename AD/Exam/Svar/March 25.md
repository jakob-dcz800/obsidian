# Multiple choice 36p

## 1 Rekursionsligninger 4p
[[Master theorem]]
![[Pasted image 20260405142707.png]]

1. n log n (case 2)
2. n log n (case 3)
3. $n^{\log_{3}(4)}$ 
4. n
5. nrd2
6. n log n

✅ gæt: **1, 2, 6**
## 2 Rekursive algoritmer 4p

![[Pasted image 20260405142719.png]]

$\Theta (n)$ dominerer $\Theta (1)$
Kaldestørrelsen er $n - 1$.
✅ **Derfor 5**

![[Pasted image 20260405144743.png]]
## 3 Invarianter 4p

![[Pasted image 20260405142731.png]]

Algoritmen returnerer `TRUE` hvis summen af to tal fra hver deres liste er lig med k.
2: hvis summen $A[i']+A[j'] = k$ afbrydes algoritmen og den stopper. Derfor er det modsatte tilfældet. 4 er heller ikke rigtig, da i og j godt kan være.
Vi går med 4, da i 2'eren går j mod i og ikke n. 
✅Gæt: **4**
![[Pasted image 20260405150047.png]]

## 4 Enigma 

![[Pasted image 20260405142743.png]]


## 5 Arbejde og spand -1

![[Pasted image 20260405142755.png]]

❌ 1: n knuder berøres, og antallet af kald til algoritmen afhænger af den længste sti med højde h
Det er selvfølgelig **4**, af de årsager skitseret ovenfor
## 6 Parallelle algoritmer 4p

![[Pasted image 20260405142806.png]]
$$
\begin{align}
T_{P} & \leq T_{1}/P+T_{\infty} \\
& = \Theta(n \log n)/P+\Theta(n) \\
& = \Theta(n \log n/P+n)
\end{align}
$$

1: sandt, men løst
2: sandt, log n går ud med sig selv sådan at det er n + n
3: falsk
4: falsk, n er fortsat til stede
5: falsk, n er fortsat til stede
✅ Derfor **1, 2**
## 7 Invarianter for dynamiske tabeller

![[Pasted image 20260405142816.png]]
## 8 Tidskompleksitet for Fibonaccihobe 1p

![[Pasted image 20260405142826.png]]

❌ Gæt: 1, **5**
Korrekt: 3, 5 
![[Pasted image 20260405155116.png]]
## 9 Stavudskæring -1p

![[Pasted image 20260405142839.png]]
![[Pasted image 20260405142847.png]]

$r$ er den akkumulerede værdi af stængerne i deres udskæringer.
$s$ er stavlængderne
❌ Vi gætter på at der er 2 stave, hver med sin længde og værdi: $p=[3, 4]$
✅ Længderne fremgår af $s$. 
s[i] indicates where to make the first cut in a rod of length i - derfor starter vi fra toppen.
	s[8] siger at vi skal starte med en stang af længde 1 (vi går ned med 1: 7)
	s[7] siger at den næste stang også har længde 1 (ned med 1: 6)
	s[6] siger at den næste stang har længde 3 (ned med 3: 3)
	s[3] siger at den sidste stang har længde 3 (ned med 3: 0)
Dvs. fire stænger totalt.
![[Pasted image 20260405163341.png]]
## 10 Længste fælles delsekvens 4p

![[Pasted image 20260405142859.png]]

1 nej X skal være skrå
2 nej, værdien af Y er max af diagonalen, oppe, og til venstre
3 ja
4 nej X skal være skrå
## 11 Huffman koder 4p

![[Pasted image 20260405142908.png]]

✅ **gætter på 1:**
![[Pasted image 20260405214051.png|299]]
![[Pasted image 20260405214114.png]]
## 12 Matrixkæde-multiplikation 4p

![[Pasted image 20260405142919.png]]

nej: 3, 4, 1, 5
✅ **ja: 2**
Process: 
- Kig på højre hjørne $p[1, 6]$, split hér
- Gå så ned ad stien $p[1, j]$ og split når tallet ændres.
- Hver gang værdien i $p[i, j]$ skifter, så split og gå rekursivt ned af træet
- Udeluk muligheder en efter en.
## 13 Paradigmer 4p

![[Pasted image 20260405142931.png]]

✅ **1**
## 14 Rotationer i rød-sorte søgetræer

![[Pasted image 20260405142944.png]]
## 15 Korteste veje

![[Pasted image 20260405142955.png]]
## 16 Mindste udspændende træ 4p

![[Pasted image 20260405143007.png]]

✅ **1, 2, 3, 5, 9**

![[Pasted image 20260405221436.png]]
## 17 Grafalgoritmer -1

![[Pasted image 20260405143017.png]]

❌ **2 - for den medtager negative vægte**
![[Pasted image 20260405221652.png]]
## 18 Konvekse hylstre

![[Pasted image 20260405143026.png]]

✅ **3: Hjørnerne i det konvekse hylster er en del af den endelige mængde af punkter**
❌ 5: usikker, men algoritmerne tager udgangspunkt i et vilkårlig 0,0 som de selv definerer (som regel laveste punkt) 

mangler: **1**
![[Pasted image 20260405222126.png]]

# Skriftlige opgaver

## 19 Rekursion og induktionsbeviser

## 20 Lokalefordeling

![[Pasted image 20260407113938.png]]
![[Pasted image 20260407113948.png]]

$S[1:n]$: liste af antal studerende i kursus $S_i$
$n$ kurser
$K[1 : m]$: liste af lokaler med kapacitet $K_{j}$
$m$ lokaler

Eksamen kan afholdes i lokale kursus i kan holde eksamen i lokale j hvis antallet af studerende er mindre eller lig med kapaciteten.
$$
S[i] \leq K[j]
$$
Et kursus pr. lokale.
Vi går baglæns:
![[Pasted image 20260407114629.png]]

![[Pasted image 20260407114752.png]]

For hvert kursus:
så længe kursus i ikke passer til lokale, gå til næste lokale
når kursus i passer til lokale k, så noter par af lokale og kursus og gå til næste lokale

Algoritmen kører i lineær tid. 
Den stopper når enten k eller s når deres maksimale værdi.
I værste fald kører algoritmen tid $k+s$

![[Pasted image 20260407115316.png]]

De $t$ mindste kurser $1 \dots t$ har fået et lokale i sorteret række følge
Hvis kurserne $i$ og $i+1$ har fået lokalerne $j_{1},j_{2}$ (indexer) så er $j_{1}<j_{2}$

Vi kan antage at $s_{i} \leq s_{i+1}$
og $k_{i} \leq k_{i+1}$

![[Pasted image 20260407120552.png]]
## 21 Kageoptimering

![[Pasted image 20260407144736.png]]

Ja, det er korrekt.
Professoren vælger at tage afsted på dag $i$ og kan derfor ikke tage afsted på dag $i + 1$
P kan tage afsted igen på dag $i + 2$, men hvis dag $i + 3$ maksimerer kagekvaliteten, kan dette være et bedre valg at træffe.
Hvis $i + 4$ er et endnu bedre valg, så skal P alligevel tage afsted dag $i + 2$, da dette ikke vil bryde med lægens råd, og vil yderligere maksimere kageglæden.
![[Pasted image 20260407145525.png]]

![[Pasted image 20260407145545.png]]

Et simpelt modbevis: gode kager laves hver 3. dag:
$$
K=[1, 1, 5, 1, 2, 6]
$$
Hvis P vælger hver 2. lige dag, bliver summen 8
Hvis P vælger hver 2. ulige dag, bliver summen 8
Hvis P vælger hver 3. dag, bliver summen 11

![[Pasted image 20260407145847.png]]

For valgt hver dag (starter ved 1) kig da 3 dage frem
vi har altså dag i, i+1, i+2 og i+3
Hvis $K[i+1] + K[i+3] > K[i+2]$ vælg da i + 1, ellers vælg i+2

> Næsten, det er simplere end det
> ![[Pasted image 20260407150248.png]]
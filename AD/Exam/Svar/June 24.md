# Multiple-choice
## 1 Mergesort og sammenligninger

![[Pasted image 20260330105923.png]]

**4 sammenligninger.** ✅
Når længerne af del-listerne er 1, kaldes merge. 
Her sammenlignes hvert tal 1 gang for hvert par.
Der er to par; altså 2 sammenligninger.
Når de to par skal merges, tømmes den ene liste først. 
Det resulterer i to sammenligninger, altså 4 i alt.

> Hvis listen havde set anderledes ud, kunne der have været flere kald.

[[Mergesort]]
## 2 Rekursionsligninger

![[Pasted image 20260330125820.png]]

**1, 6** ✅

Vi bruger [[Master theorem|master metoden]] på 1..5
[[Substitution method|Substitutionsmetoden]] anvendes på 6. da formatet ikke passer til master metoden.
### 1 ✅
$a = 1, b = 2, f(n) = \Theta(n)$
$\log_{2}(1)=0$
Vi kan se at 3. holder:
$$
f(n)=\Theta(n)=\Omega(n^{\log_{2}(1)})=\Omega(1)
$$
Derfor gælder det, at $T_{1}=\Theta(n)=O(n \log n)$
### 2 ❌
$a =2,b=2, f(n)=\Theta(n \lg n)$
Vi ser at 1. holder da T ($\Theta(n^{\log_{2}(2)})$) vokser hurtigere end f:
Derfor gælder det at $T=\Theta(n)$
### 3 ❌
$a =2,b=2, f(n)=\Theta(n^{2})$
Vi ser at 3. holder da f vokser hurtigere end T ($\Theta(n^{\log_{2}(2)})$):
Derfor gælder det at $T=\Theta(n^{2})$
### 4 ❌
$a =4,b=2, f(n)=\Theta(1)$
Vi ser at 1. holder da T ($\Theta(n^{\log_{2}(4)})$) vokser hurtigere end f:
Derfor gælder det at $T=\Theta(n^{\log_{2}(4)})=\Theta(n^{2})$
### 5 ❌
$a =4,b=2, f(n)=\Theta(n \log n)$
Vi ser at 1. holder da T ($\Theta(n^{\log_{2}(4)})$) vokser hurtigere end f:
Derfor gælder det at $T=\Theta(n^{\log_{2}(4)})=\Theta(n^{2})$

### 6 ✅
[[Substitution method]]
Vi gætter på $O(n \log n)$.

Base case: $n_0 = 2$;
$T(2)=T(1)+\Theta(\log n)$

## 3 Del og hersk

![[Pasted image 20260330125837.png]]

[[Substitution method|Substitutionsmetoden]] er nok fornuftig her.
- opskriv ligning
$T(n)=\Theta(1)$ for $n=1$

Jeg tror det er 6 fordi for hvert kald af T, foretages der en beregning på $\Theta(n^{2})$
Det giver ikke mening at skrive $2\Theta(n^{2})$, da det er lig med $\Theta(n^{2})$.
$n^{2}$ er også det tungeste led, og trumfer derfor $\Theta(n \log n)$ i beskrivelsen af køretiden.
Derfor **6** ✅

## 4 Løkkeinvarianter

![[Pasted image 20260330125854.png]]
![[Pasted image 20260330125905.png]]

Algoritmen returnerer det næsthøjeste tal.
Det er sandt, at `a` altid antager den højeste værdi.
Det er sandt, at `a` altid er lig med, eller større end `b`
**3, 5** ✅
## 5 Algoritmeanalyse

![[Pasted image 20260330125917.png]]

Der laves en tom array
Liste A gennemgås tal for tal
B fyldes med det hidtil mindste tal i A

**2, 3, 5** ✅

## 6 Algoritmeanalyse

![[Pasted image 20260330125933.png]]

**1, 5** ✅
![[Pasted image 20260330144557.png]]

## 7 Algoritmeanalyse

![[Pasted image 20260330125953.png]]
gæt: 2, 3, 6 ❌
rigtige svar: **2, 4, 6** ✅
4, fordi konstant udførelse skal ske $n$ gange. 
$n \log n$ er f.eks. til [[Sortering og binære søgetræer|binær søgning]].
![[Pasted image 20260330145601.png]]
## 8 Amortiseret analyse

![[Pasted image 20260330130005.png]]

Køretiden er $O(m \log n)$ hvor $m$ er antal operationer, og $n$ er antallet af `MAKE-SET` operationer
5 er korrekt, da $m=(k_{1}+k_{2}+k_{3})$ og $n=k_{1}$. Derfor: $O(m \log n) = O((k_{1}+k_{2}+k_{3})\log k_{1})$
Alle som er O af 5, gælder også:
6 gælder derfor også, da $O(m \log m) = O((k_{1}+k_{2}+k_{3})\log (k_{1}+k_{2}+k_{3}))$
✅
## 9 Fibonacci Hobe

![[Pasted image 20260330130021.png]]
![[Pasted image 20260330130033.png]]

$$
\Phi(H)=t(H)+2m(H)
$$
$H$: antal operationer
![[Pasted image 20260216162706.png|400]]

Ud fra skemaet (og s. 478) læser vi, at `DELETE` tager $\log n$ amortiseret tid.
`Insert` operationer betaler for fremtidig `consolidate`
	Omkostning: $t(H)$ = længden af rodlisten
`Decrease-key` operationer betaler for fremtidige `cut` operationer
	Omkostning $2m(H)$ = antal markerede knuder

❌ Gætter på 5 (måske 4 er med, men den kan risikere at være konstant)
✅ 2, 3:
	`Minimum` ændrer ikke datastrukturen og derfor heller ikke potentialfunktionen.
	`Insert` operationerne øger rodlistens længde $t(H)$ med $1$, og dermed også $Φ(H)$
	`Delete` operationer kan resultere i nye markerede knuder men i dette tilfælde laves ingen markeringer fordi kun knuder i rodlisten mister et barn.
	`Decrease-Key` operationen resulterer ikke i nogen `Cut` operation, så potentialfunktionen ændres ikke
## 10 Stavudskæring

![[Pasted image 20260330130052.png]]
Hvad betyder hvad her?
$p$ er listen af værdier.
$p_{1} = 2$ er værdien af stangen med længde 1
$$
p_{1} = 2,
p_{2} = 3,
p_{3} = 5,
p_{4} = 7,
p_{5} = 11,
p_{6} = 12,
$$
Lad os prøve iterationerne
1. først 0 pga. linje 2
2. så 2, pga. linje 6: $max\set{0, 2 + 0}$

svaret er **3**.
![[Pasted image 20260403192112.png|319]]
Når vi kommer til $p_{5}$, så får vi mere værdi pr. enhed.

Kig på værdi pr. enhed:
$$
 p_{1} = \frac{2}{1},
p_{2} = \frac{3}{2},
p_{3} = \frac{5}{3},
p_{4} = \frac{7}{4},
p_{5} = \frac{11}{5},
p_{6} = \frac{12}{6},
$$
Eftersom, $\frac{11}{5}> \frac{1}{2}$, er det denne som vinder ved $p_5$


![[Pasted image 20260403185420.png|402]]

## 11 Huffman koder

![[Pasted image 20260330130106.png]]

1❌
Svaret er 2.
![[Pasted image 20260403193450.png]]
Dette er forkert:
![[Pasted image 20260403193527.png|329]]

>[!QUESTION] Why?
>Fordi 33+33 er større end 42 og 50. 
>Derfor skal 42 og 50 merges
## 12 Rød-sorte søgetræer

![[Pasted image 20260330130120.png]]
![[Pasted image 20260330130134.png]]

✅**2**
Svar: Knuden skal være sort fordi dens forælder er rød, ellers ville en rød-sort invariant være overtrådt. Værdien skal være mellem 22 og 44 fordi træet er et søgetræ.
## 13 Rød-sorte søgetræer

![[Pasted image 20260330130151.png]]
❌ 4, 6
✅ 1, 3, 4
### 1 ✅
Eksterne knuder har ingen børn og deres højde er derfor 0. 
Den sorte højde af en knude X er antallet af sorte knuder på vej ned igennem en vilkårlig sti fra X (X ikke medregnet). 
Hvis X er en ekstern knude er dens sorte højde er lig med 0
### 2 ❌
Kontradiktion:
Den sorte højde af en rød knude er lig med den sorte højde af dens far.
### 3 ✅
**To børn af en rød knude er altid sorte.**
### 4 ✅
Per definition af et rød-sort BST
### 5 ❌
Ifølge definitionen af rød-sorte knuder er eksterne knuder altid sorte.
### 6 ❌
Simpelt modeksempel: Når en knude indsættes i et tomt rød-sort træ, får den rød farve. Dens farve ændres til sort fordi den er rod.
### 7 ❌
Når en knude skal slettes skal dens direkte efterfølger (eller direkte forgænger) findes. Hvis den er rød så skal den og knuden der skal slettes bytte plads. Nu kan den røde knude slettes og dets eventuelle højre undertræ skal hægtes på den slettedes knudes far som venstre undertræ.
## 14 Mindste udspændende træ

![[Pasted image 20260330130205.png]]

**2, 5, 6, 7, 8** ✅

![[Pasted image 20260331155749.png|207]]
![[Pasted image 20260331153816.png]]
## 15 Snit og sikre kanter

![[Pasted image 20260330130220.png]]
![[Pasted image 20260330130234.png]]

## 16 Valg af algoritme

![[Pasted image 20260330130254.png]]
![[Pasted image 20260330130303.png]]

✅ **3** - gæt eftertjek Bredde-først og Bellman-Ford
4, Kruskal og 5, Prim er grådige og derfor dårlige valg.
Bellman-Ford algoritmen og Dijkstra’s algoritme beregner begge en korteste vej, men da grafen ikke har negative vægte er Dijkstra et bedre valg fordi den er asymptotisk hurtigere.
## 17 Korteste veje

![[Pasted image 20260330130321.png]]
**1, 3, 4, 8**✅ 
Gæt: Prims algoritme
![[Pasted image 20260403222256.png|204]]
Svar: Da der er negative vægte kan kanterne i træet findes ved at køre Bellman-Ford algoritmen, der giver det angivne output (som i dette tilfælde er unikt).
## 18 Beregningsgeometri

![[Pasted image 20260330130339.png]]

✅ **1, 2,** 
✅ **4**: hvis vi antager at Theta også gælder her.
![[Pasted image 20260403222937.png|335]]
# Skriftlige opgaver
## 19 Længste fælles delsekvens

![[Pasted image 20260330130405.png]]

Gæt
![[Pasted image 20260407105309.png|292]]

Problem: Jeg ved ikke hvornår man sætte en pil som peger til venstre
Løsning:
![[Pasted image 20260407105753.png|270]]
> Her peger den op, da 1 tallet kommer ovenfra. 
> Vi vælger først det største, hvorefter vi vælger op

![[Pasted image 20260407110004.png|270]]
>Her peger en op igen, men kan sådan set godt pege til venstre

![[Pasted image 20260407110106.png|270]]
> Her peger den til venstre, da et-tallet kommer derfra

Final:
![[Pasted image 20260407110437.png|270]]
Svar:
![[Pasted image 20260407110506.png]]
![[Pasted image 20260407110613.png|270]]
## 20 Induktionsbevis for køretid

![[Pasted image 20260330130418.png]]

### a)
$$
\begin{align}
T(n) & =n^{2}+\sum ^{n}_{i=1} \frac{i(i+1)}{2} \\
\end{align}
$$
$$
\begin{align}
T(1) & =1^{2}+\sum ^{1}_{i=1} 1 \\
 & = 2
\end{align}
$$
### b)
base case:
$$
T(1)=2\leq 2n^{3} =2
$$
induktionsskridt:
$$
\begin{align}
T(n+1) & =(n+1)^{2}+\sum ^{n+1}_{i=1} \frac{i(i+1)}{2} \\
 &=1+n^{2}+\sum ^{n+1}_{i=1} \frac{i(i+1)}{2} \\
\end{align}
$$
## 21 Køretid

![[Pasted image 20260330130440.png]]
![[Pasted image 20260330130455.png]]

### a) ❌
$$
T(n, k)=\Theta(max\set{n, k})
$$
Køretiden er afhængig af variabel t, som antager den største værdi af n og k.

**Korrekt svar:** $T(n, k)=\Theta(min\set{n, k})$
t antager mindste værdi af n og k
### b) ✅
Hvor mange gange skal k ganges med 2 for at være større eller lig med n?
Lad os sige at k = 2 og n = 16, her tre 3 gange
$$
\begin{align}
T(n) & =log_2(n)-log_2(k) \\
 & =\Theta(\log n)
\end{align}
$$
### c) ❌
`PrefixSum` kan udtrykkes som funktion af n. Denne kører log n gange i den ydre løkke.
Derfor er køretiden
$$
\Theta(n \log n)
$$

## 22 Minimax udspændende træ

![[Pasted image 20260330130510.png]]
![[Pasted image 20260330130520.png]]

### a)
Tag udgangspunkt i fire  punkter
Et MMUT er et træ hvor en maksimale vægt er mindst muligt. 
Udgangspunktet er ikke at det er et minimum spanning tree.
Vi skal vise, at ved at minimere værdien af den største kant får man ikke altid et MST

![[Pasted image 20260407113311.png|309]]
MMUT er jo ligeglad med om der er et MST
### b)
Et MST er til gengæld altid MMUT

Bevis ved modstrid:
Vi har et træ $T$ som er MST men ikke MMUT
Lad $T'$ være MMUT
Største vægt i $T$ er $e$
Største vægt i $T'$ er $e'$

Da $T$ ikke er MMUT, må det gælde at: 
- $|e|>|e'|$
- $e$ er ikke i $T'$
Når $e$ føjes til $T'$ dannes der en kreds
I denne kreds findes en kant der krydser snittet defineret ved sammenhængskomponenterne der opstår hvis $e$ fjernes fra $T$
dvs. at $e$ er ikke minimal i snittet, i modstrid med antagelsen
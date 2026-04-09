# Multiple-choice 39p
## 1 Rekursionsligninger 1p

![[Pasted image 20260403223249.png]]

ja: **1**✅, men ❌ 2, 3, 6 mangler
(gæt) nej: 3, 2, 4, 5, 6

2: fordi det er tilfælde to ganger vi lg n på f:
$f(n)\cdot \lg n = \Theta(n \lg n \cdot \lg n) = \Theta(n \lg^{2} n )$
## 2 Merge-Sort variant 3p

![[Pasted image 20260403223338.png]]

gæt:
❌ 1
✅ 4: $T$ kaldes jo 4 gange og gør arbejde i $n$ tid for hvert kald. 
## 3 Tumpesortering 4p

![[Pasted image 20260403223423.png]]

✅ gæt: **3, 4**
Hvorfor dette gæt? 
Algoritmen behandler det samme array og indskrænker området tre gange for hvert kald.
Ud af de tre kald, er to unikke.
Køretiden bliver derfor også 4.
![[Pasted image 20260404113253.png|583]]
## 4 Kryptos 1p

![[Pasted image 20260403223453.png]]
![[Pasted image 20260403223509.png]]

❌ gæt: 3, 5
✅ rigtig svar: **2, 5**

![[Pasted image 20260404113719.png]]
## 5 Arbejde og spand -1p

![[Pasted image 20260403223529.png]]

[[Critical path#Arbejde og spand|Arbejde og spand]]

Arbejdet må være $n \log n$, da det er den reelle mænge arbejde som skal gøres.
Spandet må være $\log n$, da træets dybde er logaritmisk.
Derfor gæt: ❌ 5

![[Pasted image 20260404114628.png]]

But why?
I det sidste skridt, når algoritmen kalder `MERGE` på de sidste to del-arrays, tager det `n` tid.
Span er givet ved: 
$$T_{\infty}(A \cup B)=\text{max}\set{T_{\infty}(A), T_{\infty}(B)}
$$

## 6 Parallelle algoritmer 

![[Pasted image 20260403223550.png]]

span $T_{\infty} = \Theta(\sqrt{ n })$
work $T_{1}=\Theta(n^{2})$
$$
T_{P} \leq \Theta(n^{2})/P+\Theta(\sqrt{ n })=\Theta(n^{2}/P+\sqrt{ n })
$$
✅ **Gæt: 1, 4**
❌ Mangler 5
$1: T_P = O(n^2)$
$2: T_P = O(n^{2}/\log n)$
$3: T_P = O(n^{3/2})$
$4: T_P = O(n)$
$5: T_P = O(\sqrt{ n })$
$6: T_P = O(\sqrt{ n })$
Disse grænser matcher påstandene for 1., 4. og 5., men er dårligere end grænserne i 2., 3. og 6. Ifølge Theorem 26.2 er disse grænser indenfor en faktor 2 af optimalt, så disse påstande kan ikke være sande.
## 7 Fibonaccihobe 4p

![[Pasted image 20260403223617.png]]

Nej: 1, 2, 6
✅ Ja: **3, 4, 5**

## 8 Længste fælles delsekvens 4p

![[Pasted image 20260403223654.png]]

Gæt: Find den længste streng som de har tilfælles
1: nej
2: nej
3: ja
4: ja
5: nej
6: nej
7: ja
8: ja
✅ Derfor: **3, 4, 7, 8**

![[Pasted image 20260404120348.png]]

## 9 Dynamisk programmering 4p

![[Pasted image 20260403223716.png]]

✅ **3**
![[Pasted image 20260404122344.png]]
## 10 Søgetræer 4p

![[Pasted image 20260403223734.png]]

✅ Gæt: **2, 5, 6**
Hvorfor?
2: den værste nøgle ligger dybest i træet a højde $h$
4: Et balanceret træ har højde $\log n$ og et ujævnt har i værste tilfælde højde $n$
	Store O af log n er derfor nok et dårlig bud. Jeg ville nok sige omega i stedet
	Vi fjerner derfor 4. 
	- Det var satme rigtigt

![[Pasted image 20260404122944.png]]
## 11 Rød-sorte søgetræer 0p

![[Pasted image 20260403223754.png]]

1: den skal være sort - nej
2: ja
3: nej
4: ja
5: nej - børn af sorte skal være røde
6: ja
7: nej - børn af sorte skal være røde
❌ Derfor: 2, 4, 6
Rigtig: **2, 4, 5, 7**
![[Pasted image 20260404123724.png]]
## 12 Mindste udspændende træ 4p

![[Pasted image 20260403223813.png]]

✅ **1, 2, 4, 6, 7**
Metode: Sorter kanterne efter vægt. En for en tilvælg dem. Hvis kanten forbinder en knude som *allerede* er i træet, spring den da over.
## 13 Mindste udspændende træ 4p

![[Pasted image 20260403223832.png]]

Det mindst udspændte træ vil have n kanter af vægt 1.
Det siges, at der er kanter mellem alle knuder.
✅ derfor **2**.

![[Pasted image 20260404124810.png]]
## 14 Korteste veje 4p

![[Pasted image 20260403223851.png]]

Det er vel bare $n$?
Der tegnes en knude *fra* den mindre *til* den større. Derfor når der laves knude n, vil knude 1 pege på den.
✅ Derfor **2**.
![[Pasted image 20260404125058.png]]
## 15 Bellman-Ford -1p

![[Pasted image 20260403223909.png]]

? Hvad er en vægtvektor?
? Hvad returnerer algoritmen?
Algoritmen returnerer `TRUE` hvis der er en sti med negativ vægt som er en cyklus på tværs af grafen.
? Skal den traversere hele træet? Ja

❌ Korrekte svar 1, 2

![[Pasted image 20260404130755.png]]
## 16 Valg af algoritme 1p

![[Pasted image 20260403223952.png]]

`BRUTEFORCE` skal være hurtigere eller lige så hurtig som `TREE` ved valg af $m$
Algoritmerne returnerer antal fælles tal.

Ved $m =\Theta(1)$, kører `BRUTEFORCE` i tid $n$, og `TREE` kører i tid $n \lg^{2} n$
Ved $m =\Theta(n)$, kører `BRUTEFORCE` i tid $n^{2}$, og `TREE` kører i tid $(n \lg n)^{2}$

✅ Lad os stoppe her, og bare sige 1 så.
❌ For en sikkerheds skyld så vælges 2 også, da der ikke fremgår at der vil være to point.

Rigtigt svar: **1, 4**
![[Pasted image 20260404142943.png]]

## 17 Matrixkæde-multiplikation -1p

![[Pasted image 20260403224016.png]]
![[Pasted image 20260403224024.png]]

Tænker det er 3: 
Vi kigger på den øverste række. parentes ved `1` to gange, parentes ved `3`, så parentes ved `4` to gange.
$$
\begin{align}
(A_{1})(\dots) \\
(A_{1})(\dots) \\
(A_{1})(A_{2}(A_{3}))(\dots)
\end{align}
$$
❌ Forkert. Dette skal gøres baglæns.
Vi kigger først på højre hjørne i matricen. Her står der 4. 
Et split ved 4: $(A_{1}A_{2}A_{3}A_{4})(A_5A_{6})$ passer kun ved **mulighed 1**✅

![[Pasted image 20260404145109.png]]
## 18 Disjunkte mængder 4p

![[Pasted image 20260403224042.png]]

Køretiden er $O(a \log b)$ hvor $a$ er antal operationer, og $b$ er antallet af `MAKE-SET` operationer
Der er $n$ `MAKE-SET` operationer. 
$a$ er det totale antal operationer: $a = \Theta(n^{2}+n+(n-1))=\Theta(n^{2})$
✅ Derfor er best case **4** (med fare for at være 6)
Det var 4 - ikke 6!
![[Pasted image 20260404145748.png]]
# Skriftlige opgaver

## 19 Splejse reb

![[Pasted image 20260403224132.png]]

## 20 Lange stier i træer

![[Pasted image 20260403224145.png]]

### a
Vi skal lave en **pre-order traversal** af et træ.
For hver knude vi besøger, holder vi øje med dybden af knuden, ved at have en tæller som går op og ned når vi traverserer træet.

Alternativ:
![[Pasted image 20260407154605.png]]
## 21 Mindste udspændende træ

![[Pasted image 20260403224209.png]]

### a
![[Pasted image 20260407151559.png|333]]
✅ {(1, 2),(2, 5), (5, 4), (4, 3)}

### b

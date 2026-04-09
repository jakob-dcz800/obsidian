# Multiple-choice 47p
## 1 Mergesort og rekursion 4p 

![[Pasted image 20260406203416.png]]

Dette er højden af træet
42-21-11-6-3-2-1
1   2    3   4  5 6  7

✅ **Derfor 5)**:
Største antal elementer på et kald i rekursionsdybde 1,2,3,. . . er henholdsvis 42, 21, 11, 6, 3, 2 og 1. Dvs. der er op til 7 samtidige kald.
## 2 Korteste-veje træ 2p

![[Pasted image 20260406203459.png]]

1: ja, men ved ikke hvad det betyder. men det lyder rigtigt eftersom der ikke er cyklusser
2: nej, der kan være langt mellem blade i træet
3: nej, ikke et binært træ, men et træ
4: ja
5: ja

Derfor 1, 4, 5
✅ 1: Der kan være flere korteste veje mellem $s$ og en knude $v$ (med samme vægt), og korteste-vej træet indeholder netop en af disse.
❌ 4: Et mindste udspændende træ (MST) minimerer summen af kantvægte og indeholder ikke nødvendigvis de korteste veje fra en bestemt knude s; 
>[!IMPORTANT]
betragt fx en u-orienteret graf med tre knuder og kanter af vægt 2, 2 og 3 hvor et MST vil indeholde de to kanter af vægt 2, men hvor kanten af længde 3 udgør den korteste vej mellem to af knuderne.

❌ 5: Dijkstra’s algoritme er kun garanteret korrekt når der ikke er negative vægte, så hvis dette ikke er tilfældet kan output være forkert. 
(Man kan i stedet bruge en anden algoritme, fx Bellman-Ford.)
## 3 Korteste veje 4p

![[Pasted image 20260406203528.png]]

Gæt
![[Pasted image 20260406205106.png|333]]

✅ **2, 3, 5, 7, 10**
## 4 Prim’s algoritme 4p

![[Pasted image 20260406203545.png]]
![[Pasted image 20260406203552.png]]

✅ **1**, for `b` går til `d`
## 5 Mindste udspændende træ 4p

![[Pasted image 20260406203610.png]]

Gæt: 
![[Pasted image 20260406205730.png|333]]

✅ **1, 4, 6, 9, 10**
## 6 Snit og sikre kanter 2p

![[Pasted image 20260406203627.png]]
[[Minimum spanning tree#Kanter|Snit og kanter]]

Gæt: 3, 4, 5
Korrekte svar: 1, 3, 5

1: Snittene med $S_1$ og $S_3$ har ikke nogen kant i $A$, der krydser, så de respekterer $A$
2: Kanten $\set{c, d}$ krydser snittet $(S_2, V − S_2)$, så det respekterer ikke $A$.
3: Snittene med $S_1$ og $S_3$ har ikke nogen kant i $A$, der krydser, så de respekterer $A$
![[Pasted image 20260406211026.png]]
4: Kanten {d, f} har ikke mindst vægt i snittet ({a, c, d}, {b, e, f}), så den er ikke sikker.
5: Kanten {d, f} har mindst vægt i snittet ({a, c, d}, {b, e, f}), så den er sikker. 
6: Kanten {a, d} krydser ikke snittet ({a, c, d}, {b, e, f}), så den er ikke sikker.

## 7 Amortiseret analyse 1p

![[Pasted image 20260406203644.png]]

Den kører op med 1, så den må summeres til nøjagtig 1
Gæt 1, 2, 5
Korrekte svar 4, 5

![[Pasted image 20260406211359.png]]
## 8 Køretid 2p

![[Pasted image 20260406203702.png]]

Lad os prøve en enkelt kørsel af løkken hvor n = 10
2: i = 1 mod 5
3: j = 5 - 1 mod 10
->
2: i = 2
3: 5 - 2 mod 10
Den kører kvadratisk tid

✅ **Gæt: 3, 4**
❌ Mangler, 5, 6
![[Pasted image 20260406211805.png]]
## 9 Rekursionsligninger 1p
[[Master theorem]]
![[Pasted image 20260406203713.png]]

1: nej, f er større (case 3), derfor $T = \Theta(f(n))$
2: ja, de er ens, derfor $\Theta(n \lg n)$
3: nej, det er en eller anden underlig potens
4: nej, det er case 1: hvor køretiden bliver $\Theta(n^{\log_{2}(3)})$ da denne potens vokser hurtigere en $n \lg n$
5: ja, de vokser lige hurtigt og lg n ganges på (case 2)
6: ja, skidtet kører n gange á lg n tid

Derfor: 2, 4, 5
Korrekt: 2, 5, 6
## 10 Del og hersk 4p

![[Pasted image 20260406203731.png]]

✅ **3, da $O(n^{2})$ er større end $O(n \lg n)$**
## 11 Fibonacci hobe

![[Pasted image 20260406203746.png]]

## 12 Binære søgetræer 3p

![[Pasted image 20260406203759.png]]
![[Pasted image 20260406203810.png]]
[[Rød-sorte søgetræer]]

1: nej, skal være sort
2: nej, røde børn skal være sorte
3: ja ✅ 
4: ja ❌- den er mindre end 27 adem
5: ja ✅ 
6: nej, sort højden ville være off
## 13 Binære søgetræer 4p

![[Pasted image 20260406203833.png]]

1: sort højden ville være forkert
**✅ 2: ja, hvorfor ikke?**
3: valg to bryder ikke invarianten
4: valg to bryder ikke invarianten
5: pfft
## 14 Disjunkte mængder

![[Pasted image 20260406203846.png]]

## 15 Invarianter 4p

![[Pasted image 20260406203901.png]]

hvis dette tal er mindre end det hidtil mindste, er det nu det mindste
ellers hvis det er mindre end det andet mindste, så er det nu det andet mindste

1: ja, da det er i starten af løkken hvori invarianten findes
2: nej, global minimum findes ikke i løkken ved i
3: ja
4: nej, siger intet om negative tal
5: ja
6: nej, det kan alle i princippet være lig hinanden

✅ **1, 3, 5**
## 16 Valg af datastruktur 4p

![[Pasted image 20260406203912.png]]

✅ **5 - bare et gæt.**
Vi finder det mindste tidspunkt i strukturen. 
![[Pasted image 20260406214326.png]]
## 17 Korrekthedsargumenter 4p

![[Pasted image 20260406203935.png]]

Find den bedste blanding af reelle tal som giver det højeste produkt.
Resultatet en et set af indekser som peger på de optimale tal

✅ 1: ja, hvis alle tal er mindre end 1, så er det tomme set Ø end bedre løsning
2: nej
✅ 3: ja
4: nej, negative indekser er ikke en del af løsningen
## 18 Dynamisk programmering

![[Pasted image 20260406203947.png]]
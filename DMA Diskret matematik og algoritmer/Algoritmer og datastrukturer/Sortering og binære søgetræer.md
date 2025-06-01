---
tags:
  - DMA
  - Algorithm
  - Datastructure
  - RAM
---

# Sortering og binære søgetræer
## Insertion sort

**Input**: sekvens af tal af $n$ længde $\langle a_1, a_2,..., a_n \rangle$
**Output**: permuteret (sorteret) liste af samme sekvens af tal $\langle a'_1, a'_2,...,a'_n \rangle$ hvor $a'_1 \leq a'_2 \leq ... \leq a'_n$

Tallene i arrayet kaldes keys (nøgler)
Nøgler er ofte associeret med anden tilknyttet data, f.eks. Medlemsnummer og adresse
Den associerede data kaldes satellitdata, tilsammen udgør de en record

Ideen bag **insertion sort** er som et spil kort som skal sorteres.
Når man kommer til et kort som *ikke* passer ind, rykkes det tilbage i rækken indtil det passer ind.
Insertion sort returnerer den originale array `A[1:n]` blot sorteret.

```
INSERTION-SORT(A, n)
	for i = 2 to n
		key = A[i]
		//insert A[i] into the sorted subarray A[1:i-1]
		j = i - 1
		while j > 0 and A[j] > key
			A[j + 1] = A[j]
			j = j - 1
		A[j + 1] = key
```

`i` repræsenterer det nuværende kort (her kort nr. 2)

I den øverste `for` løkke starter den på indeks `A[2]` og bevæger sig fra `A[2:n]` . Den starter ved `i = 2` for at kunne holde `A[i = 2]`op mod `A[j = 1]`

`while`løkken rykker `A[j]` ned en plads ad gangen så længe `j` er større end den nedre grænse for arrayet og `A[j]` er større end `key = A[i = 2]`

`while` løkken rykker tallet ved at `j = j - 1`

`A[j + 1] = A[j]` bytter om på tallene

Når `j` er justeret til det korrekte indeks (altså hvor tallet er permuteret), oversættes tilbage til `i` indekset.
## Løkkeinvarianter

Invariant: function, quantity, or property which remains unchanged when a specified transformation is applied.

Vi skal vise 3 ting:

1. **Initialization**: er sand før første iteration af et loop.
2. **Maintenance**: hvis det er sandt før en iteration, forbliver det sandt før den næste iteration
3. **Termination**: løkken afsluttes, og invarianten - og som regel også årsagen for, at løkken er afsluttet, giver os en værdi som hjælper os vurdere om algoritmen er korrekt.

4. skridt handler det om, at bevise at `for` loopet beholder de originale værdier men i sorteret form. Både i intervallet `A[0:i - 1]` og usorteret i intervallet `A[i:n]` . Dette må være korrekt før første iteration.
5. skridt beviser at imens `for` løkken kører, er ovenstående sandt. Den sorterede del af arrayet beholder de originale værdier men i usorteret for og ligeledes usorteret i intervallet `A[i:n]`
6. løkken afslutter når `i = n + 1` og løkken kører ikke en gang til. Intervallet for den sorterede array bliver altså: `A[0:n + 1 - 1]`

Denne metoder benyttes flere gange i bogen
## RAM-modellen

Bogen benytter sig af #RAM  (Random access machine) modellen for analysering af algoritmer. Oftest er det køretid der er øje for.

RAM modellen kan kun køre en process ad gangen og antager en konstant tid for hver operation.

RAM modellen har følgende processer og datatyper som udgør de basale byggeklodser som modellen kan bruge:

1. add, subtract, multiply, divide, remainder (`%`), floor, ceiling, exponentiation
2. load, store, copy
3. conditional, unconditional, subroutine call and return
4. int, float, char

RAM modellen indebærer ikke cache eller virtual memory

## Analyse af insertion sort

Vi kigger primært på størrelsen af input som den afgørende faktor for algoritmens løbetid

Vi noterer at en algoritmer af input størrelse $n$ har en løbetid på $T(n)$

Et enkelt statement på linje $k$ tager $c_k$ skridt at udføre. Antallet af gange netop dét statement udføres, skrives som $m$.

Vi får altså, at et statement løber $c_km$ gange.

For hver iteration a `i` i `for` loopet, kører while loopet $t_i$ gange

### Tabel

|linje|cost ($c_k$)|times ($m$)|
|---|---|---|
|1|$c_1$|$n$|
|2|$c_2$|$n -1$|
|3|0|$n-1$|
|4|$c_4$|$n-1$|
|5|$c_5$|$\sum_{i=2}^{n}t_i$|
|6|$c_6$|$\sum_{i=2}^{n}(t_i-1)$|
|7|$c_7$|$\sum_{i=2}^{n}(t_i-1)$|
|8|$c_8$|$n-1$|

### Omskrivning:

Algoritmens tid regnes ved at addere tabellens konstanter ganget med antal gange konstanterne løber

$T(n)=c_1n+c_2(n-1)+c_4(n-1)+c_5\sum_{i=2}^{n}t_i + c_6\sum_{i=2}^{n}(t_i-1) + c_7\sum_{i=2}^{n}(t_i-1) + c_8(n-1)$

**Bedste tilfælde** er, at arrayet allerede er sorteret. Dvs. at $t_i=1$ for $i = 1, 2, ..., n$
Formlen vil i så fald omskrives til at være:
$T(n) = c_1n+c_2(n-1)+c_4(n-1)+c_4(n-1) = (c_1+c_2+c_4+c_5+c_8)n+(c_2+c_4+c_5+c_8)$

Funktioner bliver altså så en lineær funktion som kan noteres som: $ax+b$

**Værste tilfælde** er, når arrayet er sorteret i omvendt rækkefølge.
I så fald vil $t_i=i$ for $i = 1, 2, ..., n$

Vi ved at:
$\sum_{i=2}^{n}i=(\sum_{i=1}^{n}i)-1=\frac{n(n+1)}{2}-1$

og:

$\sum_{i=2}^{n}(i-1)=\sum_{i=1}^{n}i=\frac{n(n-1)}{2}$

I værste tilfælde vil algoritmen løbe i tid:
$T(n)=(\frac{C_5}{2}+\frac{C_6}{2}+\frac{C_7}{2})n^2+(c_1+c_2+c_4+\frac{C_5}{2}-\frac{C_6}{2}-\frac{C_7}{2}+c_8)n-(c_2+c_4+c_5+c_8)$

Hvilket er et andengradspolynomium: $an^2+bn+c$
Fordelene ved en worst/best case scenario analyse er, at du får en øvre grænse for hvor længe en algoritmer løber.

Worst case sker ofte. F.eks. når man søger efter data som ikke findes i en db.
I nogle tilfælde er det relevant at undersøge average cases.

## Store-theta notation

De små konstanter $c$ er relativt ligegyldige. Det man skal have øje for, er den variabel der vokser hurtigst. I eksemplet ovenover er det $n^2$ der vokser hurtigst.

Det noterer vi således:

$\Theta(n^2)$

Vi ignorerer altså konstanter og de andre vækstrater, og beskriver løbetiden med udgangspunkt i det hurtigst voksende led

## Design af algoritmer

Insertion sort gør brug af et design som hedder incremental design.

Et andet godt alternativ som er nemmere at udregne køretid på, er divide and conquer

**Divide and conquer** gør brug af rekursive funktioner som opdeler problemet og løser dem på mindre skala, for efter at koble dem sammen for en løsning af det større problem.

1. Divide: Del problemet op i mindre del-problemer som grundlæggende er samme problem, men mindre i størrelse
2. Conquer: Løs delproblemerne
3. Combine: Sæt del-problemerne sammen for løsning af det originale problem

### Merge-sort

Merge-sort gør brug af **divide and conquer** ved at dele den originale array `A[1:n]` op, og derefter løse samme problem for en sub-array som passes ned i samme funktion (`A[p:r]`)

1. Divide: Del arrayet op i sub-arrays `A[p:r]` ved at finde mid: $q=\lfloor \frac{r-p}{2} \rfloor$. Sub-arrays bliver altså `A[p:q] & A[q + 1 : r]`
2. Conquer: Ved at sorterer resultatet af de to sub-arrays rekursivt. De sorteres ved at vi kalder funktionen vi er i: `MERGE(A, p, q, r)`
3. Combine: Ved at sammenlægge de to sorterede arrays `A[p:q] & A[q + 1 : r]`. Vi ender altså med `A[p:r]`

Funktionen kan ikke kalde sig selv igen når `A.length == 1` altså når `p == q`

Som tidligere nævnt er et array med kun 1 element altid sorteret.

Nøglen er derfor i combine-delen af algoritmen

#### Merge funktionen

`MERGE` er en hjælpe funktion som er del af `MERGE-SORT` funktionen. `MERGE` antager at de to sub-arrays allerede er sorterede internt.

For at merge de to arrays, kigger algoritmen på den første værdi i begge arrays, og lægger den mindste værdi af de to i output-arrayet.

```jsx
if (arr1[first] > arr2[first]) {
	output_array.push(A[0])
}
```

Siden operationen som udføres tager konstant tid, tager denne algoritme altså $\Theta(n)$ tid.

Forklaring:

$L$ er en kopi af det ene sub-array `A[p : q]`
$R$ er en kopi af det andet sub-array `A[p + 1 : r]`
$n_L$ og $n_R$ er længden af de respektive arrays

$i$ indekserer $L$
$j$ indekserer $R$

$k=p$ fortæller hvor i $A$ algoritmen skal placere de sorterede tal

#### Køretidsanalyse af merge-sort

![[køretid_merge_sort.png]]

## Lineær og binær søgning

Søgealgoritmer returnerer et indeks, hvis intet findes returneres -1

Lineær søgning kører gennem hvert tal og kører i tid $\Theta (n)$

ifm. køretid er vi ligeglade med hvilken logaritme der gøres brug af da logaritmer vokser med en konstant faktor

man kan højst dele arrayet op i to $log_2(n)$ gange
Binær søgning kører $\Theta(\lg n)$
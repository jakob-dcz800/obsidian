---
tags:
  - DMA
  - Datastructure
---

# Stakke, køer, lister, hobe

> (CLRS kapitel 10, dog ikke afsnit 10.3)

## Datastrukturer

Kapitel handler om repræsentation af **dynamiske sæt** ved brug af simple [[Datastrukturer]] som blandt andet benytter pointers

Alle datastrukturer skal gemmes i hukommelsen, dvs. i et stort array.
Er til for at tilgå/søge data hurtigt og gemme data kompakt

> [!Vigtigt]
> Mikkel går meget op i, at alt gemmes som arrays

### Arrays
Et array er gemt in-memory som sammenhængende sekvens af bytes.

Bogen tager udgangspunkt i, at det tager konstant (og samme) tid at indeksere alle entries i et array.

Når vi har at gøre med et array af objekter, indeholder arrayet en pointer til objektet, da de fleste sprog kræver, at alle værdier har samme bit-størrelse
### Matricer
$$M=\begin{pmatrix}1 & 2 & 3 \\ 4 & 5 & 5 \end{pmatrix}$$
Matricer af størrelse $m\cdot n$ repræsenteres ofte i:
- row-major order hvor rækkerne repræsenteres samlet: `[1, 2, 3, 4, 5, 6]`
- column-major order hvor kolonnerne er samlet: `[1, 4, 2, 5, 3, 6]`

Man kan også gemme kolonner og rækker i sine egne arrays.
Indeksering af elementer i arrays findes på side 253 CLRS
Blok-repræsentation er også en mulighed.
### Stakke
Stakke er dynamiske set hvor elementer der slettes er pre-specificerede.
I en stak er det det øverste element som slettes kaldes også last in, first out (LIFO)

Indsæt-operationen kaldes for `push(S, x)` og dernæst `delete(S)` eller `pop(S)` - disse tager ingen argumenter

Kun det øverste element er tilgængeligt

`S` = stakken
`S.Top` = indeks for øverste element
`S.Size` = størrelsen (`n`) af elementer
`S[1]` = nederste element
`pop(S)` returnerer øverste element og fjerner det fra stakken, selvom det viser sig i arrayet

Når `S.Top` = 1, er stakken tom
Hvis man forsøger `pop(S)` når stakken er tom, får man stack-underflow
Når `S.Top` bliver større end `S.Size` får man stack overflow

Operationerne er på side 255 CLRS
`is-empty(S)` returnerer false/true
`is-empty` returnerer true når `S.top == -1`

det der poppes, står stadig i arrayet men overskrives når der pushes

Alle køretider for operationerne er $\Theta(1)$
Arrayet som stakken lever i, har fast størrelse
### Køer
I en kø er det det element som først blev indsat som slettes - first in, first out (FIFO)

Insert operationen kaldes for `enqueue(Q, x)` og delete kaldes `dequeue(Q)` og denne tager ingen argumenter

Køen har `head` og `tail`
Når man kalder `enqueue(Q, x)` placeres x ved køens `tail`
Når man kalder `dequeue(Q)` fjernes elementet ved `head`

`Q.tail` indekserer hvor det næste element placeres
nye elementer kommer ind fra højre side og ud fra venstre
køen har også `is-empty(Q)`
køer er cykliske

`Q.N` = størrelsen af arrayet (ikke køen)
sidste index i arrayet er `Q.N - 1`
køen er tom hvis `tail == head`

### Hægtede lister

Datastruktur hvor elementer kan ligge hulter til pulter i arrayet
Hvert element har en pointer der peger på det næste i rækken
Hvert element har nøgleværdi og felt(er) ved siden af med en pointer til næste og/eller forrige felt

`key` : værdi
`next` : næste element (index)

Vi kan altså indsætte elementer på vilkårlige pladser
Vi behøver ikke at gøre plads men skal bare tjekke om der er plads
Dobbelthægtede lister peger både frem og tilbage

`prev` forrige element (index)

pile kaldes hægter eller pointers
rækkefølgen in-memory er: 
1. key 
2. next 
3. prev

Vi kan bruge `list-search(L, k)` hvor k: nøgleværdi vi leder efter
Listen har sit eget `head` som har fast sted i hukommelsen. 
`Head`: index for første element
`NIL`, man er ikke kommet til enden af listen `NIL==/` ??

## Hobe

Hvert element referer til en node i et [[Grafalgoritmer#Træer|træ]]

Hobe har attributten `A.heap-size` som fortæller størrelsen af hoben
Roden i træet er `A[1]`
I et [[Grafalgoritmer#Binære træer|binær træ]] (altså med to børn per node) kan man tilgå `left` og `right` :

```
PARENT(i)
	return floor(i/2)

LEFT(i)
	return 2 * i
	
RIGHT(i)
	return 2 * i + 1
```

max-heaps har største element som rod hvor min-heaps har mindste

“bobler ned”:

MAX-HEAPIFY vedligeholder maks-hobe strukturen med udgangspunkt i et indeks, som her ikke passer ind for at strukturen er max-heap

denne starter ved $\lfloor \frac{A.Heap-size}{2}\rfloor$altså ved næst-nederstes lag, fordi det nederste lag kan ikke boble ned!

Se side 165 CLRS

BUILD-MAX-HEAP konverterer et array til en maks-hob.

Antallet af blade i træet er `A[floor(n/2) + 1 : n]`
Build-max-heap kan gøres i tid: $O(n)$ via lidt kompliceret bevis men se 24-09 slides
Når et element bobler ned, vælger den det største barn
**Blad**: knude uden børn

Antal blade: $\lceil\frac{n}{2}\rceil$

### Hobeordenen

mangler...
## Heapsort

Kører $\Theta(n\cdot \log(n))$ men bevarer en konstant mængde plads
Benytter hobestrukturen

Hobe er også gode til prioritetskøer

Algoritmen bygger først et **max-heap** fra et array `A[1:n]`
Roden er så det største element, `A[1]` kan så bytte plads med `A[n]`

Derefter kører den MAX-HEAPIFY på det største af de to børn
`A.heap-size` bliver 1 mindre pr. iteration og `A[1]` kan så bytte plads med det nye sidste element

![[Stakke, køer, lister, hobe 2025-03-08 16.47.23.excalidraw]]
## Prioritetskøer

Multimængde (der kan være flere af samme værdi)

Al sortering med sammenligninger kræver $\Omega(n\cdot \lg(n))$ sammenligninger

Prioritetskøer er datastrukturer af set $S$ af elementer alle med en `key` værdi

`INSERT(S, x, k)` indsætter elementet $x$ med nøgle-værdi $k$ ind i $S$

samme som $S \cup \set{x}$ (union)

`MAXIMUM(S)` returnerer element med største `key`

`EXTRACT-MAX(S)` fjerner og returnerer element med største `key` . selvom der er to af samme, returneres kun 1 element

`INCREASE-KEY(S, x, k)` forøger element $x.key$ med k så det er større eller lig med det nuværende
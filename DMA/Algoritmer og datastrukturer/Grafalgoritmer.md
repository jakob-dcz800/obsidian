---
tags:
  - Math
  - Algorithm
  - Datastructure
---

# Grafalgoritmer
## Træer
## Binære træer
## Binære søgetræer

Binært søgetræ, hver knude har nul, et eller to børn
Hver knude har referencer til forældre, venstre og højre barn, samt egen værdi
Venstre barn skal være mindre end knuden, og højre skal være større

Et binært søgetræ, er ikke nødvendigvis struktureret som et [[#Træer|træ]] hvor venstre mod højre skal fyldes op. Dog skal venstre tal i et niveau skal være lavere end sin venstre nabo

Disse strukturer er ikke hobe og skal ikke opretholde [[Stakke, køer, lister, hobe#Hobeordenen|hobeordenen]]
Det binære søgetræ opretholder [[#Søgetræsinvarianten|søgetræsinvarianten]]

Hver knude tager 4 pladser i array $A$, key, left, right og parent

> [!NOTE]
> Basale operationer i et binær-træ tager tid som er proportionel med højden af træet
> Binære søgetræer kan desuden også benyttes som køer

Binære søgetræer benytter hægtede liste-modellen, hvor en key (value) er koblet til satellitdata (left, right og p).
$p$, repræsenterer knudens venstre og højre barn, såvel som knudens forældre. Hvis en af disse mangler, står der `nil`

Træet har en attribut `root` som peger på roden af træet, eller `nil` hvis træet er tomt (`T.root`)
`T.root` er den eneste knude som har `nil` som forældre.

![[Grafalgoritmer 2025-03-08 17.43.08.excalidraw]]

Når vi ser på en forældre, skal de venstre børn alle være mindre en knudens værdi, og de højre være større. Dette gælder for *alle* knuder.

### Søgetræsinvarianten
Skriv noget om den.


### Inorder-tree-walk
Printer først venstre barn, så knuden, og sidst højre barn således:
```
INORDER-TREE-WALK(x)
	if x != NIL
		INORDER-TREE-WALK(x.left)
		print x.xey
		INORDER-TREE-WALK(x.right)
```

Dette tager  $\Theta(n)$ tid, da alle, og kun alle elementer printes (hvis x ved det første kald er roden)
## Søgning af binære søgetræer

Vi viser, at følgende operationer på det binære søgetræ tager $O(h)$ tid - altså proportionel med højden.
### Search
Search søger efter én værdi i træet

Algoritmen tager pointer til roden og søgeværdi `SEARCH(x, k)`
Algoritmen returnerer blokken altså alle 4 værdier for $x$

Skridt:
	Hvis `x.key` er lig `k` så returner
	Hvis `k` er mindre end `x.key` så kør igen på venstre barn
	Ligeledes på højre, hvis `k` er større end `x.key`
Algoritmen er proportionel med højden, da der gøres en operation pr. niveau i træet
### Max/Min
Finder mindste og største tal i træet

For at finde det mindste tal, vælger vi at gå til venstre ind til vi har ramt bunden
	altså når `x.left == NIL`
Ligeledes går vil til højre indtil bunden er ramt for at finde `max`
### Efterfølger og forgænger
<mark class="hltr-cyan">CLRS side 318</mark>

Forgænger finder den størst mulige nøgleværdi hvor $y.key < x.key$
mindste tal som er større end $x$ - altså næste tal i rækken
Efterfølger finder den mindst mulige nøgleværdi hvor $y.key > x.key$

### Indsæt knude i binært søgetræ
Sætter tal ind i træet
Hele træet må modificeres når vi indsætter og sletter

Vi indsætter vi tallet fra toppen og lader det synke ned, sådan at det opretholder ordenen for et binært søgetræ [[#Søgetræsinvarianten|læs]]
Nye tal vil altid ende nederst i træet.
### Slet knude i binært søgetræ
Slet er mere kompliceret end indsæt

Strategi for slet:
- hvis ingen børn, så bare slet og ved at gøre forælderens barn til `NIL` (vi sletter ikke, men modificerer kun pointers)
- Hvis et barn, tager vi barnet og løfter op (vha. pointers)
- Hvis flere børn <mark class="hltr-red">mangler</mark>

### Transplanter 

Her bytter vi et sub-træ ud med et andet
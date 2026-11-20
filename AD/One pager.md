
# Divide and conquer
Divide and Conquer algorithm is a problem-solving strategy that involves.
- **Divide** : Break the given problem into smaller non-overlapping problems.
- **Conquer** : Solve Smaller Problems
	- Use brute force if size is sufficiently small
- **Combine** : Use the Solutions of Smaller Problems to find the overall result.

For mange algoritmiske problemer er netop del og hersk metoder de hurtigste.

---
# Geometrisk sum
>[!INFO] Definition
>En geometrisk række er en type matematisk række, hvor hvert led i rækken er et multiplum af det foregående led.
## Uendelig geometrisk række

>[!INFO] Definition
>En uendelig **geometrisk** række er en uendelig række, hvor de på hinanden følgende led har samme forhold.

# Master metoden

>[!TIP]
Master metoden er et formelt argument for køretiden - ikke et gæt

>[!INFO] Forudsætninger
>Hvis en rekursionsligning er på denne formel
$$ T(n)=aT(n/b)+f(n)$$
>hvor $a\geq 1$ og $b > 1$ er konstanter. Så kan man bruge master metoden

>[!NOTE] Definition
>Master metoden giver med det samme $\Theta$ hvis man kan finde $a, b, f$
>1. Hvis $f(n)= O(n^{\log_{b}a-\epsilon})$ for konstanten $\epsilon>0$, så gælder det:
>$$T(n)=\Theta(n^{\log_{b}(a)})$$
>_Hvis $f(n)$ i en hvis forstand er "lille" ift. funktionen T_
> ---
>2. Hvis $f(n)= \Theta(n^{\log_{b}a})$, så gælder det:
>$$T(n)=\Theta(n^{\log_{b}a})\lg n$$
>_$f(n)$ har "samme" vækstrate som T_
>---
>3. Hvis $f(n)= \Omega(n^{\log_{b}a+\epsilon})$ for konstanten $\epsilon>0$ og $af(n /b)\leq cf(n)$ for $c<1$ og nødvendigt stort $n$, så gælder det:
>$$T(n)=\Theta(f(n))$$
>_$f(n)$ vokser hurtigt ift. funktionen T_

>[!QUESTION] Hvad med floor / ceiling?
>Man ignorerer bare floor og ceiling. 
## Eksempel 1

Vi bruger [[mergesort|merge-sort]] som eksempel.
$$
T(n)=2T(n /2)+\Theta(n)
$$
✅Den er på den rigtige form.
- $a=2$
- $b=2$
- $f(n)=\Theta(n)$
 
>[!QUESTION]
>Skal $f(n)$ være en [[Asymptotic notation|asymptotisk]] funktion?
>**nej**, se [[#eksempel 2]]

Eftersom $\log_{2}2=1$, kan vi se at 2. holder:
$$
f(n)=\Theta(n^{\log_{2} 2})=\Theta(n)
$$
Af dette kan vi se, at:
$$
T(n)=\Theta(n) \log n= \Theta(n \log n)
$$
## Eksempel 2
$$
T(n)=T(\lfloor n /2 \rfloor )+T(\lfloor n /2 \rfloor )+3
$$
- $a=2$
- $b=2$
- $f(n)=3$
Eftersom at $\log_{2}2=1$, har vi at $n^{\log_{b} a}=n$
$f(n)$ skal være polynomielt mindre en $n^{\log_{b}a}$, siden at $\epsilon$ trækkes fra.
Da $f(n)$ er en konstant, er den i alle fald polynomielt mindre.
Vi har altså at 1. holder, og derfor:
$$
T(n)=\Theta(n^{\log_{b}a})=\Theta(n)
$$
## Eksempel 3
![[Pasted image 20260209174910.png]]

- $a=4$
- $b=2$
- $f(n)=n^{2}$
Vi har altså at $n^{\log_{b}a}=n^{2}$, og derfor:
$$
T(n)=\Theta(n^2\cdot \lg n)
$$
## Eksempel 4
![[Pasted image 20260209175018.png]]
# Undtagelser

>[!QUESTION] Hvornår kan man **ikke** bruge master metoden?
Her kan man ikke:
>$$T(n)=4T(n/2 +2)+n$$
>da den ikke følger formen

> [!TIP]
> Floor and ceiling can be ignored
> Base step can be ignored

# Recursion trees

## [[Mergesort|Merge-sort]]

Vi har ligningen:
$$
T(n)=
\begin{cases}
\Theta(1) & \text{if } n=1 \\
T(\lceil n/2 \rceil )+T(\lfloor n/2 \rfloor ) + \Theta(n) & \text{if } n > 1
\end{cases}
$$
Som vi omskriver eftersom vi glemmer floor og ceil:
$$
T(n)=
\begin{cases}
\Theta(1) & \text{if } n=1 \\
2T(n/2) + \Theta(n) & \text{if } n > 1
\end{cases}
$$
Af dette kan vi konkludere, at en øvre grænse for køretiden kan formuleres:
$$
T(n)\leq 2T(n/2)+cn \space\space \text{ for some constant } \space\space c>0
$$
$cn$ udtrykker den tid det tager at udføre den ikke-rekursive del af algoritmen (merge).

### metode for rekursionstræ

_Her antages det, at $n$ er et lige tal_
- knude for hvert rekursivt kald
- for hver knude noterer vi tiden brugt på ikke-rekursiv del ($cn$ i dette tilfælde)
	- **kan være anderledes i andre tilfælde**
	- eftersom at listen halveres i størrelse for hvert rekursionskald, bliver tidsudtrykket $cn$ også halveret.
- formulér træet:
![[køretid_merge_sort.png]]

**Slut så af med at summere træet som i eksemplet ovenover**

>[!IMPORTANT] Notation
>Når vi laver et rekursionskald på køretidsudtrykket: $T(n)\leq 2T(n/2)+cn$, så rykker vi $n/2$ over på venstre side:
>$T(n /2)\leq 2T(n/4)+cn /2$
>_For rekursive algoritmer som deler data op i større bidder, deles $cn$ i antallet af bidder_

I bladene (nederst i træet) tager det konstant tid: $cn/n = c$
Der er $\lg n$ niveauer (listen deles i $2$ for hvert rekursionskald) hvor $\lg =\log_{2}$
Vi kan således udtrykke worst case køretid som $O(n \lg n)$
## Eksempel 2

$$
T(n)=T(\lfloor n/ 3 \rfloor )+T(\lfloor 2n/ 3 \rfloor )+cn, \space c>0
$$
![[Pasted image 20260209152859.png]]

>[!QUESTION] Hvorfor bliver træet skævt?
>Venstre barn vil altid være $\frac{1}{3}n$, hvorimod højre barn altid vil være $\frac{2}{3}n$
>Derfor kræver det flere kald før at størrelsen bliver $c$

For hver række får vi $cn$ når vi summerer knuderne:
	Se række 3: $(cn /9)+(2cn /9)+(2cn /9)+(4cn /9)=cn$

På det dybeste niveau (længst til højre) er der kun én knude. 
Dog kan vi sige at der højest er $cn$ omkostning på det dybeste niveau.
Derfor er den totale omkostning i værste tilfælde:
$$
T(n)=cn \lg_{3/2} n
= O(n \lg n)
$$
## Eksempel 3
$$
T(n)=T(\lfloor n /2 \rfloor )+T(\lceil n /2 \rceil )+3
$$
Vi gætter på køretid
$$
\text{forkert: } \space\space O(3\cdot \lg n)=O(\lg n)
$$
---
![[Pasted image 20260209153609.png]]

>[!TIP] Tommefingerregel
>Da det største led dominerer [[Asymptotic notation|asymptotisk]], er det blot det vi vælger eftersom at vi forkaster alle led som ikke dominerer. Det er altså når der er tale om en [[Geometrisk sum|geometrisk sum]], at vi kan gøre dette.
>$$
T(n)=c\sum^{\log_{k} n}_{i=0} k^{i}=O(n)
$$

>[!INFO] Bevis:
>
>$$2^0+2^1+\dots+2^{\lg n}=\sum ^{\lg n}_{i=0} \frac{n}{2^{i}}< \sum^\infty_{i=0} \left( \frac{1}{2} \right)^{i}=\frac{n}{1- \frac{1}{2}}=2n=O(n)
$$

I dette tilfælde:
$$
T(n)=3\sum^{\log_{2} n}_{i=0} 2^{i}=O(n)
$$
## Eksempel 4
$$
T(n)=4T(n /2)+n
$$
Vi gætter på køretid 
$$
\text{forkert: } \space\space O(2n \lg n) = O(n \lg n)
$$
---
![[Pasted image 20260209155131.png]]
For hvert rekursive kald ganges antallet af knuder med 4: $4^{i}$, hvor $i$ er det $i$'te kald.
$\frac{n}{2^{\lg n}}$ er omkostningen pr. kald.

Lad os omskrive det sidste led:
$$
\begin{align}
4^{\lg n} \frac{n}{2^{\lg n}} & =
n\cdot \frac{4^{\lg n}}{2^{\lg n}} \\
 & = n\cdot 2^{\lg n} \\
 & = n\cdot n \\
 & = n^{2}
\end{align}
$$
Vi får altså køretid:
$$
O(n^{2})
$$
_...fordi at køretiden er domineret af det sidste led ligesom [[#Eksempel 3]]_

# Rekursionsligninger

>[!TIP]
>Målet med at løse en rekursionsligning er 

Kan løses vha. 
- [[Recursion trees]]
- [[Master theorem]]
- [[Substitution method]]
## Eksempel

Hvordan løser man en rekursionsligning som denne her?
$$
T(n)=
\begin{cases}
\Theta(1) & \text{if } n=1 \\
T(\lceil n/2 \rceil )+T(\lfloor n/2 \rfloor ) + \Theta(n) & \text{if } n > 1
\end{cases}
$$
_Denne er fra [[Mergesort#Køretid|merge-sort]]_
Vi kan sommetider ignorere loft og gulv sådan at vi kan simplificere:
$$
T(n)=
\begin{cases}
\Theta(1) & \text{if } n=1 \\
2T(n/2) + \Theta(n) & \text{if } n > 1
\end{cases}
$$
Vi må gerne ignorere floor og ceil når vi skal bruger [[Master theorem|master theorem]] eftersom at den giver os et gæt på køretiden.
Når vi bruger [[Substitution method|substitutionsmetoden]] skal vi huske floor og ceiling.

# Substitution method
>[!INFO] Purpose
>The substitution method is used to find upper- (and lower) bounds on [[recurrences]] using mathematical [[induction]].

Substitutionsmetoden er reelt set [[Induction#Strong induction|stærk induktion]].
Metoden består af følgende skridt:
1. Gæt formen af løsningen (typisk [[Køretidsanalyse#Big-O|O-notation]], eller [[Køretidsanalyse#Omega|omega]])
2. Benyt stærk induktion til at finde de konstanter som skal gælde for at vise at gættet (1.) holder

[[Recursion trees|Rekursionstræ-metoden]] kan bruges til at finde et fornuftigt gæt.
Vi beviser altså at gættet er korrekt. 
## Antagelser

Vi noterer sjældent basistilfældet som i [[Mergesort#Køretid|denne rekursionsligning]]
For værdier af $n=1, 2,\dots,k$ (vælg selv et relativt småt $k$) kan vi antage, at $T(n_{k})= 1$
**Dette gælder kun op indtil konstanten, ikke for alle $k$**

_Man vælger selv k, det skal bare være en fast værdi på forhånd_
## Eksempel
**Preamble**
$$
T(n)=2T(\lfloor n /2 \rfloor )+n, n>1
$$
Vi antager $T(1)=1$
Vi gætter: $T(n)=O(n \lg n)$
Vi skal altså vise, at $T(n)\leq cn \lg n$, for alle $n \geq n_{0}$, for en konstant $c  >0$ og $n_{0}>0$
$$
\exists c, n_{0}>0 \space \forall n\geq n_{0}: T(n)\leq cn \lg n
$$
Uligheden gælder ikke når n = 1: $1 \leq 0$ hvilket er usandt.
Så vi vælger $n_{0}=2$
Vi ser inde i udtrykket $T\left( \left\lfloor  \frac{n}{2}  \right\rfloor \right)$, at hvis $n_{0}=2, 3$ så bliver udtrykket $T(1)$
Vi har lige set, at $T(1)$ ikke kan bruges i vores induktion da uligheden ikke holder.

---
**Base step**
Siden $T(n) = 2T\left( \left\lfloor  \frac{2}{n}  \right\rfloor \right)+n$ for $n>1$, har vi at 
- $T(2)=2(1)+2=4$
- $T(3)=2(1)+3=5$

>[!QUESTION] Hvorfor vælger vi ikke base case $n_0= 3$?
>Problemet opstår når vi skal vise for $n=4$, den afhænger nemlig af $n=2$ som vi så ikke har fået vist

Hvis vi vælger $c\geq 2$, har vi at $T(n)\leq cn \lg n$ for $n=2, 3$
- $T(2)=4\leq c\cdot 2 \lg 2=2c$
- $T(3)=5\leq c\cdot 3 \lg 3\simeq3c$

---
**Induction step**
Vi kan antage, at $n>3$ da vi havde to basistilfælde.
Vi kan også antage (pga. stærk induktion), at $T(m) \leq cm \lg m$ for $m=2,3,\dots, n-1$
_(1 galt jo ikke)_

Så hvis den gælder for $[2;n-1]$, så må den også gælde for $\lfloor n /2 \rfloor$, da det ligger i intervallet.
$$
T(\lfloor n /2 \rfloor )
\leq c \lfloor n /2 \rfloor \lg \lfloor n /2 \rfloor  
$$
Nu kan vi bruge definitionen:
$$
\begin{align}
T(n) & =2T(\lfloor n /2 \rfloor )+n \\
 & \leq 2c \lfloor n /2 \rfloor \lg \lfloor n /2 \rfloor +n \\
 & \leq c n \lg (n/2) +n \\
 & = cn \lg n - cn \lg 2 + n \\
 & = cn \lg n - cn + n
\end{align}
$$
Det vi skulle vise var $T(n)\leq cn \lg n$
Vi satte $c\geq2$ (i.e. lig med $2$), så der står reelt:
$$
\begin{align}
T(n) & \leq cn \lg n -2n+n \\
 & \leq cn \lg n-n \\
 & < cn \lg n 
\end{align}
$$

# Bipartite graph

A ****bipartite graph**** can be colored with two colors such that no two adjacent vertices share the same color. This means we can divide the graph's vertices into two distinct sets where:

- All edges connect vertices from one set to vertices in the other set.
- No edges exist between vertices within the same set.

****An alternate definition:**** Formally, a graph $G = (V, E)$ is bipartite if and only if its vertex set V can be partitioned into two non-empty subsets X and Y, such that every edge in E has one endpoint in X and the other endpoint in Y. This partition of vertices is also known as bi-partition.

![[Pasted image 20260323214432.png]]
_Nodes of the same color are of the same set_

# Dijkstra's algoritme
>[!DEFINITION]
>Algoritmen finder korteste vej til fra ét til alle punkter i en **vægtet og orienteret graf**
>Returnerer listen af distancer
>Dijkstra’s algoritme er kun garanteret korrekt når der **ikke er negative vægte**

Denne resulterer ikke i et [[Minimum spanning tree]], som Kruskal og Prims algoritme gør.

## Metode

- Vælg startknude
- Hav en liste af ubesøgte knuder
- Hav liste af distancer for alle knuder (opdateres løbende)

![[Pasted image 20260406134202.png|235]]
> Så vælger vi {c, b} da denne er mindste vægt
![[Pasted image 20260406134427.png|235]]
> Nu vælges d
![[Pasted image 20260406134539.png|235]]
![[Pasted image 20260406134607.png|235]]

# Bellman-Fords algoritme

Udregner distancer med udgangspunkt i en knude
Returnerer en liste af korteste veje (samme som [[Dijkstras algoritme]])


## Egenskaber
- Fungerer godt med **negative vægte**
- Benytter en vægtet, orienteret graf
- Kører max b-1 iterationer
- Tidskompleksiteten er $O(|V|\cdot|E|)$
	- For hver iteration gennemgås all knuder og deres kanter
	- Dette kan ske samtlige gange, men O simplificerer

## Metode
- Går gennem alle kanter for hver iteration
	- Tip: kig på alle knuder og deres udadgående kanter
- Vedligehold en liste af distancer for alle knuder

## Pseudokode

![[Pasted image 20260407131610.png]]

## Forskel fra Dijkstra's algoritme

Kører på grafer med negative vægte
Begge fejler ved **negative cyklusser**

Dijkstra er en [[Greedy algorithms|grådig algoritme]]
	Dijkstra vælger først og efterberegner ikke
Bellman ford er ikke grådig
	Bellman ford kører over samtlige iterationer og kan opdatere valg
![[Pasted image 20260407132149.png|333]]

> Her vil Dijkstra først vælge s,a:3 og ikke opdatere valget
> Bellman ford vil også først vælge s, a,  men efterfølgende opdatere den korteste vej fra s til a som at være s -> b -> a: 2
### Negativ cyklus
En negativ cyklus bliver mindre og mindre for hver iteration
# Parallelle algoritmer
## Critical path
**Kritisk sti**: "critical path" Længste sti i parallelforløbet
**Spand**: "span" Antal knuder på den kritiske sti, betegnes med $T_∞$
>[!TIP]
>Uanset hvor mange processorer der er til rådighed kan vi ikke udføre beregningen i færre end $T_∞$ parallelle skridt

![[Pasted image 20260318140232.png]]

Hver kasse er et kald til algoritmen
Hver bold er en udregning af $x$, $y$, eller $x+y$
Pilene viser hvilke afhængigheder der er.

**Arbejde** (“work”): Antal knuder i [[Grafmodel for parallelforløb|parallelforløbet]], betegnes med $T_1$
## Arbejde og spand

![[Pasted image 20260318141613.png]]

For parallelle processer er span udregnet til at være den process som tager længst tid

# Grafmodel for parallelforløb
parallel trace

**Knuder**: (Grupper af) instruktioner 
	“strands"
**Kanter**: Afhængigheder mellem instruktioner
	“Hvad er nødt til at være beregnet før denne instruktion kan udføres?”
![[Pasted image 20260318124528.png|250]]

## Eksempel

```python
RECURSIVE_SUM(A, l, r)
	if l = r
		return A[l]
	mid = floor((l + r)/2)
	lSum = RECURSIVE_SUM(A, l, mid)
	rSum = RECURSIVE_SUM(A, mid + 1, r)
	return lSum + rSum
```

![[Pasted image 20260318130022.png]]

# Parallelle rekursionsligninger

spawn: kald en procedure parallelt
sync: vent på at alle parallelle kald (fra denne procedure) returnerer
### Work

### Span

## Rekursionstræ for P-Fib

![[Pasted image 20260407140403.png]]
Se [[Critical path]]

## Eksempel

### 1
![[Pasted image 20260407140605.png]]

### 2
![[Pasted image 20260407140622.png]]

# Parallel Pseudocode

![[Pasted image 20260318135813.png]]
### Sekventiel
```python
SUM-ARRAYS(A, B, C, n)
	for i = 1 to n
		C[i] = A[i] + B[i]
```

### Parallel
```python
SUM-ARRAYS(A, B, C, n)
	parallel for i = 1
		C[i] = A[i] + B[i]
```

![[Pasted image 20260318135900.png]]

**Spawn**: kald en procedure parallelt
**Sync**: vent på at alle parallelle kald returnerer fra denne procedure (altså de kald som er foretaget i denne procedure)

# Opgaveplanlægning

"Scheduling"
De enkelte knuder i et parallelforløb skal udføres af fysiske kerner/processorer 
Opgaverne koordineres af en opgaveplanlægger (“scheduler”)

## Grådig opgaveplanlægning
Når en knude (“strand”) er klar til at blive udført bliver den stillet i en kø 
Når en processor er færdig med en knude går den i gang med næste knude fra køen

>[!TIP] Antagelse
>Tiden brugt på opgaveplanlægning er negligibel i forhold til tiden for beregninger

### Theorem 26.1

>Brent’s theorem

På en ideel parallelcomputer med processorer $P$ giver grådig opgaveplanlægning af en beregning med arbejde $T_{1}$ og spand $T_{\infty}$ en algoritme der tager tid $T_P ≤ T_1/P + T_∞$

Med processorer $P$ til rådighed kan vi ikke udføre beregningen i mindre end $T_{1}/P$ parallelle skridt
Uanset hvor mange processorer der er til rådighed kan vi ikke udføre beregningen i færre end $T_∞$ parallelle skridt

### Eksempler

#### Sekventiel sum
$T_1(n) = T_1(SUM(A, n)) = Θ(n)$ 
$T_∞(n) = T_∞(SUM(A, n)) = Θ(n)$

Theorem 26.1 giver:
$T_P(n) ≤ Θ(n)/P + Θ(n) = Θ(n)$
Flere end $P=1$ processorer hjælper ikke
#### Parallel sum
$T_1(n) = T_1(\text{P-SUM}(A, n)) = Θ(n)$ 
$T_∞(n) = T_∞(\text{P-SUM}(A, n)) = Θ(\lg n)$

Theorem 26.1 giver:
$T_P(n) ≤ Θ(n)/P + Θ(\lg n) = \Theta(\lg n + n/P)$
Med $P=\frac{n}{\lg n}$ processorer er tiden $T_{P}(n)=O(\lg n)$
flere processorer hjælper ikke:
$$
\begin{align}
\Theta(\lg n + n/P) & = 
\Theta\left( \lg n + n/\frac{n}{\lg n} \right)
\end{align}
$$

# Lower bound for sorting
## Comparison sort

>[!IMPORTANT]
>Alle sammenlignings-algoritmer skal lave $\Omega(n \lg n)$ sammenligninger

This only comments on comparison-based sorting where elements are compared:
- a < b
- a > b
- a = b
- etc.
# Merge-sort

> [!INFO]
> Merge-sort kører i værste tilfælde $\Theta(n \lg n)$

Merge-sort gør brug af [[divide and conquer]] ved at dele den originale array `A[1:n]` op, og derefter løse samme problem for en sub-array som passes ned i samme funktion (`A[p:r]`)

1. Divide: Del arrayet op i sub-arrays `A[p:r]` ved at finde mid: $q=\lfloor \frac{r-p}{2} \rfloor$. Sub-arrays bliver altså `A[p:q] & A[q + 1 : r]`
2. Conquer: Ved at sorterer resultatet af de to sub-arrays rekursivt. De sorteres ved at vi kalder funktionen vi er i: `MERGE(A, p, q, r)`
3. Combine: Ved at sammenlægge de to sorterede arrays `A[p:q] & A[q + 1 : r]`. Vi ender altså med `A[p:r]`

Funktionen kan ikke kalde sig selv igen når `A.length == 1` altså når `p == q`
Som tidligere nævnt er et array med kun 1 element altid sorteret.
Nøglen er derfor i *combine*-delen af algoritmen når vi bevæger os tilbage op ad træet.

## Køretid

> Merge-sort kører i værste tilfælde $\Theta(n \lg n)$

For at undersøge [[Time complexity|køretiden]] indfører vi rekursionsligningen:
$$
T(n)=
\begin{cases}
\Theta(1) & \text{if } n=1 \\
T(\lceil n/2 \rceil )+T(\lfloor n/2 \rfloor ) + \Theta(n) & \text{if } n > 1
\end{cases}
$$
Hvor $T(n)$ er worst-case køretid for liste af $n$ elementer - ikke et udtryk for den [[Asymptotic notation|asymptotiske køretid]].
Se [[Rekursionsligninger#Eksempel|løsning]]

![[Recursion trees#Mergesort Merge-sort]]
## Merge funktionen

> [!INFO]
> Merge kører i tid $O(k_{1}+k_{2})$, hvor $k_{n}$ er længden af liste $n$

`MERGE` er en hjælpe funktion som er del af `MERGE-SORT` funktionen. `MERGE` antager at de to sub-arrays allerede er sorterede internt.

For at merge de to arrays, kigger [[AD/Time complexity/Algorithms|algoritmen]] på den første værdi i begge arrays, og lægger den mindste værdi af de to i output-arrayet.

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

![[Pasted image 20260209142217.png]]
![[Pasted image 20260209142415.png]]
## Pseudo kode

```python
def MergeSort(A, p, r)
	if p < r:                            # check for base case
		q = floor((p + r) / 2)           # divide
		MergeSort()                      # conquer
		MergeSort()                      # conquer
		Merge()                          # combine
```

```python
def Merge(A, p, q, r)
	n1 = q - p + 1
	n2 = r - q
	let L[1 .. n1 + 1]    # be a new array
	let R[1 .. n2 + 1]    # be a new array
	
	for i = 1 to n1:
		L[i] = A[p + i - 1]
		
	for j = 1 to n2
		R[j] = A[q + j]
	
	L[n1 + 1] = ∞
	R[n2 + 1] = ∞
	i = 1
	j = 1
	
	for k = p to r:
		if L[i] <= R[j]
			A[k] = L[i]
			i = i + 1
		else A[k] = R[j]
			j = j + 1
	
```

> Antal elementer, der skal sorteres: **`n = r − p + 1`**

# Quicksort
Quicksort is an efficient, general-purpose sorting algorithm.

>[!IMPORTANT] In-place sorting
>Unlike [[Mergesort|merge-sort]], quicksort sorts _in place_, meaning that it requires only $O(1)$ words of memory in addition to the memory for the input list.
>
>Quicksort has worst case running time $\Theta(n^{2})$

Quicksort is a [[divide and conquer|divide-and-conquer]] algorithm. It works by selecting a "pivot" element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.


![[Pasted image 20260125001004.png]]

## Code

![[Pasted image 20260125001108.png]]![[Pasted image 20260125001046.png]]

> Antal elementer der skal sorteres: $n = r − p + 1$

# Grådige algoritmer

>[!DEFINITION] Hvad er en grådig algoritme?
>En grådig algoritme løser et problem, ved gentagne gange at vælge den mulighed som er bedst på det *nuværende* tidspunkt
>Den laver altså et grådigt valg hele tiden.

## Forskel fra dynamisk programmering

- [[Dynamisk programmering]] udregner først og foretager valget bagefter
- Grådige algoritmer vælger først og udregner efter

Grådige algoritmer er som regel hurtigere end dynamisk programmering.
Ikke alle problemer kan løses med grådige algoritmer og kræver derimod dynamisk programmering. (f.eks. 0/1 knapsack problem, fractal knapsack kan godt løses)

# Greedy choice property

> Paradigme/skabelon for problemløsning

- Når først et valg er taget, kan det ikke ændres
- Vi skal altså sikre os, at efter et valg kan vi fortsat finde en optimal løsning for problem $P$

> [!DEFINITION]
> Vi har "greedy choice property" hvis der findes en optimal løsning for problem $P$ som indeholder grådige valg.
> Uden denne property kan det ske, at et grådigt valg tages som udelukker alle optimale løsninger.

## Optimal delstruktur

![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=6&rect=34,153,548,760|Slides_Greedy_uden_indlagte_pauser-1, p.6]]
> Ovenstående er uformelt
> Hvis vi kan påvise greedy choice property, så er ovenstående altid gældende.

# Longest Common Subsequence (LCS)

Last Updated : 23 Jul, 2025

Given two strings, ****s1**** and ****s2****, the task is to find the length of the Longest Common Subsequence. If there is no ****common subsequence****, return `0`. A ****subsequence**** is a string generated from the original string by deleting 0 or more characters, without changing the relative order of the remaining characters.

For example, subsequences of "ABC" are "", "A", "B", "C", "AB", "AC", "BC" and "ABC". In general, a string of length $n$ has $2^n$ subsequences.

## Schema

![[Pasted image 20260404121545.png]]

Reglen er:
- række og kolonne 1 er 0.
- Hvis et bogstav er ens i $c_{i, j}$ sæt da en pil. Værdien er så diagonalen +1.
- Hvis et bogstav ikke er ens, skal værdien være maks af de to øverste eller det forrige tal i rækken
	 ![[Pasted image 20260404121806.png|197]]

# Rod cutting
## Eksempler

### Juni 24

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
> Kig på værdi pr. enhed:
>$$
 p_{1} = \frac{2}{1},
p_{2} = \frac{3}{2},
p_{3} = \frac{5}{3},
p_{4} = \frac{7}{4},
p_{5} = \frac{11}{5},
p_{6} = \frac{12}{6},
$$
> Eftersom, $\frac{11}{5}> \frac{1}{2}$, er det denne som vinder ved $p_5$


![[Pasted image 20260403185420.png|321]]

## Choosing a method

![[Pasted image 20260405162833.png]]

# Det konvekse hylster

> Se for dig, at du skal omkranse alle punkter på en plan ved at forbinde punkter.
> Denne ring skal indeholde alle punkter i mængden.

![[Pasted image 20260304180722.png|697]]

![[Pasted image 20260304180806.png]]

## Udregning

To algoritmer
- [[Graham’s Scan]] ($O(n\lg n)$)
- [[Jarvis March]] ($O(nh)$) hvor $h$ er antallet af hjørner af $CH(Q)$
# Konvekse mængder

>[!INFO] Definition
> En mængde $M$ er konveks hvis linjestykket mellem ethvert par af punkter er indeholdt i $M$.

## Eksempel
![[Pasted image 20260304175520.png]]

## Ikke-eksempel
![[Pasted image 20260304175536.png]]


# Jarvis March
>aka. Gift wrapping


Input: Mængde af $n$ punkter $Q$ i planen specificeret ved koordinaterne $(x, y)$. 
Output: Hjørnerne af det konvekse hylster $CH(Q)$ i cyklisk rækkefølge mod uret.

Køretid:
($O(nh)$) hvor $h$ er antallet af hjørner af $CH(Q)$
Bedre end [[Graham’s Scan]] når $h=o(\log n)$

![[Pasted image 20260407141512.png|333]]
![[Pasted image 20260407141528.png|333]]
![[Pasted image 20260407141542.png|333]]

# Graham’s Scan

Input: Mængde af $n$ punkter $Q$ i planen specificeret ved koordinaterne $(x, y)$. 
Output: Hjørnerne af det konvekse hylster $CH(Q)$ i cyklisk rækkefølge mod uret.

Køretid
$O(n\lg n)$
Domineret af sortering

> Bemærk: Nogle iterationer kan tage $Ω(n)$ tid, men i alt pusher og popper vi $≤ n$ gange.

## Metode
![[cg.pdf#page=9|cg, p.7-30]]

## Invarianter

Løkkeinvariant: 
I begyndelsen af hver iteration af for-løkken indeholder stakken $S$ hjørnerne af $CH(Q_{i−1})$ i rækkefølge mod uret.

![[Pasted image 20260407141419.png]]
# Amortisering

> [!TIP] Dele en omkostning jævnt ud over tid
>- Amortiseret analyse kan give mere præcise grænser for samlet (worst case) [[Time complexity|tidsforbrug]] når visse operationer tager mere tid end andre
>- Summen af amortiserede tider er en øvre grænse for den samlede tid
>- [[Potentialmetoden|Potentialfunktioner]] kan bruges til at lave præcise argumenter for amortiseret tid

## Eksempel 

- Amortiseringslån i banken (fast rente): 
	- Betal samme beløb hver måned 
	- I starten er en større del **renter**, senere er det meste $\text{afbetaling}$

![[Pasted image 20260211160728.png]]

## Amortisering i datastrukturer

> Læg løbende “penge” til siden for at betale for fremtidige dyre operationer

[[Regnskabsmetoden]]

# Binary counter
I forbindelse med [[Amortized analysis|amortiseret analyse]] kigger vi på omkostningen ved at lægge binære tal sammen.

![[Pasted image 20260211134432.png]]

Omkostningen defineres som følgende:
Når vi skal ændre et tal (f.eks. $0 \to 1$) har det omkostning: 1
$42+9$ har omkostning: 2, fordi at to tal ændres.

>[!QUESTION] Hvad er tiden for at tælle op med 1?
>- I værste fald? 
>- I gennemsnit?

![[Pasted image 20260211160547.png]]

# Potentialmetoden

Variant af [[regnskabsmetoden]], mere generel og præcis:
Summen af opsparede $ udtrykkes ved en funktion
$$
\Phi(i) \geq 0
$$
>[!IMPORTANT] Defintion
>Den [[Amortized analysis|amortiserede]] omkostning $\hat{c}_{i}$ er den faktiske omkostning $c_{i}$ plus ændringen i potentialet, $\Phi(i)-\Phi(i-1)$:
$$ \hat{c}_{i}=c_{i}+\Phi(i)-\Phi(i-1) $$

>[!QUESTION] Eksempel
>$\Phi(i)$: antal 1'ere i den binære repræsentation af $i$ 
>Lad $t_{i}$: antal 1'ere der bliver til 0'er mellem $i-1$ og $i$
>Omkostningen $c_{i}$ ved at ændre $i-1$ til $i$ er $c_{i}=t_{i}+1$
>$$ \begin{align} \\
\hat{c}_{i} & = c_{i}+(\Phi(i)-\Phi(i-1)) \\
 & \leq (t_{i}+1)-(t_{i}-1)  \\
 & = 2
\end{align}   $$

>[!TIP]
>En gyldig potentialfunktion må aldrig være lavere end dens udgangspunkt
>"Vi må aldrig have mindre i banken end hvad vi startede med"
>
>Denne funktion er f.eks. aldrig lavere end hvad den starter med. $H$ er antallet af hobe:
>$$\Phi (H)=t(H)+2m(H)$$
## Samlet tid via amortisering

Vi vil gerne udtrykke den samlede tid for en sekvens af $n$ operationer.

![[Pasted image 20260211162525.png]]

>[!tip] Betydning af led
>$$ \hat{c}_{i}=c_{i}+\Phi(i)-\Phi(i-1) $$
>Vi har led:
>- $c_{i}$: 
>- $\Phi(i)$: Potentialet lige efter $i$'te operation
>- $-\Phi(i-1)$:Potentialet lige før $i$'te operation

# Regnskabsmetoden

>Teknik til at holde styr på [[Amortized analysis|amortiserede]] omkostninger


Idé: Vi lægger “penge” til side og knytter vi dem til elementer i datastrukturen
Eksempel: [[Binary counter|Binær tæller]]

• Hver bit der er sat til 1 har $1 
• "Betaler selv" $1 for at blive ændret til 0 
• Omkostning per operation er $2 fordi én bit skal ændres fra 0 til 1 og have $1 tilknyttet

## Omkostning for binær tæller

![[Pasted image 20260211161156.png]]

# Binære søgetræer 
## Operationer

| Operation        | Køretid | Betydning |
| ---------------- | ------- | --------- |
| `Tree-Insert(x)` | $O(h)$  |           |
| `Tree-Delete(x)` | $O(h)$  |           |
| `Tree-Search(x)` | $O(h)$  |           |
| `Max`            |         |           |
| `Min`            |         |           |
Alle i tid $O(h)$ hvor $h$ er højden på træet, 
$\lg n ≤ h < n$

[[LSM Trees]]

Vi vil gerne have et balanceret træ som har dybde $\log_{2}n$

![[Pasted image 20260403182923.png]]

# Tree traversal

## Example

![[Pasted image 20260407142217.png]]
# Binary heap
## Operationer

| Operation      | Running time |
| -------------- | ------------ |
| `Make-heap`    | $O(1)$       |
| `Insert`       | $O(\lg n)$   |
| `Minimum`      | $O(1)$       |
| `Extract-min`  | $O(\lg n)$   |
| `Union`        | $O(n)$       |
| `Decrease-key` | $O(\lg n)$   |
| `Delete`       | $O(\lg n)$   |
Worst-case køretider

![[Pasted image 20260216155754.png]]

# Fibonacci heap
## Operationer

| Operation      | Running time |
| -------------- | ------------ |
| `Make-heap`    | $O(1)$       |
| `Insert`       | $O(1)$       |
| `Minimum`      | $O(1)$       |
| `Extract-min`  | $O(\lg n)$   |
| `Union`        | $O(1)$       |
| `Decrease-key` | $O(1)$       |
| `Delete`       | $O(\lg n)$   |
[[Amortized analysis|Amortiserede]] køretider, ikke worst-case ligesom [[binary heap]]. 
Dvs. omtrent gennemsnitlige køretider 
### Heap-Insert

![[Pasted image 20260216161513.png]]

### Extract-Min

![[Pasted image 20260216161540.png]]

Sidste skridt i `Extract-Min`, der leder til bedre amortiseret kompleksitet: 
	`Consolidate` sørger for at der ikke findes to rodknuder med lige mange børn

### Consolidate

![[Pasted image 20260216162218.png]]

## Definition

`kFibonacci` [[Stakke, køer, lister, hobe#Hobe|hoben]] er et samling af rodfæstede træer.
Hver knude `x` har nøgle `key(x)`$\in \mathbb{R}$. Nøglen svarer til den indsatte reelle værdi.

### Attributter
invariant: Nøgler falder i værdi når man går mod roden

| Attribut  | Betydning                           |
| --------- | ----------------------------------- |
| `x.deg`   | Antallet børn som er koblet til `x` |
| `x.mark`  | `bool` om `x` er markeret           |
| `x.p`     | parent                              |
| `x.child` |                                     |

### Egenskaber
Alle træer har [[Min heap|min-heap]] egenskaben, altså at:
> [!INFO]
> Enhver knude `x`, som har en forældre `p`, skal have en værdi `key(x) <= key(p)`
> Altså, et barns værdi skal være mindre eller lig med forælderens værdi
> 
> Roden er altså af lokal minimal værdi 

- Alle knuder er forbundne via. en [[Stakke, køer, lister, hobe#Hægtede lister|dobbelt-hægtet liste]]
- Alle knuder har pointer til forældre (hvis en sådan findes).
- Alle knuder har pointer **et enkelt barn** (hvis en sådan findes).
	- Se på eksempel herunder (4 til 7 og 5 til 7)
	- *Usikker: Der er ingen regler om hvilket barn som vælges?*
- Søskende er forbundne i en cirkulær [[Stakke, køer, lister, hobe#Hægtede lister|dobbelt-hægtet liste]]
	- Hvis en knude er enebarn, peger den på sig selv.
- Der findes en pointer til den mindste værdi i skoven som er roden af et træ.
- Rødderne er hægtet sammen i en cirkulær [[Stakke, køer, lister, hobe#Hægtede lister|dobbelt-hægtet liste]]

En knude kan have et ubegrænset antal børn
#### Eksempel
Her vises fire træer i en heap
Bemærk at H, kan referere til en samling a heaps.
En heap kan have op til flere træer.

![[Slides_Fibonacci_uden_indlagte_pauser-1.pdf#page=6&rect=273,154,560,767|Slides_Fibonacci_uden_indlagte_pauser-1, p.6]]

![[Pasted image 20260216160641.png]]
### Fordele

Det, at `Decrease-key` kører i tid $O(1)$ er en fordel når det kommer til 
[[Dijkstras algoritme|Dijkstra]]'s- og [[Prims algoritme]]
### Ulemper

Fibonacci heaps er i praksis ret langsomme, men giver gode teoretiske begrænsninger for køretid.
Man skal op på meget store problemstørrelser før at fibonacci heaps slår [[binary heap|binary heaps]]

## Amortiseret omkostning

Se [[potentialmetoden]]

![[Slides_Fibonacci_uden_indlagte_pauser-1.pdf#page=9|Slides_Fibonacci_uden_indlagte_pauser-1, p.9]]

Hvis vi kan finde en øvre grænse for den amortiserede omkostning, så finder vi den også for den faktiske omkostning.

## Diverse

>[!QUESTION] Hvordan tegner jeg et fibonacci træ?

![[Pasted image 20260216160938.png]]

# Forest

>[!definition] 
>a forest F is a graph with no cycles

![[Pasted image 20260331152504.png]]

# Lister

**Bitonisk (bitonic)** betyder, at sekvensen først går i én retning og derefter skifter retning præcis én gang.

Eksempler:
- Bitonisk:
    - [1, 3, 7, 12, 9, 4, 2] (stiger → falder)
    - [9, 6, 4, 5, 8] (falder → stiger)
- Ikke bitonisk:
    - [1, 4, 2, 5, 3] (skifter retning flere gange)

# LSM-træer

Alternative søgetræer, meget brugt i praksis


> [!NOTE] Idé (simpleste udgave)
> - Vi har $i$ sorterede lister $L_{i}$ for $=0, 1, 2, \dots$
> - Liste $L_{i}$ har $0$ eller $2^{i}$ elementer

Største liste indeholder $N \leq n$ elementer

![[Pasted image 20260216151551.png]]
## Operationer

| Operation        | Køretid | Betydning |
| ---------------- | ------- | --------- |
| `Tree-Insert(x)` | $O(h)$  |           |
| `Tree-Delete(x)` | $O(h)$  |           |
| `Tree-Search(x)` | $O(h)$  |           |

### Search
Udfører binær søgning på alle træer.
Tager tid:
![[LSM træer fibonaccihobe og Dijkstra.pdf#page=4&rect=20,82,1198,322|LSM træer fibonaccihobe og Dijkstra, p.4]]

### Insert
Skal overholde at liste $L_{i}$ har $0$ eller $2^{i}$ elementer.
- Vælg den første tomme liste $L_{j}$
- Fyld den med alle foregående elementer i sorteret rækkefølge
- Vi genbruger [[Mergesort#Merge funktionen|merge proceduren fra merge-sort]]
- Faktisk omkostning ved operation:
$$
\leq c \sum ^{j-1}_{i=0}2^{i}\leq c \cdot 2^{j}
$$
## [[Amortized analysis|Amortiseret analyse]]

Elementerne i liste $L_{i}$ har været del af $i$ merge operationer.
Koster $O(1)$ pr. element.

[[Regnskabsmetoden]]:
Hvert element tildeles $\lg n$ dollars når det indsættes.
Ved hvert merge, betaler elementet 1 dollar hvilket dækker omkostningen.
Dette holder, da jo flere elementer som er indsat, jo flere dollars får nye elementer tildelt.

![[LSM træer fibonaccihobe og Dijkstra.pdf#page=8&rect=19,102,1908,1065|LSM træer fibonaccihobe og Dijkstra, p.8]]

## Eksempel: RAM

![[LSM træer fibonaccihobe og Dijkstra.pdf#page=10|LSM træer fibonaccihobe og Dijkstra, p.10]]

# Max heap
A min heap is a [[Binary heap]]
## Egenskaber

### Invarianter
- Træet er perfekt balanceret 
- Knuder på nederste niveau er placeret længst til venstre 
- Værdierne er **ikke-aftagende** på stier fra blade til roden

![[Pasted image 20260216155710.png]]

# Minimum spanning tree
>[!DEFINITION]
>A minimum spanning [[Trees|tree]] or minimum weight spanning tree is a subset of the edges of a connected, edge-weighted undirected graph that connects all the vertices together, without any cycles and with the minimum possible total edge weight.

**Input**: connected graph $G$ and $w:E(G) \to \mathbb{R}$
**Output**: a minimum weight spanning tree
This is a discrete optimization problem

## Algoritmer
Der er to måder at finde MST på
Begge algoritmer er [[Greedy algorithms|grådige]]
### Kruskáls algoritme
>Returnerer et MST

Gror en skov, ikke et træ
Kigger på alle kanter og tager de mindste kanter. Hvis kanten forbinder to knuder som er i samme træ, springes kanten over.

```
let F_0 = ∅ 
as long as F_k is not spanning 
	let e ∈ E be of minimum weight 
		so that Fk ∪ {e} has no cycles
	set F_{k+1} = F_k ∪ {e}
output the spanning F
```

#### Korrekthed
Optimal delstruktur
Samme skridt gentages mange gange:
	Vælg den kant med mindst vægt. 
	Hvis den forbinder en ny knude til grafen, er den del af den optimale struktur

### Prims algoritme
>Returnerer et MST

Gror et træ, ikke en skov.
Kigger kun på kanter som tager udgangspunkt i knuder som allerede er besøgt.

## Kanter

Med udgangspunkt i en vægtet, ikke-orienteret og sammenhægende graf $G=(V, E)$
Et **snit** (cut) er defineret ved $(S, V-S)$
Snittet er en delmængde af $V$
En kant $(u, v) \in E$ **krydser** snittet hvis den ene knude hører til $S$, og den anden hører til $V -S$

En **let kant** er en kant som krydser snittet, og hvis vægt er mindre end nogen anden kant som krydser snittet.
Et snit **respekterer** en delmængde af kanterne $A$, hvis ingen kant i $A$ krydser snittet.
En **sikker kant**, kan tilføjes til et minimum spanning tree uden at bryde invarianten.
### Eksempel
![[Pasted image 20260406131710.png|367]]
![[Pasted image 20260406131922.png|367]]
> {A, C} er en let kant
![[Pasted image 20260406132051.png|367]]
> {A, C} er en let kant
![[Pasted image 20260406132151.png|367]]
> {F, D} er en let kant

# Priority queue

A priority queue is an abstract data type similar to a regular queue or stack abstract data type. 
In a priority queue, each element has an associated priority, which determines its order of service. Priority queue serves highest priority items first.

## Types

[[Binary heap]]
- [[Min heap]]
- [[Max heap]]

## Running times

![[Pasted image 20260216162706.png]]


# Rød-sorte søgetræer

>Standard [[Binære søgetræer|binært søgetræ]]
## Egenskaber

1. En knude er enten sort eller rød
2. Rodknuden er sort
3. Alle blade er `NIL` og er sorte
4. Hvis en knude er rød, er dens børn sorte
5. For enhver knude, indeholder alle stier til knudens blade det samme antal sorte knuder.

>[!TIP] Højde
> Et rød-sort træ med $n$ indre knuder, har maksimalt højden $2 \lg (n+1)$

>[!INFO] Sort højde
> Sort-højden er antal sorte knuder fra en knude, og ned til bladene
> Rodens sort-højden er altid mindst $h/2$
> Derfor gælder det, at 
$$ n \geq 2^{h/2}-1$$
## Køretider

`RB-Insert` tager $O(\lg n)$ tid
Søgning er $O(\lg n)$

`RB-Delete` tager også $O(\lg n)$ tid
`RB-Fixup` er del af `RB-Delete` og tager også $O(\lg n)$ tid

## Rotation
>Se 337 CLRS for eksempel

![[Pasted image 20260406202939.png]]
## Successor

En successor for $x$, er den mindste i mængden af tal, som er større end $x$.
I et træ er en successor dét tal, som besøges efter $x$ i en **in-order tree walk**
# Trees

> [!DEFINITION]
> A tree T is a connected [[forest]]

![[Pasted image 20260331152622.png]]

$H$ is a subgraph of $G$ if $V(H) = V(G)$ and $E(H) ⊆ E(G)$
Spanning tree $T$ is a connected subgraph of $G$ with no cycles
The weight of $T$ is $w(T)=\sum_{e \in E(T)}w(e)$
# Activity selection
Here, we use [[Greedy algorithms]]

![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=8&rect=40,160,383,762|Slides_Greedy_uden_indlagte_pauser-1, p.8]]

Vigtigt at: $s_i \not=f_{i}$
$[s_{i},f_{i})$: starter på $s_{i}$ og slutter lige inden $f_{i}$ se [[Intervaller]]
To aktiviteter er kompatible hvis deres tidsintervaller er [[Datastrukturer for disjunkte mængder|disjunkte]]
	Det betyder at der ikke er noget overlap.

## Eksempel

Her er en optimal løsning:
![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=10&rect=171,161,437,763|Slides_Greedy_uden_indlagte_pauser-1, p.10]]

Denne er optimal, da man ikke kan finde 5 tider som parvist er kompatible.
4 er det største antal.
Målet er at maksimere antallet er planlagte resurser.

## Løsning / algoritme

### Dynamisk programmering
[[Dynamisk programmering]]

![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=11&rect=263,169,531,755|Slides_Greedy_uden_indlagte_pauser-1, p.11]]
![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=12&rect=269,162,530,756|Slides_Greedy_uden_indlagte_pauser-1, p.12]]
![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=13&rect=267,163,529,757|Slides_Greedy_uden_indlagte_pauser-1, p.13]]
### Grådig algoritme
[[Greedy algorithms]]

# Proofs

## Contra positive
### Example

> $\sqrt{ 2 }$ is not rational

Assume towards a contradiction that $\sqrt{ 2 }$ is rational. 
Let Q be the (nonempty) [[Set laws|set]] of rationals that are equal to $\sqrt{ 2 }$. 
Let $\frac{a}{b}$ be the element in Q with minimum value of $|a| + |b|$. 

Now,
$$
\begin{align}
\sqrt{ 2 }  & =\frac{a}{b} \\
\iff 2 &  =\frac{a^{2}}{b^{2}} \\
\iff 2b^2 & =a^2
\end{align}
$$
From this, we can see that $a$ is an even number.
So $a=2c$ where $c \in \mathbb{N}$ is an arbitrary number with $c\neq 0$.
$$
\begin{align}
\iff 2b^2 & = (2c)^{2} \\
\iff b^2 & = 2c^{2} \\
\iff \sqrt{ 2 } & = \frac{b}{c}
\end{align}
$$
So $\frac{b}{c} \in Q$, but $|b| + |c| < |a| + |b|$ which contradicts the choice of $\frac{a}{b}$ .

## Induction
Another powerful proof method is induction (especially, in CS). 
In a proof by induction, we have some property $P ⊂ N$, and our goal is to prove that $P = N$. 
A proof by induction has two parts: 

1. (base) $1 ∈ P$
2. (step) for every $n ∈ N$, if $n ∈ P$ then $n + 1 ∈ P$
### Example

let us try to prove that for every integer $n ∈ N$,
$$
\sum^n_{i=1} i =\frac{n(n+1)}{2}
$$
#### Definition
$$
P=\set{
n \in \mathbb{N} : \sum^n_{i=1} i =\frac{n(n+1)}{2}
}
$$
#### Theorem
$$
P=\mathbb{N}
$$
**Base step**
$i \in P$, because $1 = \frac{1\cdot 2}{2}$

**Step**
Assume that $n ∈ P$. 
So $\sum^n_{i=1} i =\frac{n(n+1)}{2}$. Now,

$$
\sum^{n+1}_{i=1} i 
= n + 1 + \sum^{n+1}_{i=1}i
= n + 1+ \frac{n(n+1)}{2}
= \frac{(n+1)(n+2)}{2}
$$
It follows that $n + 1\in P$

## Strong induction

Strong induction includes **base case** and **induction step**

Here, we start by assuming $P(n_0)$ and $P(n) \Rightarrow P(n+1)$
We then have a stronger induction hypothesis
We must assert that all are true from $n_0$ to $n$

Identify starting value $n_0$

Example from class
	We assume all $P(n)$ work up till $n$ 
	Then we look at the $n - 2$ and conclude we can just add another $3$

# Time complexity
[[Køretidsanalyse]]
## Running time

We talk about running times of [[AD/Time complexity/Algorithms|algorithms]]
Function T(n) of input length
$$
T(n)=\text{max}\set{T(x):|x|\leq n}
$$
T(n) er et "tal" ikke en funktion.
>[!IMPORTANT]
>Aldrig skriv $T(1) \leq O(1)$
## Examples

Here, using [[Asymptotic notation]]
$n + 10 ≤ O(n)$
$n^2 + n ≤ O(n^2)$ 
$2 \cdot sin(n) ≤ O(1)$

$n + 10 \not ≤ O( \sqrt{n})$ 
$n^2 + n  \not ≤ O(n log_2 (n))$ 
$log_2 (n) \not ≤ O(log_2 (1 + log_3 (n)))$

## Proof

> To prove an asymptotic claim, just find literal values
> asymptotic claims cannot be proven by induction
> i.e. a simple proof:
> $T(n)\leq 100C \space lg_{2}(n)$

Claim: $n! \geq \Omega \left( \frac{n^n}{4^n} \right)$
Cannot be proven, since it is a claim

$n! \geq \frac{n^n}{4^n}$
Can be proven, since it is a relation

base
$1 \geq \frac{1}{4}$

step
$(n+1)! \geq \frac{(n+1)^{n+1}}{4^{n+1}}$

$(n+1)! = (n+1)n!$

Aka.
$n! \geq (n+1) \frac{(n)^{n}}{4^{n}}$

>[!IMPORTANT]
>$n!= \Theta(\sqrt{ n}(n / e)^n)$
>Måde at udregne $n!$ på

# Dynamisk programmering
## Egenskaber

- Generel algoritmisk teknik 
- Smart udtømmende søgning 
- Genbrug af beregninger

- It is mainly an optimization over plain recursion. Wherever we see a recursive solution that has repeated calls for the same inputs, we can optimize it using Dynamic Programming.
- The idea is to simply **store the results of subproblems** so that we do not have to re-compute them when needed later. This simple optimization typically reduces time complexities from exponential to polynomial.
## Eksempler

[[Rod cutting]]
[[AD/Problems/Matrixkædemultiplikation|Matrixkædemultiplikation]]
# Matrixkædemultiplikation

Optimer antallet af udregninger ved at sætte parenteser de rigtige steder.
## Metode for læsning

![[Pasted image 20260407135900.png]]
## Pseudokode

![[Pasted image 20260404145126.png]]

## Eksempel

![[Pasted image 20260405142919.png]]

nej: 3, 4, 1, 5
✅ **ja: 2**
Process: 
- Kig på højre hjørne $p[1, 6]$, split hér
- Gå så ned ad stien $p[1, j]$ og split når tallet ændres.
- Hver gang værdien i $p[i, j]$ skifter, så split og gå rekursivt ned af træet
- Udeluk muligheder en efter en.
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

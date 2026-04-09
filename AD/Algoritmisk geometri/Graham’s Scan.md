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
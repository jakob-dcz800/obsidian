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

# Eksempel: RAM

![[LSM træer fibonaccihobe og Dijkstra.pdf#page=10|LSM træer fibonaccihobe og Dijkstra, p.10]]
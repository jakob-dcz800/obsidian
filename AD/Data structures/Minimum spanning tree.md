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


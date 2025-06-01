---
tags:
  - DMA
  - Math
---
# Relationer

$$
_{a}R_{b}
$$
This is a relation. An example could be: "$a$ divides $b$".
A relation is a [[Serier og sæt#Sets|set]].
If $a$ divides $b$, then the set 
$$
R = \set{(2, 2), (2, 4), (2, 6), (3, 3), (3, 6)}
$$
Here, the **domain** is:
$Dom(R) = \set{2, 3} = \set{a \in A \mid \exists b \in B:  _{a}R_{b}}$,
and the **range** is: 
$Ran(R) = \set{2, 4, 6, 3} = \set{b \in B \mid \exists a \in A:  _{a}R_{b}}$

## Relation som matrice

Relationen som [[DMA Diskret matematik og algoritmer/Diskret matematik/Matricer|matrice]] defineres som
$$
R \subseteq A \times B
$$Hvor matricen er endeligt sæt (ikke uendeligt).
Kigger vi på sæt: 
$$
A = \set{1, 2}
, B = \set{r, s}
$$
Kan vi have relationen: $R = \set{(1,r), (2,s), (3, r)}$
Matricen bliver således: 
$$
M =
\begin{bmatrix}
1,0 \\
0,1 \\
1,0
\end{bmatrix}
$$
## Relation som digraph

Matricen kan omskrives til en directed graph.
Kigger vi på: $R = A \times A = \set{(a, a), (a, b), (b, a)}$, får vi matricen:
$$
\begin{bmatrix}
1, 1 \\
1, 0
\end{bmatrix}
$$
Dette omskriver vi til en directed graph:

![[Pasted image 20250309134939.png]]

## Stier

En relations eksponent bestemmer hvor mange skridt, der springes over i en digraph.
Betragt relationen
$$
R^1 = \set{(2, 1),(3,2),(4,3),(5,4)}
$$
Med yderligere trin:
$$
R_{2}= \set{(3, 1), (4, 2), (5, 3)}
$$
$$
R_{3} = {\set{(4, 1),(5,2)}}
$$

![[Pasted image 20250309135755.png]]

### Infinite steps

$R^{\infty} = R_{1} \cup R^2 \cup \dots \cup R^m$
$|R| = m$

## Ordensrelationer

### Poset
Et **poset** opretholder alle disse attributter
Noteres som $(A, \leq)$
*Er ikke altid ordnet efter tal*
$P(S)$ denoterer alle mulige subset (powerset)

Eksempel på **poset**:
$(\Bbb{Z}^+, \mid)$  - positive hele tal som deler hinanden
$(2, 7)$ er **ikke** sammenlignelig, da $2 \nmid 7 \land 7 \nmid 2$
Dette noteres:
	$(2 \not \leq 7) \land (7 \not \leq 2)$
### Refleksivitet
"Refleksiv"
$$
a \leq a
$$
### Transitivitet
"Transitiv"
Hvis $a = b$ og $b \leq c$ så $a \leq c$
### Antisymmetri
"Antisymmetrisk"
Hvis $a \leq b$ og $b \leq c$ så $a = b$

### Hasse-diagram
Hasse-diagrammer kan tegnes for poset
1. Fjern pile som kan fjernes pga. transitivitet og refleksivitet
2. Vend bladende opad

![[Pasted image 20250309141710.png]]
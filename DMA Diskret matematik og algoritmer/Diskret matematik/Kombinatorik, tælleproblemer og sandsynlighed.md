---
tags:
  - DMA
  - Math
---

# Kombinatorik og tælleproblemer

<mark class="hltr-cyan">KBR 3.1–3.2</mark>
Basic probability theory (KBR 3.4)
## Permutationer

A task $T_1$ and $T_2$ can be done in ways: $n_1, n_2$ respectively. 
Total ways of doing $T_1$ and $T_2$ is $n_1n_2$

Permutations are re-orderings of existing sets
Repetitions are allowed

![[Pasted image 20250308190232.png]]

## Kombinatorik

In how many ways can we choose r elements from an n-element set?

![[Pasted image 20250309125326.png]]
### Ordered with repetition
$$
n^r
$$

$P$, is "permute"
[[Serier og sæt#Sequences|Sequences]] 
### Ordered without repetition
$$
 _{n}P_{k} = \frac{n!}{(n-k)!}
$$
$C$, is "choose"
[[Serier og sæt#Sequences|Sequences]] without repetition
### Unordered with repetition
Let A be an n-element [[Serier og sæt#Sets|set]]. There are
$$
_{n+r-1}C_{r}= \frac{(n+r-1)!}{r!((n+r-1)-r)!}
$$
multisets of size r made up from elements of A
### Unordered without repetition
$$
_{n}C_{r} = \frac{n!}{r!(n-r)!}
$$
$C$, is "choose"
Subsets
### Examples
#### Number of poker-hands
$$
_{52}C_{5}
$$
You have a set of 52 card, you must pick 5.
No repeats and no order
#### Combinations of full-house

A full house is \[AAABB]
First we have 13 values to choose from to get \[BB], 4 suits, and we need 2 cards
$$
13 \cdot _{4}C_{2} 
$$
Thus we've chose a value, and we cannot get three additional pairs, so one value is removed
$$
12 \cdot _{4}C_{3} 
$$
#### Roll of three dice
How many ways can we roll three (*indistinguishable*) dice?
Two dice can come up the same (*repeats are allowed*).  
*Order doesn’t matter*. 
So we count [[Serier og sæt#Multisets|multisets]].
	$A=\set{1, . . . , 6}$ and $r = 3$. 
The total number of ways is:  
$$
_{6+3-1}C_{3}=_{8}C_{3}= \frac{8!}{3!5!}=56
$$
# Sandsynlighed


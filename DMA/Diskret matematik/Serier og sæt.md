---
tags:
  - DMA
  - Math
  - Datastructure
---

# Serier og sæt

$$
\set{ a, b, c } \not= (a, b ,c)
$$
Cartesian product:
We have that $A = \set{ a, b, c }$ and $B \set{1, 2}$, then
$$
A \times B = \set{(a, 1), \dots, (c, 2)}
$$
## Sequences

Ordered collection of elements
($a_n$) defines the while sequence

$a_n$ = nth element in $a$
**ordered doesn't mean it is sorted**

$0, 3, 8, 15, 24, 35, ...$, has the function: $f(n)=n^2-1$

The function
$f(n) = !n$ ⇒
{ $a_1=1$
{ $a_n = n a_{n-1}$ for $n > 1$

Is the same as:
$a_0 = 1$
$a_1 = 1$
$a_n = a_{n-1} + a_{n-2}$ for $3 \leq n$
## Series

$\sum$ lets us a set of sums in an accurate manner

$1+4+9+16...+n^2$ = $\sum_{i=1}^{n}n^2$

$i$ er nedre grænse, hvor $n$ er øvre
($s_k$) is the sum of $\sum$

## Sets

A set is a collection of elements **without ordering** and **no duplicates**
Sets have curly braces:

$Ø = \set{}$, empty set
$A=\set{1, 2, 3}$
$|A|=$  length of set (the cardinality of a set)
$|\Bbb{Z}|= \infty$ (length of set of all integers)
Set $A$ is finite if $|A|< \infty$
$$
\begin{matrix}
A=\set{a, b} &  & a \in A &  & c \not \in A \\
B=\set{1,2,3} \\
C = \set{x^2 : x =1,2,3}  &  & =\set{1,4,9} \\
D = \set{H, T} \\
\mathbb{N} = \set{1, 2, 3,\dots} \\
\mathbb{Z} = \set{\dots,-2,-1,0,1,2,\dots}
\end{matrix}
$$
### Theorem

#### 1 subset
Set $A$ is a subset of set $B$ if every $x$ in $A$ is also in $B$:
$$
A \subset B \equiv (x \in A) \Rightarrow (x \in B)
$$
E.g. $\mathbb{N} \subset \mathbb{Z}$

#### 2 
A set is **countable** if it is finite or if it its elements can be listed and enumerated.
E.g.
$$
A=\bigcup^\infty_{k=1}\set{a_{k}} =\set{a_{1},a_{2},a_{3},\dots}
$$
$\mathbb{N}$ is countable
$\mathbb{R};[0,1]$ is not countable
## Operations

### Union
$$
\cup
$$
![[Pasted image 20250309125749.png]]

### Intersection
$$\cap$$
![[Pasted image 20250309130330.png]]

### Compliment

$\over{A}$ or $A^c$
The set of all elements not in $A$

![[Pasted image 20250309130456.png]]

### Subtraction
![[Pasted image 20251006141214.png]]

## Disjoint sets

![[Pasted image 20251006141315.png]]

Two sets A and B are **mutually exclusive** or **disjoint** if they do not have any shared elements; i.e., their intersection is the empty set, $A∩B=∅$. More generally, several sets are called disjoint if they are pairwise disjoint, i.e., no two of them share a common element.
## Set partitions

![[Pasted image 20251006141357.png]]

## Multisets

$$
M = [1, 1, 4, 3]
$$

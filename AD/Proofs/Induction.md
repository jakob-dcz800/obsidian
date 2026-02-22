Another powerful proof method is induction (especially, in CS). 
In a proof by induction, we have some property $P ⊂ N$, and our goal is to prove that $P = N$. 
A proof by induction has two parts: 

1. (base) $1 ∈ P$
2. (step) for every $n ∈ N$, if $n ∈ P$ then $n + 1 ∈ P$

## Example

let us try to prove that for every integer $n ∈ N$,
$$
\sum^n_{i=1} i =\frac{n(n+1)}{2}
$$
### Definition
$$
P=\set{
n \in \mathbb{N} : \sum^n_{i=1} i =\frac{n(n+1)}{2}
}
$$
### Theorem
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

# Strong induction

Strong induction includes **base case** and **induction step**

Here, we start by assuming $P(n_0)$ and $P(n) \Rightarrow P(n+1)$
We then have a stronger induction hypothesis
We must assert that all are true from $n_0$ to $n$

Identify starting value $n_0$

Example from class
	We assume all $P(n)$ work up till $n$ 
	Then we look at the $n - 2$ and conclude we can just add another $3$
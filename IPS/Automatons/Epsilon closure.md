# Epsilon closure

![[Pasted image 20260611113815.png]]

$N$ is a [[NFA]] which contains:
- $S$ states
- $Σ$ the alphabet
- Starting state $s_{0}$
- Final states $F \subseteq S$
- $T$: A relation (tuples) that describe transitions $T \subseteq S \times (Σ \cup \set{\epsilon})$ 


## Fixed point

![[Pasted image 20260611121613.png]]

$$
F_{M}(X) = M \cup \set{t \mid \exists s \in X . s^{\epsilon}t \in T }
$$

$F_M$ is distributive, i.e., $F(X ∪ Y ) = F(X) ∪ F(Y )$

$F_{\set{1}} (\set{1, 2, 5}) = F_{\set{1}} (\set{1}) ∪ F_{\set{1}} (\set{2, 5})$
If we already computed $F_{\set{1}} (\set{1})$ we need not recompute it again!

### Process
- Start by $X_0 = ∅$ and compute $X_i = F(X_{i−1}) \dots$ until $X_n = F(X_n)$
- We have $∅ ⊆ F(X_0) ⊆ F(X_1) ⊆ \dots ⊆ F(X_n−1) = Xn = F(X_n)$
	- i.e., fixed-point reached because the set of states is finite!

## Worklist algorithm for ε-closures

> Suitable for pen-and-paper calculation

Have set $M$, want to compute $\hat{ε}(M)$.

1. Write out the elements of $M$ as a list, all unmarked.
2. If there are no unmarked elements, we are done:
	1. List contains all of $\hat{ε}(M)$
	2. Usually a good idea to **sort** the list now.
3. Consider the **first** unmarked element x
	1. Mark x in the list.
	2. Add each immediate ε-successors of x to the end of list (unmarked), if it’s not already there.
4. Go to step 2
## Example 1

![[Pasted image 20260611125600.png]]

| eps closure                  | resulting set               | fixed point                                                                                                                               | explainer                                                                                                       |
| ---------------------------- | --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| $\hat{\epsilon}(Ø)$          | $\set{Ø}$                   |                                                                                                                                           |                                                                                                                 |
| $\hat{\epsilon}(\set{1})$    | $\set{1, 2, 5, 6, 7}$       | $X_{0}=Ø$<br>$X_{1}=F(X_{0})=\set{1}$<br>$X_{2}=F(X_{1})=\set{1, 2, 5}$<br>$X_{3}=F(X_{2})=\set{1, 2, 5, 6, 7}$<br>$X_{4}=F(X_{3})=X_{3}$ |                                                                                                                 |
| $\hat{\epsilon}(\set{8})$    | $\set{1, 2, 5, 6, 7, 8}$    | $X_{0}=Ø$<br>$X_{1}=F(X_{0})=\set{8}$<br>$X_{2}=F(X_{1})=\set{8, 1}$<br>$X_{3}=F(X_{2})=\set{8, 1, 2, 5, 6, 7}$<br>$X_{4}=F(X_{3})=X_{3}$ | When {1} is added to the set, we can simply insert the epsilon closure of {1} since the closure is distributive |
| $\hat{\epsilon}(\set{3, 8})$ | $\set{1, 2, 3, 5, 6, 7, 8}$ | $X_{0}=Ø$<br>$X_{1}=F(X_{0})=\set{3, 8}$<br>$X_{2}=F(X_{1})=\set{3, 8, 1, 2, 5, 6, 7}$<br>$X_{3}=F(X_{2})=X_{2}$                          |                                                                                                                 |
| $\hat{\epsilon}(\set{4})$    | $\set{4}$                   | $X_{0}=Ø$<br>$X_{1}=F(X_{0})=\set{4}$<br>$X_{2}=F(X_{1})=X_{1}$                                                                           |                                                                                                                 |
> [!QUESTION]
> Why do we choose the elements in this order?
> {1}, {8}, {3, 8}, {4}

Answer:
{1} is the starting state
{8} is for the b transitions
{3, 8} is for the a transitions
{4} is for the c transitions

After this, we perform subset cunstruction
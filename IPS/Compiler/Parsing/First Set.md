# First Set

>[!TIP] In short
>First results in a set of terminals

>[!Definition] Definition
>Let $G = (Σ, N, S, P)$ be a grammar and ⇒ its derivation relation. 
>For all sequences of grammar symbols $α ∈ (Σ ∪ N)^∗$ , define
>$$\text{First}(α) = \set{c ∈ Σ \mid α ⇒^∗ cβ \text{ for some } β ∈ (Σ ∪ N)^∗ }$$
>All input tokens at the start of what can be derived from $α$

Computing [[Nullable Property|Nullable]] and [[First Set|First]] for right-hand sides: 
- Equations recursively use results for nonterminals 
- Smallest solution found by computing a smallest fixed point 
- Solved simultaneously for all right-hand sides of the productions.
## Recursive Rules for First

![[Pasted image 20260611214101.png]]

1. ε is not `first`
2. Terminals are `first`
3. If the first $\alpha$ is `nullable` then `first` depends on either $\alpha$ or $\beta$
4. The sub-productions ($\alpha$, $\beta$) of a non-terminal are `first` in their own right

### Equations for nonterminals
![[Pasted image 20260611215249.png]]
### Equations for the right-hand side
![[Pasted image 20260611215303.png]]

# Language

## Definition

Let $G = (Σ, N, S, P)$ be a grammar and ⇒ its derivation relation.
The language that $G$ generates is the set of all words that can be obtained by the **transitive** derivation relation:
$$
L(G) = \set{w ∈ Σ^{∗} | S ⇒^{∗} w}
$$
>[!TIP] In other words
>The language of $G$ is given by a set of characters in the alphabet that can be derived with the transitive derivation relation ($\implies^*$)
>
>For example, `aabbb` and `aaabbbb` $∈ L(G)$ 
>Because $S ⇒^∗$ `aabbb` and $S ⇒^∗$ `aaabbbb`.

## Transitive derivation

The transitive derivation relation is defined as:
- $α ⇒^∗ α$, for $α ∈ (Σ ∪ N)^∗$ , derived in 0 steps,
	- Where $N$ is the set of non-terminals
- $α ⇒^∗ β$ if there exists $γ ∈ (Σ ∪ N)^∗$ for $α, β ∈ (Σ ∪ N)^∗$ such that $α ⇒ γ$ and $γ ⇒^∗ β$
	- i.e. derived in at least 1 step.

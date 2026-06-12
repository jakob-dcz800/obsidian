# Nullable Property

>[!TIP] In short
>Nullable is a yes/no question

>[!Definition] Definition
>Let $G = (Σ, N, S, P)$ be a grammar and ⇒ its derivation relation. 
>For all sequences of grammar symbols $α ∈ (Σ ∪ N)^∗$ , define
>$$\text{Nullable}=\begin{cases} \text{true},  & \text{if } \alpha \implies^* \epsilon \\ \text{false, } & \text{otherwise}\end{cases}$$
>If a non-terminal can result in an ε, then it is Nullable

Computing [[Nullable Property|Nullable]] and [[First Set|First]] for right-hand sides: 
- Equations recursively use results for nonterminals 
- Smallest solution found by computing a smallest fixed point 
- Solved simultaneously for all right-hand sides of the productions.

## Recursive Rules for Nullable
1. ε is inherently nullable
$$
Nullable(ε) = true
$$
2. Terminals are not nullable
$$
Nullable(a) = false
$$
3. Non- or terminals in series are nullable if their productions are
$$
Nullable(\alpha \beta) = Nullable(\alpha) \land Nullable(\beta), \alpha, \beta ∈ (Σ ∪ N)^∗
$$
4. A non-terminal is nullable if just one of it non- or terminals are nullable
	In other words: a nonterminal is nullable if any of its productions have a nullable right hand side.
$$
Nullable(N) = Nullable(\alpha_1) \lor \dots \lor Nullable(α_n)
$$
for all productions of $N$ of form $N → α_i , i ∈ \set{1 \dots n}$

>[!TIP]
>See fixed-point calculation at book page 59.
### Equations for nonterminals:
![[Pasted image 20260611213546.png]]
### Equations for the right-hand side
![[Pasted image 20260611213617.png]]

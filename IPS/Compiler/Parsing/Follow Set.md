# Follow Sets for Nonterminals

>[!DEFINITION] Formal definition
>A character $c$ is in $Follow(N)$ if there exists a derivation from the start symbol $S$ such that $$S \implies \alpha N c \beta$$
>(where $\alpha$ and $\beta$ are possibly empty sequences of [[Context-free grammars|grammar]] symbols).
>I.e. $c$ is in $Follow(N)$, if $c$ at some point may *follow* $N$ in a sequence of grammar symbols.
>>[!WARNING] Not a nonterminal property
>>This is **not** a *nonterminal* property, but a property of all the *productions* that (directly or indirectly) uses $N$ on their **right hand side**.


## Motivation
[[First Set|First]] sets might not be enough for [[parsing]].
Assume a production $X → α$ and $\text{Nullable}(α) = true$.
If the [[LL(1)|look-ahead]] can follow $X$ then this production may be chosen 
	(but the [[First set]] cannot provide this information!)

## Definition
Let $G = (Σ, N, S, P)$ be a grammar and ⇒ its derivation relation. 
For each nonterminal $X ∈ N$ define
$$
\text{Follow}(X) = \set{c ∈ Σ \mid S ⇒^∗ αXcβ \text{ for some } α, β ∈ (Σ∪N)^∗ }
$$
All input tokens that follow $X$ in sequences derivable from $S$.

### Adding special characters
To recognize the end of the input, we also extend the grammar with new symbols
- A starting character $S'$ , 
- A new character $\$$ ,
- And a production $S' → S\$$ 
- Instead of just $S' \to S$ (which may be a valid end of terminals)

>It follows that we always have $\$ ∈ Follow(S)$


>[!TIP] End of line
>`{ $ }` is in `Follow(N)` if exactly $S' \to \alpha N \$$
## Recursive Rules for Follow

Requires solving a collection of **set constraints**, which are generated from the right-hand sides.

For each $X ∈ N$, consider all productions $Y → αXβ$ and generate:
- $\text{First}(β) ⊆ \text{Follow}(X)$
	- "The first terminal of $\beta$ must exist in the [[follow set]] of $X$"
- $\text{Follow}(Y ) ⊆ \text{Follow}(X)$ if $\text{Nullable}(β)$ **IMPORTANT**
	- All the follow elements from $Y$ are passed to $X$ if the following non- or terminal is Nullable.
$$
\begin{align}
M & \implies \alpha N \color{gray}\beta\\
S' & \implies \gamma M\color{green}\delta \\
 & \implies \gamma \alpha N\color{gray}\beta \color{green}\delta
\end{align}
$$
	- This means that also $First(\delta) \subseteq Follow(N)$ when $Nullable(\beta)$
	- e.g. $\beta$ is nullable when: $β = ϵ$

> [!IMPORTANT]
> If X occurs multiple times on the right-hand side of a production, *each occurrence contributes with its own constraints!*

![[Pasted image 20260611220823.png]]

## Calculations
1. Extend the grammar:
Add $S' \to S \$$ where $S$ is the starting nonterminal.
2. For every right hand side occurrence of nonterminal $N$, do the following.
I.e. where $M \to \alpha N \beta$ (where $\alpha, \beta$ may be sequences og grammar symbols - or empty)
	2.1. Let $m = First(\beta)$. If $m \not= Ø$, then add the constraint $m \subseteq Follow(N)$ to the set of constraints
	2.2. If $M \not = N$ and $Nullable(\beta)$, add the constraint $Follow(M) \subseteq Follow(N)$.
	If $\beta$ is empty, $Nullable(\beta)$ is true.
3. Solve the constraints:
	3.1. Start with empty sets for $Follow(N)$ for all nonterminals
		except for $S$ which doesn't have a follow set.
	3.2. For each constraint of the form $m \subseteq Follow(N)$ (seeds), add the contents of $m$ to $Follow(N)$
	3.3. Iterate until no changes: for each prop form ($Follow(M) \subseteq Follow(N)$), add contents of $Follow(M)$ to $Follow(N)$
### Example
![[Pasted image 20260611221332.png]]


| Iter | S          | B          | Explained                                           | Step |
| ---- | ---------- | ---------- | --------------------------------------------------- | ---- |
| Init | `Ø`        | `Ø`        | All follow sets are initialized to `Ø`              | -    |
| 1    | `{ b, $ }` | `Ø`        | Both `$` and `b` immediately follow `S`             | 2.1  |
| 2    | `{ b, $ }` | `{ b, $ }` | Since `S -> B`, `Follow(S)` is added to `Follow(B)` | 3.3  |
| 3    | `{ b, $ }` | `{ b, $ }` | No changes, end process                             | 3.3  |


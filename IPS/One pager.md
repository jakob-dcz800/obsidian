# Context-free grammars

Like [[regular expressions]], context-free grammars describe sets of strings, i.e., languages

>[!QUESTION]
>What is the right-hand side of a production?
>See [slides](file:///C:/Users/jakis/Documents/Datalogi/IPS/lectures/9-SyntaxAn.pdf) page 33/61

## Terminals
A context-free grammar also defines structure on the strings in the language it defines. 
A language is defined over some alphabet, for example the set of tokens produced by a lexer or the set of alphanumeric characters. 
The symbols in the alphabet are called **terminals**.

A context-free grammar recursively defines several sets of strings.
Each set is denoted by a name, which is called a **nonterminal**.
The set of nonterminals is [[Disjoint sets|disjoint]] from the set of terminals.

## Ambiguity

The grammar is said to be ambiguous if there exists a word that can be derived in two ways corresponding to different syntax trees

![[Pasted image 20260611172901.png]]

> [!TIP] You can't decide if a grammar is ambiguous
> Ambiguity is in general undecidable, i.e., there is no method that for any grammar can answer the question “Is this grammar ambiguous?”
> However, in many cases, it is not difficult to detect & prove ambiguity.
>For example, 
>$$N → NαN \mid β$$
> is ambiguous, where α and β are any sequences of grammar symbols.
> $N$ exists both right and left of $\alpha$
### Example
![[Pasted image 20260611173451.png|174]]Very ambiguous grammar

## Defining Operator Associativity

- Left-associative if expression $x ⊕ y ⊕ z$ should be grouped from left to right: 
$$
(x ⊕ y) ⊕ z
$$
	- + and /

- Right-associative if expression $x ⊕ y ⊕ z$ should be grouped from right to left: 
$$
x ⊕ (y ⊕ z)
$$
	- exponentiation ^, assignment :=
- Non-associative if expressions such as $x ⊕ y ⊕ z$ are disallowed
	- relational < and =
- Associative if both left-to-right and right-to-left groupings lead to the same result (a semantic property).


## Resolving Operator Associativity by Recursion

![[Pasted image 20260611174549.png]]

### Equal precedence level
![[Pasted image 20260611174829.png]]

If two productions have different precedence levels, do **not** put them on the same non-terminal:

![[Pasted image 20260611174945.png]]

![[Pasted image 20260611175020.png]]

## Resolving Operator Precedence

> At grammar level: This can be accomplished by introducing one nonterminal for each level of precedence.

![[Pasted image 20260611175208.png]]

Finally, one can resolve associativity as discussed [[#Resolving Operator Associativity by Recursion|before]]
>At grammar level: This can be accomplished by introducing new nonterminals that establish associativity by recursion type:

![[Pasted image 20260611175315.png]]


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

# Syntax Analysis

> Aka. parsing

recombine tokens from the [[Lexical Analysis]]
Not back into a list of characters, but into something that reflects the structure of the text
This “something” is typically a data structure called the [[syntax tree]] of the text

In addition to finding the structure of the input text, the syntax analysis must also reject invalid texts by reporting **syntax errors**.

As [[syntax analysis]] is less local in nature than [[lexical analysis]], more advanced methods are required. We, however, use the same basic strategy: A notation suitable for human understanding and algebraic manipulation is transformed into a machinelike low-level notation suitable for efficient execution. This process is called parser generation.

The notation we use for human manipulation is context-free grammars, which is a recursive notation for describing sets of strings and imposing a structure on each such string.

# Syntax tree

As the name indicates, this is a tree structure. The leaves of this tree are the tokens found by the [[lexical analysis]], and if the leaves are read from left to right, the sequence is the same as in the input text.
# Syntax trees

Syntax trees describe the “structure” of the derivation (independent of the order in which nonterminals have been chosen to be derived)

Leftmost derivation always derives the leftmost nonterminal first, and corresponds to a depth-first, left-to-right tree traversal:

![[Pasted image 20260611172646.png]]
![[Pasted image 20260611172704.png]]

# Data-Flow Equations

For faster convergence compute in reverse: 
`in[i + 1]` before `out[i]`, and `out[i]` before `in[i]` (backward data-flow analysis).
$$
in[i] = gen[i] \cup (out[i] \setminus kill[i])
$$
$$
out[i] = \bigcup_{j \in succ[i]}in[j]
$$

| fib(n) | Instruction                             | `succ[i]` | `gen[i]` | `kill[i]` |
| ------ | --------------------------------------- | --------- | -------- | --------- |
| 1      | `a := 0`                                | 2         |          | `a`       |
| 2      | `b := 1`                                | 3         |          | `b`       |
| 3      | `z := 0`                                | 4         |          | `z`       |
| 4      | `LABEL loop`                            | 5         |          |           |
| 5      | `IF n = z`<br>`THEN end`<br>`ELSE body` | 6, 13     | `n, z`   |           |
| 6      | `LABEL body`                            | 7         |          |           |
| 7      | `t := a + b`                            | 8         | `a, b`   | `t`       |
| 8      | `a := b`                                | 9         | `b`      | `a`       |
| 9      | `b := t`                                | 10        | `t`      | `b`       |
| 10     | `n := n − 1`                            | 11        | `n`      | `n`       |
| 11     | `z := 0`                                | 12        |          | `z`       |
| 12     | `GOTO loop`                             | 4         |          |           |
| 13     | `LABEL end`                             | 14        |          |           |
| 14     | `RETURN a`                              |           | `a`      |           |

## In
`in[i]` = variables that must already have a value before instruction `i` executes, because that value may be needed later.

For example, at instruction 6, `z` is not in `in[6]` even though it was assigned earlier, because after the branch decision at instruction 5, the value of `z` is never used along the path through the loop body.

### First iteration

| fib(n) | Instruction                   | `in[i]`      | explained                                                                                                                   |
| ------ | ----------------------------- | ------------ | --------------------------------------------------------------------------------------------------------------------------- |
| 1      | `a := 0`                      | `n`          | `n` must be available because <br>it is used later in the loop condition <br>and decrement operation.                       |
| 2      | `b := 1`                      | `n, a`       | `n` is needed later; `a` is needed <br>later by `t := a + b` before `a` <br>is redefined.                                   |
| 3      | `z := 0`                      | `n, a, b`    | `n` is needed later; `a` and `b` are <br>needed later by `t := a + b`.                                                      |
| 4      | `LABEL loop`                  | `n, z, a, b` | The next instruction compares `n` <br>and `z`; `a` and `b` may be needed <br>if execution continues into the loop body.     |
| 5      | `IF n = z THEN end ELSE body` | `n, z, a, b` | `n` and `z` are used immediately <br>by the test; on the `body` branch, <br>`a` and `b` are still needed for computing `t`. |
| 6      | `LABEL body`                  | `a, b, n`    | `a` and `b` are needed by the next <br>instruction (`t := a + b`); `n` remains <br>live because it is decremented later.    |
| 7      | `t := a + b`                  | `a, b, n`    | `a` and `b` are used immediately to <br>compute `t`; `n` is still needed later <br>by `n := n - 1`.                         |
| 8      | `a := b`                      | `b, t, n`    | `b` is needed to perform the assignment; <br>`t` will be needed by `b := t`; <br>`n` is needed later.                       |
| 9      | `b := t`                      | `t, n`       | `t` is needed immediately to update `b`; <br>`n` is needed later by the decrement.                                          |
| 10     | `n := n − 1`                  | `n`          | The current value of `n` is needed to <br>compute the new value `n - 1`.                                                    |
| 11     | `z := 0`                      | _(empty)_    | No variable value is required before <br>this instruction; it overwrites `z` with <br>a constant.                           |
| 12     | `GOTO loop`                   | _(empty)_    | The jump itself uses no variables. <br>(Variables become live again only <br>after control reaches instruction 4)           |
| 13     | `LABEL end`                   | `a`          | `a` must be preserved because it is <br>returned immediately afterward.                                                     |
| 14     | `RETURN a`                    | `a`          | `a` is used directly by the return statement.                                                                               |
One subtle point: **`in[i]` is not "variables assigned previously."** It is **"variables whose current values are still needed."**
## Out
**`out[i]`** = variables that must have correct values **immediately after** instruction `i`.

>[!TIP]
>The `out[i]` sets are the union of the `in[i]` sets of the instructions successors:
>$$
out[i] = \bigcup_{j \in succ[i]}in[j]$$


| fib(n) | Instruction                   | `in[i]`      | `succ[i]` | `out[i]`     | Explainer               |
| ------ | ----------------------------- | ------------ | --------- | ------------ | ----------------------- |
| 1      | `a := 0`                      | `n`          | 2         | `n, a`       |                         |
| 2      | `b := 1`                      | `n, a`       | 3         | `n, a, b`    |                         |
| 3      | `z := 0`                      | `n, a, b`    | 4         | `n, z, a, b` |                         |
| 4      | `LABEL loop`                  | `n, z, a, b` | 5         | `n, z, a, b` |                         |
| 5      | `IF n = z THEN end ELSE body` | `n, z, a, b` | 6, 13     | `a, b, n`    | `a` is both in 6 and 13 |
| 6      | `LABEL body`                  | `a, b, n`    | 7         | `a, b, n`    |                         |
| 7      | `t := a + b`                  | `a, b, n`    | 8         | `b, t, n`    |                         |
| 8      | `a := b`                      | `b, t, n`    | 9         | `t, n`       |                         |
| 9      | `b := t`                      | `t, n`       | 10        | `n`          |                         |
| 10     | `n := n − 1`                  | `n`          | 11        | _(empty)_    |                         |
| 11     | `z := 0`                      | _(empty)_    | 12        | _(empty)_    |                         |
| 12     | `GOTO loop`                   | _(empty)_    | 4         | _(empty)_    |                         |
| 13     | `LABEL end`                   | `a`          | 14        | `a`          |                         |
| 14     | `RETURN a`                    | `a`          |           | _(empty)_    |                         |

## Further iterations

>[!TIP]
>$$in[i] = gen[i] \cup (out[i] \setminus kill[i])$$


| `succ[i]` | `gen[i]` | `kill[i]` | `out[i]:1`   | `in[i]:2`    | explained                         |
| --------- | -------- | --------- | ------------ | ------------ | --------------------------------- |
| 2         |          | `a`       | `n, a`       | `n`          |                                   |
| 3         |          | `b`       | `n, a, b`    | `n, a`       |                                   |
| 4         |          | `z`       | `n, z, a, b` | `n, a, b`    |                                   |
| 5         |          |           | `n, z, a, b` | `n, z, a, b` |                                   |
| 6, 13     | `n, z`   |           | `a, b, n`    | `n, z, a, b` |                                   |
| 7         |          |           | `a, b, n`    | `a, b, n`    |                                   |
| 8         | `a, b`   | `t`       | `b, t, n`    | `a, b, n`    | `t` is in `kill` and not included |
| 9         | `b`      | `a`       | `t, n`       | `b, t, n`    |                                   |
| 10        | `t`      | `b`       | `n`          | `t, n`       |                                   |
| 11        | `n`      | `n`       | _(empty)_    | `n`          |                                   |
| 12        |          | `z`       | _(empty)_    |              |                                   |
| 4         |          |           | _(empty)_    |              |                                   |
| 14        |          |           | `a`          | `a`          |                                   |
|           | `a`      |           | _(empty)_    | `a`          |                                   |

# Liveness analysis

## Rules for Liveness
1. `var` is **live at the start** of instruction `I` when the value of a variable var is **used** in instruction `I`.
```fsharp
I: a := a + var // var is live at the start
```

2. If `var` is assigned a value in instruction `I` (and (1) does not apply) then `var` is **dead at the start** of `I`.
```fsharp
I: var := b // var is dead at the end
```

3. If `var` is **live at the end** of instruction `I` then it is live at the start of `I` 
	1. (unless `I` assigns to `var`)

4. If `var` is live at the end of instruction `I`, then `var` is **live at the start** of any instruction that may be executed **directly after** `I`.

## Concepts
> We number program instructions from $i = 1$ to $n$.

For each instruction we define the following sets:

| Set       | Meaning                                                                                      |
| --------- | -------------------------------------------------------------------------------------------- |
| `succ[i]` | The numbers of all **instructions** that may be executed **directly after** instruction `i`. |
| `gen[i]`  | The set of **variables** whose values are **read** by instruction `i`.                       |
| `kill[i]` | The set of variables that are **overwritten** by instruction `i`.                            |
| `in[i]`   | The set of variables that are **live at the start** of instruction `i`.                      |
| `out[i]`  | The set of variables that are **live at the end** of instruct `i`.                           |
In the end, what we need is `out[i]` for all instructions.

## Constructing `succ` Sets

- `succ[i] = {i + 1}` unless instruction i is `GOTO`, `IF`, or `RETURN`.	
- `succ[i] = {j}`, 
	- if instruction `i` is `GOTO x` 
	- and instruction `j` is `LABEL x`.
- `succ[i] = {j, k}`, 
	- if instruction `i` is `IF c THEN l1 ELSE l2`, 
	- instruction `j` is `LABEL l1` 
	- and instruction `k` is `LABEL l2`
- `succ[i] = ∅`, if instruction `i` is `RETURN x`.

## Constructing `gen` and `kill` Sets

Below, `k` denotes a constant, `M[...]` denotes memory access.

| Instruction `i`                | `gen[i]` | `kill[i]` | Explained                                           |
| ------------------------------ | -------- | --------- | --------------------------------------------------- |
| `LABEL l`                      | `Ø`      | `Ø`       |                                                     |
| `x := y`                       | `{y}`    | `{x}`     |                                                     |
| `x := k`                       | `Ø`      | `{x}`     |                                                     |
| `x := unop y`                  | `{y}`    | `{x}`     |                                                     |
| `x := unop k`                  | `Ø`      | `{x}`     |                                                     |
| `x := y binop z`               | `{y, z}` | `{x}`     |                                                     |
| `x := y binop k`               | `{y}`    | `{x}`     |                                                     |
| `x := M[y]`                    | `{y}`    | `{x}`     |                                                     |
| `x := M[k]`                    | `Ø`      | `{x}`     |                                                     |
| `M[x] := y`                    | `{x, y}` | `Ø`       | `x` is also used as a variable <br>to access memory |
| `M[k] := y`                    | `{y}`    | `Ø`       |                                                     |
| `GOTO l`                       | `Ø`      | `Ø`       |                                                     |
| `IF x relop y THEN lt ELSE lf` | `{x, y}` | `Ø`       |                                                     |
| `x := CALL f (args)`           | `args`   | `{x}`     | `args` are variables too                            |
| `RETURN x`                     | `{x}`    | `Ø`       |                                                     |

# Bottom-Up Parsing

Builds syntax tree from the leaves going up.

- Search for parts of input string that match right-hand side of productions and rewrite these to left-hand side nonterminals, 
- [[Syntax tree]] is completed when the string has been rewritten by the inverse rightmost derivation to the start symbol. 

- Also called shift-reduce parsing: shifts input to stack, 
- then reduces right-hand side to left-hand side nonterminal, 
- until the start symbol is reached.

>[!tip]
>Uses a stack to keep track of the derivation sequence.

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

# Look-ahead 1

Used in [[Top-Down Parsing]]

>[!definition] LL(1)
>An LL(1) parser requires computation of the: 
>- [[Nullable Property|Nullable]] and [[First Set|First sets]] for all right-hand sides of prods, 
>- [[Follow Set|Follow sets]] for all nonterminals.

## Process
![[Pasted image 20260611183357.png]]

Compute info to choose the correct production:
- For each right-hand side: *What input token may come first?*
- Pay attention to empty right-hand sides: *What may follow?*

Choose a production $N → α$ by a look-ahead of 1 token if:
1. look-ahead = $c$ and $α ⇒^∗ cβ$ , or
2. look-ahead = $c$ and $α ⇒^∗ ϵ$ and $c$ can follow $N$.

## Constructing a LL(1) parsing table
With a grammar like this, start with the bottom production.
We find the [[First Set|first]] and follow sets

|             | First     | Follow   |
| ----------- | --------- | -------- |
| S -> aABb   | { a }     | { $ }    |
| A -> c \| ε | { c, ε }  | { d, b } |
| B -> d \| ε | { d,  ε } | { b }    |
> S does not appear in the [[Follow Set|following sets]], so we note $ in Follow
 >A can be followed by a $d$ or a $b$ if $b$ is ε.
 
|     | a         | b      | c      | d      | $   |
| --- | --------- | ------ | ------ | ------ | --- |
| S   | S -> aABb |        |        |        |     |
| A   |           | A -> ε | A -> c | A -> ε |     |
| B   |           | B -> ε |        | B -> d |     |
1. S does not produce ε, so the follow set $ is ignored
2. A *can* be written as ε, therefore A -> ε is written in col b, d (follow sets)

## Example
### Grammar simplification
Original [[Context-free grammars|grammar]] & operator conventions:
`E -> num | E + E | E * E | ( E )`

>   * binds tighter than +, and both associate to the left
**Disambiguated grammar:**
```haskell
E -> E + T | T
T -> T * F | F
F -> num | ( E )
```

**Grammar without left-recursion:**
```haskell
E -> T E'
E' -> + T E' | eps

T -> F T'
T' -> * F T' | eps

F -> num | ( E )
```

**New start symbol, numbered productions:**
```haskell
0    S  ->  E $
1    E  ->  T E'
2a   E' ->  + T E'
2b   E' ->  eps
3    T  ->  F T'
4a   T' ->  * F T'
4b   T' ->  eps
5a   F  ->  num
5b   F  ->  ( E )
```

**Computing `nullable(N)` (abbreviated as `null(N)`) for all `N`:**
```haskell
null(S)  = false                   --[always, because of the $]
null(E)  = null(T) && null(E')
null(E') = null(+ T E') || null(eps) = false || true = true
null(T)  = null(F) && null(T')
null(T') = null(* F T') || null(eps) = false || true = true
null(F)  = null(num) || null( ( E ) ) = false || false = false
```

> `null(+ T E') = false` after rule 3, all non- or terminals must be nullable
> `null(E)` uses rule 3 (`&&`), since `E` only has 1 production,
> `null(E')` uses rule 4 (`||`), since `E'` has more productions

**Simplifying:**
```haskell
null(T) = null(F) && null(T') = false && true = false
null(E) = null(T) && null(E') = false && true = false
```

> Here, we simplify productions with a single production (which use rule 3), by using the result of the productions with more instances (using rule 4).

**Computing `first(N)` for all `N`:**
```haskell
first(S)  = first(E $)    = first(E)      --[since !null(E)]
first(E)  = first(T E')   = first(T)      --[since !null(T)]
first(E') = first(+ T E') U first(eps)  = {+} U {} = {+}
first(T)  = first(F T')   = first(F)      --[since !null(F)]
first(T') = first(* F T') U first(eps)  = {*} U {} = {*}
first(F)  = first(num) U first( ( E ) ) 
          = {num} U { ( } = { num, ( }
```

>Rows 1, 2 & 4 use [[First Set#Recursive Rules for First|rule 3]]
>Rows 3, 5 use [[First Set#Recursive Rules for First|rule 4]]
>On row 3: `first(+ T E') = { + }` by rule 2 and 3

**Simplifying further:**
```haskell
first(T) = first(F) = {num, (}
first(E) = first(T) = first(F) = {num, (}
first(S) = first(E) = first(T) = first(F) = {num, (}
```

>Here, we simplify productions that aren't fulfilled (they all use rule 3 above)
### Computing `follow(N)` for all `N`:
**Generating constraints:**
> This is done for each *unique* production

  (0)   `S -> E $`
```haskell
1. {$} <= follow(E)              --[because first($) = {$}]
```
>[[Follow Set#Recursive Rules for Follow|Constraint 1]] is used
>"{ $ } is in follow set of E"

  (1)   `E -> T E'`
```haskell
2. {+} <= follow(T)         --[because first(E') = {+}]
3. follow(E) <= follow(T)   --[because nullable(E')]
4. follow(E) <= follow(E')  --[because E' last in production]
```
> "{ + } is in follow set of T"
> "The follow set of E is in the follow set of T"

  (2a)  `E' -> + T E'`
```haskell
{+} <= follow(T)            --[because first(E') = {+}, copy of 2.]
5. follow(E') <= follow(T)  --[because nullable(E')]
follow(E') <= follow(E')    --[because E' last in production, trivial]
```

  (2b)  `E' -> eps`

  (3)   `T -> F T'`
```haskell
6. {*} <= follow(F)         --[because first(T') = {*}]
7. follow(T) <= follow(F)   --[because nullable(T')]
8. follow(T) <= follow(T')  --[because T' last in production]
```

  (4a)  `T' -> * F T'`
```haskell
{*} <= follow(F)            --[because first(T') = {*}, copy of 6.]
9. follow(T') <= follow(F)  --[because nullable(T')]
follow(T') <= follow(T')    --[because T' last in production, trivial]
```

  (4b)  `T' -> eps`

  (5a)  `F -> num`

  (5b)  `F -> ( E )`
```haskell
10. { ) } <= follow(E)        --[because first( ) ) = { ) }]
```

### Finding least solution:
Seed rules 
```haskell
{ a1, .. ,an } <= follow(N): 
-- rules: 1., 2., 6., 10.
```
>These terminals a1 to an are in some follow set

Propagation rules 
```haskell
follow(N1) <= follow(N2): 
-- rules: 3., 4., 5., 7., 8., 9.
```
> The follow sets of some non terminals may be in the set of another

| Set          | Seed              | Prop 1                   | Final     |
| ------------ | ----------------- | ------------------------ | --------- |
| `follow(E)`  | `$ [1.], ) [10.]` |                          | `$ )`     |
| `follow(E')` |                   | `$ [4.], ) [4.]`         | `$ )`     |
| `follow(T)`  | `+ [2.]`          | `$ [3.], ) [3.]`         | `$ ) +`   |
| `follow(T')` |                   | `+ [8.], $ [8.], ) [8.]` | `$ ) +`   |
| `follow(F)`  | `* [6.]`          | `+ [7.], $ [7.], ) [7.]` | `$ ) + *` |

>Seed are the direct pointers to which set a non terminal is in
>Prop, is when the follow set is propagated (once maybe?)

**Look-ahead sets:**
```haskell
la(S -> E $) = first(E)                  = { num, ( }
la(E -> T E') = first(T)                 = { num, ( }
```
```haskell
la(E' -> + T E') = first(+ T E)          = { + }
la(E' -> eps) = first(eps) U follow(E')  = { $, ) }
--[ok: la sets are disjoint!]
```
```haskell
la(T -> F T') = first(F)                 = { num, ( }
```
```haskell
la(T' -> * F T') = first(* F T')         = { * }
la(T' -> eps) = first(eps) U follow(T')  = { $, ), + }
--[ok: la sets are disjoint!]
```
```haskell
la(F -> num) = first(num)                = { num }
la(F -> ( E )) = first( ( E ) )          = { ( }
--[ok: la sets are disjoint!]
```

### LL(1) table

|     | num    | (       | )     | +        | *        | $     |
| --- | ------ | ------- | ----- | -------- | -------- | ----- |
| S   | `E $`  | `E $`   |       |          |          |       |
| E   | `T E'` | `T E'`  |       |          |          |       |
| E'  |        |         | `eps` | `+ T E'` |          | `eps` |
| T   | `F T'` | `F T'`  |       |          |          |       |
| T'  |        |         | `eps` | `eps`    | `* F T'` | `eps` |
| F   | `num`  | `( E )` |       |          |          |       |

**Table-driven LL(1) parsing of `num * num`:**

| Input       | Stack         | Explainer                           |
| ----------- | ------------- | ----------------------------------- |
| num * num $ | `S`           | `S` becomes `E  $`                  |
| num * num $ | `E  $`        | `E` becomes `T E'`                  |
| num * num $ | `T  E' $`     | `T` becomes `F T'`                  |
| num * num $ | `F T' E' $`   | `F` becomes `num`                   |
| num * num $ | `num T' E' $` | `num` is ingested                   |
| * num $     | `T' E' $`     | `*` from the input becomes `* F T'` |
| * num $     | `* F T' E' $` | `*` is ingested                     |
| num $       | `F T' E' $`   | `F` becomes `num`                   |
| num $       | `num T' E' $` | `num` is ingested                   |
| $           | `T' E' $`     | `T` becomes `eps`                   |
| $           | `E' $`        | `E'` becomes `eps`                  |
| $           | `$`           | `$` from the input becomes `eps`    |

# Look ahead set

![[Pasted image 20260612190229.png]]

## Example
### Not LL(1)
![[Pasted image 20260612190325.png]]

>[!Question] Why is this not LL(1)?
>🤷
### LL(1)
![[Pasted image 20260612190338.png]]


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

# Top-Down Parsing

Builds [[syntax tree]] from the root going down.
Also called *predictive parsing*: guesses the to-be-used production.
Reads Left-to-right, uses Leftmost derivation, look-ahead 1: [[LL(1)]]

>[!tip]
>Uses a stack to keep track of the derivation sequence.

## Example

We have two productions:
```
T -> aTc
T -> R
```

As long as the input is `b` we choose `T` nr. 2
For input `a` we of course choose the first `T`
This method extends do more productions that start with terminals.
Here, we find the [[first set|first sets]]. These describe the initial characters that each production produce.
To calculate `FIRST` we need a new auxillary function called [[Nullable Property|nullable]]
This indicates if a sequence of grammar symbols $\alpha$ can derive the empty string.

>[!definition]
>$\alpha$ and $\beta$ are sequences of grammar symbols

# Predictive parsing

If the same nonterminal has productions with *disjoint* [[First Set|first sets]], then we can choose the corresponding production if the input char exists in one of the sets. If it doesn't we choose the empty production, if such production exists.

>[!DEFINITION] Generalized rule
>If the next input does **not** exist in any [[first set]], we can choose the [[Nullable Property|nullable]] production.
>Nullable productions can have non-empty first sets, so it can also be chosen if the next input is in its first set.

If there are many nullable productions, we cannot pick one - therefore for predictive parsing, a nonterminal must have at most one nullable production.

[[Follow Set|Follow sets]] are used to choose which nullable nonterminal to choose in predictive parsing.

# Converting to a DFA

## Subset construction

## Example

We have our sets from the [[epsilon closure]].

| DFA State | Epsilon closure              | Set                         |
| --------- | ---------------------------- | --------------------------- |
| E         | $\hat{\epsilon}(Ø)$          | $\set{Ø}$                   |
| S         | $\hat{\epsilon}(\set{1})$    | $\set{1, 2, 5, 6, 7}$       |
| A         | $\hat{\epsilon}(\set{8})$    | $\set{1, 2, 5, 6, 7, 8}$    |
| B         | $\hat{\epsilon}(\set{3, 8})$ | $\set{1, 2, 3, 5, 6, 7, 8}$ |
| C         | $\hat{\epsilon}(\set{4})$    | $\set{4}$                   |

## Tradeoff

![[Pasted image 20260611154256.png]]

# DFA

>[!DEFINITION] Definition
>Let Σ be an alphabet of (input) characters. A DFA consists of 
>- The alphabet $Σ$ of input characters, 
>- A finite set $S$ of states: 
>- A start (initial) state $s_0 ∈ S$ 
>- A set of final (accepting) states $F ⊆ S$, and 
>- A function **move** : $S × Σ ⇀ S$ describing state transitions. 
>	($⇀$ means that $S$ may be *undefined*)

## Move

$$
\text{move}(s_1,c) = s_2
$$

If in state $s_1$ with input character $c$, go to $s_2$

> [!Note] 
> $\text{move}(s_1,c)$ can be undefined, i.e., is a partial function.

No $ϵ$ transitions, no 2 identically labelled transitions from a state.

>[!IMPORTANT] Important
>**At most one** transition possible from any state, uniquely identified by current state & input char.

## Dead states

A dead state is a state from which no accepting state can be reached.
They do not occur in [[DFA]]'s constructed from [[NFA]]'s with no dead states.

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

# Minimizing a DFA

## Process

1. Group accepting and non-accepting states.
2. For each group:
	1. Note for each character in the alphabet ($\sum$) which group the outward arrow points to.
	2. All states in the group must point to the same pairs of groups
	3. Otherwise split the group into new groups and repeat the process for each group until all groups are homogenous.
3. Note each group and its members.

> [!QUESTION] Question
> How do i pre-process the DFA by making [[DFA#Move|the move function]]  total?

>[!DEFINITION] Total move function
> The `move` function is total when there are transitions on all symbols from all states *or* when there are no [[DFA#Dead states|dead states]] in the [[DFA]].
> Dead states might make a group *inconsistent*, when in fact it is not
> >[!IMPORTANT] Remove dead states
> >It is important to remove dead states - and you can simply remove them intirely.


## Example 1 - Dead state

![[Pasted image 20260611165521.png|637]]

Here, see that 4 is a dead state.
You *could* simply remove it, but the task requires us to not do so.

```
Accepting states
G1 = { 1 }
Non-accepting states
G2 = { 2, 3, 4, 5, 6 }
```

---

| ✅ G1 | a   | b   | c   |
| ---- | --- | --- | --- |
| 1    | G2  | G2  | G2  |

| ✅ G6 | a   | b   | c   |
| ---- | --- | --- | --- |
| 6    | -   | -   | G1  |

| ✅ G5 | a   | b   | c   |
| ---- | --- | --- | --- |
| 5    | G5  | G6  | G4  |

| ✅ G4 | a   | b   | c   |
| ---- | --- | --- | --- |
| 4    | G4  | -   | -   |

| ✅ G7 | a   | b   | c   |
| ---- | --- | --- | --- |
| 3    | G4  | G4  | -   |

| ✅ G8 | a   | b   | c   |
| ---- | --- | --- | --- |
| 2    | G5  | G6  | -   |

---

| ❌ G3 | a   | b   | c   |
| ---- | --- | --- | --- |
| 3    | G4  | G4  | -   |
| 2    | G5  | G6  | -   |

| ❌ G2 | a   | b   | c   |
| ---- | --- | --- | --- |
| 2    | G2  | G2  | -   |
| 3    | G2  | G2  | -   |
| 4    | G2  | -   | -   |
| 5    | G2  | G2  | G2  |
| 6    | -   | -   | G1  |

---

| Group | Members | a   | b   | c   |
| ----- | ------- | --- | --- | --- |
| 1     | { 1 }   | 2   | 2   | 2   |
| 4     | { 4 }   | 4   | -   | -   |
| 5     | { 5 }   | 5   | 6   | 4   |
| 6     | { 6 }   | -   | -   | 1   |
| 7     | { 3 }   | 4   | 4   | -   |
| 8     | { 2 }   | 5   | 6   | -   |

## Example 2
![[Pasted image 20260611162930.png|377]]

```
Accepting states
G1 = { 3 }
Non-Accepting states
G2 = { 1, 2, 4, 5, 6, 7, 8 }

G1 | 0  | 1  |
---+----+----|
3  | G2 | G2 |


G2 | 0  | 1  |
---+----+----|
1  | G2 | G2 |
2  | G2 | G1 |
4  | G1 | G2 |
5  | G2 | G2 |
6  | G1 | G2 |
7  | G2 | G2 |
8  | G2 | G1 |
G2 is Not consistent

G1 = { 3 }
G3 = { 1, 5, 7 }    --2, 2
G4 = { 4, 6 }       --1, 2
G5 = { 2, 8 }       --2, 1

We pick G3 for consideration

G3 | 0  | 1  |
---+----+----|
1  | G4 | G4 |
5  | G4 | G4 |
7  | G3 | G3 |
G3 is Not consistent


G1 = { 3 }      -m
G4 = { 4, 6 }   -m
G5 = { 2, 8 }   -m
G6 = { 1, 5 }   -m    
G7 = { 7 }      -m

We pick G4 for consideration

G4 | 0  | 1  |
---+----+----|
4  | G1 | G7 |
6  | G1 | G7 |
G4 is consistent, and we pick G5

G5 | 0  | 1  |
---+----+----|
2  | G7 | G1 |
8  | G7 | G1 |
G5 is consistent, and we pick G6

G6 | 0  | 1  |
---+----+----|
1  | G5 | G4 |
5  | G5 | G4 |
G6 is consistent

Thus, we have the groups:

G1 = { 3 }
G4 = { 4, 6 }
G5 = { 2, 8 }
G6 = { 1, 5 }    
G7 = { 7 }
```

# NFA

> [!DEFINITION] What is it?
> Nondeterministic Finite Automata
> Used to decide if the input string is a member of the language $L$:
> - Starting state
> - final states where execution ends if the input ∈ L, (accepting states),

![[Pasted image 20260611114048.png]]

A stepping stone towards implementing [[regular expressions]].
It is **nondeterministic** (there are many choices one can make to reach the same result)

Can be transformed to [[DFA]], which efficiently executes on real hardware

![[Pasted image 20260608163439.png|258]]
## Definition

An abstract machine with a finite number of 
- states: initial, final, intermediate, 
- transitions between states: labelled with a char $c \in \sum$ or with $\epsilon$

## Transitions

Used to reach a new state from the current state,
- either follow an $ϵ$ transition (no char of input is consumed) or
- consume the current char $c$ of the input and follow a transition labelled with $c$ from the current state (if such transition exists)

### Membership 
If there is a *possibility* to reach an accepting state after all input characters were consumed then $\text{input} ∈ L$ (input is in language).
*Possibility* refers to choices/guesses on what transition to follow!

>[!TIP] Acceptance
>If there exist a sequence of choices reaching an accepting state at the end of the input string.

### Notation for transitions:

$s_{i}^{c}s_{j} \in T$: may transition from state $s_i$ to $s_j$ on consuming char $c$
$s_{i}^{\epsilon}s_{j} \in T$: may freely transition from state $s_i$ to $s_j$
	(without consuming an input char)
Several options may exist, hence T is a relation.
**Acceptance**: if there exist a sequence of choices reaching an accepting state at the end of the input string.

# Converting Regex to NFA

Make a sort of tree of the expression.
A single final state is added at the end of the construction.

![[Pasted image 20260608161325.png]]

## Example 1

$$
(a\cdot b|a)\cdot(b|ε)
$$
![[Pasted image 20260608161624.png|412]]

## Example 2

![[Pasted image 20260608161728.png]]


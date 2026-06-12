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




---
tags:
  - DMA
  - Math
---

# Logik og beviser

A statement or proposition can be either true or false, but not both

In logic, $p$, $q$, $r$ are like mathematical variables, but these can be propositions that are either true or false
## Funktionspræfikser

Compound statements are bound by logical operators or **connectives**:
**Universal quantifier**: $\forall$ for all [variable] the following is true…
**Existential quantifier**: $\exists$ there exists one [variable] for which the following is true…

Let $Q(x):1+x < 4$ then $\exists x \enspace Q(x)$ is true

The order only matters for different quantifiers (e.g. when all quantifiers are $\forall$ you can switch them around)

### Predicates and quantifiers

| Symbol    | Explainer |
| --------- | --------- |
| $\exists$ | for some  |
| $\forall$ | for all   |
See [[Logik og beviser#Funktionspræfikser|quantifiers]]
Predicates have capitalized names: $Q(x), P(x), P(x, y)$

Example
$Q(x, y):x^2+y^2=4$

$\forall x \in S \> P(x)$ 
**Means**: for all $x$ in $s$, $P(x)$ is true (or holds)

$\exists x \in S \> P(x)$ 
**Means**: there exists an $x$ in $S$ such that $P(x)$ is true (or holds)

<mark class="hltr-red">The order matters for quantifiers</mark>
### Negation of quantifiers
for $q$ what is $\sim q$?
#### Example:
$S$: Set  of students who have made homework
$x$: Student

All students have made homework, is equivalent to: 
$\forall x \in S \> P(x)$
The negative statement: $\sim (\forall x \in S \> P(x))$

The correct negation is "NOT all students have made their homework"
We write it as: $(\exists x \in S \> \sim P(x))$

An incorrect negation is "All students have NOT made their homework"

Correct negation of statement:
$\sim (\forall x \in S \> P(x)) \equiv (\exists x \in S \> \sim P(x))$
And reverse
$\sim (\exists x \in S \> P(x)) \equiv (\forall x \in S \> \sim P(x))$

We negate the predicate and switch the “for all ( $\forall$ )” out with “there exists” ( $\exists$ ) and vice versa
#### Another example
![[Pasted image 20250308172833.png]]
## Logiske operatorer

Implication: $q \Rightarrow r$ means that if $q$ then $r$
Means that $q$ and $r$ will not be `true` and `false` (respectively) at the same time
It does not mean that $q$ causes $r$ or implies any cause and effect

*See page 57 KBR*

A **tautology** is always `true`
And **contradictions** or **absurdities** are always `false` ( $p \land \sim p$ )
A **contingency** can be `true` or `false`

`false` can imply `true`, but `true` cannot imply `false`

Right implication means:
hypothesis $\Rightarrow$ conclusion
### Contrapositive right implication
$p \Rightarrow q$ becomes $(\sim q) \Rightarrow (\sim p)$

If I'm tired I'm sleepy, when I'm sleepy I'm tired
*Switch and negate*
### Converse implication
Converse statement switches the logical 'variables' 
$p \Rightarrow q$ becomes $q \Rightarrow p$

This is **NOT** the same thing
"If it rains, i use my umbrella" becomes "If i use my umbrella, then it rains"
This is not logically equivalent
When writing $\equiv$ (equal to), we imply the values are `true`

$p$ if and only if $q$ is double implication: $p \iff q$

$\Rightarrow$ expressed as `nand` $\odot$ and $\sim$ only is:
$(p \Rightarrow q) \equiv (p \odot (\sim q))$
---
tags:
  - Math
  - DMA
---

# Induktionsbeviser

Induction is a method to prove that certain statements are true.

The method usually consist of 2 steps:
1. **Basis step** (or base case), here, we must prove that the statement is true for some arbitrary constant $n_0$
2. **Induction step**, (hard part)

Here, we use the [[Logik og beviser#Logiske operatorer|implication arrow]]: $\Rightarrow$
True cannot imply false, but all others are true

| $p$ | $q$ | $p \Rightarrow q$ |
| --- | --- | ----------------- |
| T   | T   | T                 |
| F   | T   | T                 |
| T   | F   | F                 |
| F   | F   | T                 |

Therefore we must prove that $P(k)$ and $P(k+1)$ is true.

<mark class="hltr-cyan">See KBR page 68</mark>

Induction hypothesis → we have checked for one value and can conclude that theorem must hold for at least **one** value

> [!Important]
> Remember to explain that you use mathematical induction, before and after the proof.
> By the principle of mathematical induction we've... 

$p \equiv q$ always have the same truth value, if the statements are logically equivalent. 

<mark class="hltr-cyan">Theorem 2.2.1 is very important</mark>

1) the order does not matter
2) the order does not matter
3) preference of ORs doesn't matter
4) preference of ANDs doesn't matter
5) 
6) 
7) 
8) double negation

## Stærk induktion

Strong induction includes **base case** and **induction step**

Here, we start by assuming $P(n_0)$ and $P(n) \Rightarrow P(n+1)$
We then have a stronger induction hypothesis
We must assert that all are true from $n_0$ to $n$

Identify starting value $n_0$

Example from class
	We assume all $P(n)$ work up till $n$ 
	Then we look at the $n - 2$ and conclude we can just add another $3$

## Invarianter

This is a property that is **preserved** throughout the procedure (e.g. loop)

Invariant: $xy=z$
Invariants are used to prove correctness in programs

A loop invariant could be: $P(n):x_n+y_n=c$, where $n$ is the number of steps in the loop
This is used to prove what value is terminated by the algorithm
If algorithm e.g. has if statements, analyse each case for the value $n + 1$
# Bevisteknikker

A proof is a rigorous argument of a series of statements
To prove a statement, we must understand the start, **assert assumptions** and **define what** we need to prove

Think up the end of the proof - *what* is required for statement to be true?

Otherwise use a proof strategy
**Justify every step**, add one step more than is necessary
## Proving an implication

$p \Rightarrow q$
### Direct proof of an implication
if $p$ is true, then $q$ holds
- assume $p$ holds
- manipulate $p$ to conclude that $q$ holds using **theorems** and **arguments**
### Proof by contrapositive statement
$(p \Rightarrow q)\equiv((\sim q) \Rightarrow (\sim p))$

Tell the reader what method is used
Then prove the **contrapositive statement** via a direct proof

#### Example from board:
Let us separately analyse cases when $n | a$ (case 1) and when $n|b$ (case 2)
Case 1
	if $n|a$, then $a=cn$ for $c\in \Bbb{Z}$ 
	So $ab = (an)|b =(cb)|n$ where $c\in \Bbb{Z}$
	Hence $n|(ab)$
Case 2
	Exercise
## Proving a biconditional statement

If $p$ and only if $q$
$(p \iff q) \equiv (p \Rightarrow q)\land(q \Rightarrow p)$

Here, we must first prove the $\Rightarrow$ statement, and subsequently the $\Leftarrow$ statement
### Example
Show that:
	$a$ is even $\iff a^2$ is even
Case $\Rightarrow$
	On slides
Case $\Leftarrow$
	We will show that if $a^2$ is even, then $a$ is even. 
	We will prove the **contrapositive**:
	If $a$ is odd, then $a^2$ is odd
	We assume that $a$ is odd, so we write $a = 2k + 1$
	Now $a^2 = (2k + 1)^2 = 4k^2+ 4k+1 = 2(2k^2+2k)+1$
	Since $2k^2+2k\in \Bbb{Z}$, we have proved that $a^2$ is odd as desired
## Proof by contradiction

Bevis ved modstrid
Contrapositive (EN) = Kontrapositiv (DK)

Tell the reader the method

We want to prove that q holds
Then assume $\sim q$ holds
Arrive at a contradiction

### Example
Show that:
	$\sqrt{2}$ is irrational
Case $\sim q$, that $\sqrt{2}$ is rational
	First, we assume that $\sqrt{2}$ is rational
	So we can write is as $\sqrt{2}=\frac{a}{b}$, for $a, b \in \Bbb{Z}^+$
	Moreover, we can choose $a, b \in \Bbb{Z}^+$, so that $GCD(a, b) = 1$ 
		([[Hele tal#GCD / Euclid's algorithm|read about GCD]])
	Squaring both sides yields $2 = \frac{a^2}{b^2}$ 
	So $2b^2=a^2$, which means that $a^2$ is even
	By claim 1, $a$ is even
	So $a^2$ is divisible by $4$, and thus $2b^2$ is divisible by $4$
	Hence, $b^2$ is divisible by $2$, and is thus by claim 1 even
	We have shown, that $2|a$ and $2|b$ 
	This **contradicts** our choice of $a$ and $b$, such that $GCD(a, b) = 1$ 
	So $\sqrt{2}$ cannot be rational
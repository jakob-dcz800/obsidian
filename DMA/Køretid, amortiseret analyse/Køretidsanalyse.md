---
tags:
  - DMA
  - Math
---

# Køretidsanalyse

<mark class="hltr-cyan">CLRS side 55 er guld</mark>
## Vigtigheden af hurtige algoritmer

Vi kan se hvor meget hurtigere eller langsommere T1 er end T2:

$\frac{T1}{T2}$= forholdet mellem de to

Vi er ligeglade med konstanter fordi:

- kommer an på hvordan vi tæller - det er besværligt at definere konstanterne for sig
- I praksis er det forskelligt fra computer til computer - det vil altså ikke sige noget om hvor lang tid det faktisk tager
- Forskellige sprog har forskellige konstanter
- $\Theta$ - den asymptotiske stigning er den vigtige
- Nogle algoritmer har nogle meget store konstanter og her vil det måske være relevant

## Asymptotic notation

$\Omega$, $O$, $\Theta$

Asymptotically positive functions output  $\Bbb{R}^+$.
$100-x^3$ isn’t asymptotically positive

### Asymptotically positive functions
We say that a function 
$f : \Bbb{R}^+ → \Bbb{R}$ is **asymptotically positive** if there exists $x_0 ∈ \Bbb{R}^+$ such that $0 < f(x)$ for all $x ≥ x_0$ 

We will also apply the above definition for functions that are defined on some subset of the positive reals. A common choice of such a subset will be positive integers $\Bbb{Z}^+$ or natural numbers $\Bbb{N}$.
## Theta

**Formal definition**: 
$f(x)$ is $Θ(g(x))$ if there exist constants $c1, c2 > 0$ and $x_{0}$ such that $$c_{1}g(x) ≤ f(x) ≤ c_{2}g(x)$$ for all $x ≥ x_{0}$
$g$ and $f$ **grow at the same rate** asymptotically

Big-O both ways, the functions grow at the same rate:
$f = O(g)$
$g = O(f)$
→ $f = g$

## Big-O

**Formal definition**:
$f(x)$ is $O(g(x))$ if there exists a constant $c > 0$ and $x_0$ such that $$f(x) ≤ c_g(x)$$ for all $x ≥ x_0$
$g$ **grows at least as fast** as $f$ asymptotically

$f(x)$ is $O(g)$ if there exists $c > 0$ and $x_0 > 0$
past the value of $x_0$, $g(x)$ must always represent a larger or equal growth-value than $f$
growth rate of $f$ is **upper bounded** by $g$

$f = O(g)$
$f$ = all functions for $O(g)$

$x^2=O(x^c)$

for $f(x)=2x$ and $g(x) = x$

it is not given, that $f \leq g$ for large values of $x$

But $f(x) \leq cg(x)$
Functions grows at the same rate, but $g$ is less than $f$ for sufficiently large values of $x$

$O(x) = O(2x)$
You can add the constant $c$ to the growth rate: $O(x) = cx$

### Little O
$f(x)$ is $o(g(x))$ if for any constant $c > 0$ we can find $x_0$ such that 
$$
f(x) < cg(x)
$$
for all $x ≥ x_{0}$

$g$ grows (strictly) faster than $f$ asymptotically
$f(x) < cg(x)$, $f$ is strictly less than $O(g)$ for all $x \geq x_0$

## Omega

$\Omega$
*Reverse big-O*

$g$ **grows no faster** than $f$ asymptotically

$g = O(f)$

$f$ grows *at least* as fast as $g$, informally $g \leq f$
Omega can be thought of as a [[Serier og sæt#Sets|set]] 

$g$ is upper bounded for all functions in $O(g)$
Used for proving there is no better algorithm than this one.

## Collection of rules

Theorem 5. Let $f, g, h, p : R^+ → R$ be [[#Asymptotically positive functions|asymptotically positive functions]]
Informally, we can summarize rules R4–R6 from below as 
	Constants < Logarithms < Polynomials < Exponentials
### R1
Overall constant factors can be ignored
	If $c > 0$ is a constant then $cf(x)$ is $Θ(f(x))$.
### R2
For polynomials only the highest-order term matters
	$If p(x)$ is a polynomial of degree $d$, then $p(x)$ is $Θ(x^d)$
### R3
The fastest growing term determines the growth rate
	If $f(x)$ is $o(g(x))$ then $c_{1}g(x) + c_{2}f(x)$ is $Θ(g(x))$, where $c1 > 0$ and $c2 ∈ \Bbb{R}$ are constants
### R4
Logarithms grow faster than constants
	If $c > 0$ is a constant then $c$ is $o(log_{a} (x))$ for all $a > 1$
### R5
Powers (and polynomials) grow faster than logarithms
	$log_a (x)$ is $o(x^b)$ for all $a > 1$ and $b > 0$
### R6
Exponentials grow faster than powers (and polynomials)
	$x^a$ is $o(b^x)$ for all $a$ and all $b > 1$.
### R7
Larger powers grow faster
	$x^a$ is $o(x^b)$ if $a < b$
### R8
Exponentials with a bigger base grow faster
	$a^x$ is $o(b^x)$ if $0 < a < b$
### R9
[[Transitivity]]
	If $f(x)$ is $O(g(x))$ and $g(x)$ is $O(h(x))$ then $f(x)$ is $O(h(x))$ 
	If $f(x)$ is $o(g(x))$ and $g(x)$ is $o(h(x))$ then $f(x)$ is $o(h(x))$
	If $f(x)$ is $Θ(g(x))$ and $g(x)$ is $Θ(h(x))$ then $f(x)$ is $Θ(h(x))$
### R10
Chaining
	If $f(x)$ is $O(g(x))$ and $g(x)$ is $Θ(h(x))$ then $f(x)$ is $O(h(x))$
	If $f(x)$ is $Θ(g(x))$ and $g(x)$ is $O(h(x))$ then $f(x)$ is $O(h(x))$
	If $f(x)$ is $o(g(x))$ and $g(x)$ is $O(h(x))$ then $f(x)$ is $o(h(x))$
	If $f(x)$ is $O(g(x))$ and $g(x)$ is $o(h(x))$ then $f(x)$ is $o(h(x))$
	If $f(x)$ is $o(g(x))$ and $g(x)$ is $Θ(h(x))$ then $f(x)$ is $o(h(x))$ 
	If $f(x)$ is $Θ(g(x))$ and $g(x)$ is $o(h(x))$ then $f(x)$ is $o(h(x))$
### R11
Multiplication
	If $f(x)$ is $O(g(x))$, then $h(x)f(x)$ is $O(h(x)g(x))$
	If $f(x)$ is $Ω(g(x))$, then $h(x)f(x)$ is $Ω(h(x)g(x))$
	If $f(x)$ is $o(g(x))$, then $h(x)f(x)$ is $o(h(x)g(x))$
	If $f(x)$ is $Θ(g(x))$, then $h(x)f(x)$ is $Θ(h(x)g(x))$

The rule **R11** is useful when we want to compare the asymptotic growth of, 
for example, $n\cdot  log(n)$ and $n^2$
From rule ([[#R5]]) we know that $log(n)$ is $o(n)$
Applying **R11** with $h(n) = n$, we can conclude that $n\cdot log(n)$ is $o(n^2)$
This, for example, tells us that [[Sortering og binære søgetræer#Merge-sort|Merge sort]] is a better sorting algorithm than [[Sortering og binære søgetræer#Insertion sort|Insertion sort]] when it comes to asymptotic worst-case complexity.
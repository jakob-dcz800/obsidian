[[Køretidsanalyse]]
## Running time

We talk about running times of [[Algorithms|algorithms]]
Function T(n) of input length
$$
T(n)=\text{max}\set{T(x):|x|\leq n}
$$
T(n) er et "tal" ikke en funktion.
>[!IMPORTANT]
>Aldrig skriv $T(1) \leq O(1)$
## Examples

Here, using [[Asymptotic notation]]
$n + 10 ≤ O(n)$
$n^2 + n ≤ O(n^2)$ 
$2 \cdot sin(n) ≤ O(1)$

$n + 10 \not ≤ O( \sqrt{n})$ 
$n^2 + n  \not ≤ O(n log_2 (n))$ 
$log_2 (n) \not ≤ O(log_2 (1 + log_3 (n)))$

## Proof

> To prove an asymptotic claim, just find literal values
> asymptotic claims cannot be proven by induction
> i.e. a simple proof:
> $T(n)\leq 100C \space lg_{2}(n)$

Claim: $n! \geq \Omega \left( \frac{n^n}{4^n} \right)$
Cannot be proven, since it is a claim

$n! \geq \frac{n^n}{4^n}$
Can be proven, since it is a relation

base
$1 \geq \frac{1}{4}$

step
$(n+1)! \geq \frac{(n+1)^{n+1}}{4^{n+1}}$

$(n+1)! = (n+1)n!$

Aka.
$n! \geq (n+1) \frac{(n)^{n}}{4^{n}}$

>[!IMPORTANT]
>$n!= \Theta(\sqrt{ n}(n / e)^n)$
>Måde at udregne $n!$ på

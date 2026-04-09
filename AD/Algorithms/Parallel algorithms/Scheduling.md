# Opgaveplanlægning

"Scheduling"
De enkelte knuder i et parallelforløb skal udføres af fysiske kerner/processorer 
Opgaverne koordineres af en opgaveplanlægger (“scheduler”)

## Grådig opgaveplanlægning
Når en knude (“strand”) er klar til at blive udført bliver den stillet i en kø 
Når en processor er færdig med en knude går den i gang med næste knude fra køen

>[!TIP] Antagelse
>Tiden brugt på opgaveplanlægning er negligibel i forhold til tiden for beregninger

### Theorem 26.1

>Brent’s theorem

På en ideel parallelcomputer med processorer $P$ giver grådig opgaveplanlægning af en beregning med arbejde $T_{1}$ og spand $T_{\infty}$ en algoritme der tager tid $T_P ≤ T_1/P + T_∞$

Med processorer $P$ til rådighed kan vi ikke udføre beregningen i mindre end $T_{1}/P$ parallelle skridt
Uanset hvor mange processorer der er til rådighed kan vi ikke udføre beregningen i færre end $T_∞$ parallelle skridt

### Eksempler

#### Sekventiel sum
$T_1(n) = T_1(SUM(A, n)) = Θ(n)$ 
$T_∞(n) = T_∞(SUM(A, n)) = Θ(n)$

Theorem 26.1 giver:
$T_P(n) ≤ Θ(n)/P + Θ(n) = Θ(n)$
Flere end $P=1$ processorer hjælper ikke
#### Parallel sum
$T_1(n) = T_1(\text{P-SUM}(A, n)) = Θ(n)$ 
$T_∞(n) = T_∞(\text{P-SUM}(A, n)) = Θ(\lg n)$

Theorem 26.1 giver:
$T_P(n) ≤ Θ(n)/P + Θ(\lg n) = \Theta(\lg n + n/P)$
Med $P=\frac{n}{\lg n}$ processorer er tiden $T_{P}(n)=O(\lg n)$
flere processorer hjælper ikke:
$$
\begin{align}
\Theta(\lg n + n/P) & = 
\Theta\left( \lg n + n/\frac{n}{\lg n} \right)
\end{align}
$$

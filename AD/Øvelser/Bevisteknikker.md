# 4

$$
S(n) = \sum ^{n}_{i=1}
(2i-1)
$$
Giv en formel for summen af de først $n$ ulige tal
Vi beviser ved [[Induction|induktion]] og kan evt. bruge:
$$
\sum ^{n}_{i=1}i=
\frac{n(n+1)}{2}
$$
Eller... vi har $(2i-1)+(2i-1)+\dots+(2i-1)=2\left( \sum^n_{i=1} i \right)-n$
$$
\begin{align}
2\left( \frac{n(n+1)}{2} \right)-n & =n(n+1)-n \\
 & =n^2
\end{align}
$$

# 5

Vis at $n! ≥ 2^{n}$ n for $n ≥ 4$

$2^{n}$ bliver dobbelt størrelse $n$ gange.
$n!$ for hver forøgelse af $n$, bliver $n$ mere end dobbelt så stor.
---

Alternativ løsning vha. induktion
Base step (n = 4)
$$
\begin{align}
4! & = 24 \\
2^4 & =16
\end{align}
$$
Induktionsskridtet.
$$
\begin{align}
(n+1)! & \geq 2^{n+1} \\
(n+1)(n!) & \geq 2(2^n)
\end{align}
$$
Begge led til venstre er større end tilsvarende led til højre.
# 6


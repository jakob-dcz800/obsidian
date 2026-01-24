---
tags:
  - Assignment
---
[[MASD2025_Assignment_1.pdf]]

## 2

### Vi viser diskontinuitet i -2

Vi undersøger grænsen $-2$.
Først ser vi på funktionen $e^{4x-8}$ når $x\to(-2)$
Når funktionen nærmer sig fra venstre:
$$
\lim_{ x \to (-2)^- } e^{4x-8}=e^{-16}
$$
Når [[Epsilon-delta teknikken|funktionen så nærmer sig]] $-2$ fra højre:
$$
\begin{align}
\lim_{ x \to (-2)^+ }-\frac{7}{8}x^{2}+\frac{1}{4}x+4  & = -\frac{7}{8}(4)-\frac{2}{4}+4 \\
 & = \frac{14}{4}-\frac{28}{8} \\
 & =0
\end{align}
$$
Det er tydeligt, at $e^{-16} \not= 1$. Derfor mødes de to funktioner aldrig i $-2$, og funktionen $f$ er ikke kontinuerlig i punktet $(-2, f(-2))$.

### Vi viser diskontinuitet i 2

Vi undersøger [[Grænseværdier|grænsen]] $x=2$.
Først ser vi på funktionen $-\frac{7}{8}x^{2}+\frac{1}{4}x+4$ når $x\to 2$
$$
\begin{align}
\lim_{ x \to 2^- }-\frac{7}{8}x^{2}+\frac{1}{4}x+4  & = -\frac{7}{8}(4)+\frac{2}{4}+4 \\
 & =\frac{36}{8} -\frac{28}{8} \\
 & =1
\end{align}
$$
Når $f$ så nærmer sig $2$ fra højre:
$$
\lim_{ x \to 2^+ }  2x-2 = 2
$$
Det er tydeligt, at $2 \not= 1$. Derfor mødes de to funktioner aldrig i $2$, og funktionen $f$ er ikke [[Kontinuerte funktioner|kontinuerlig]] i punktet $(2, f(2))$.

### Vi viser kontinuitet i x /= 2, -2
I [[Intervaller|intervallet]] $[-5, -2)$ er funktionen kontinuerlig, da den består af den kontinuerlige (og differentierbare) funktion $e^{4x-8}$.

I $[-2, 2)$ gælder det samme for det differentierbare polynomium $-\frac{7}{8}x^2+\frac{1}{4}+4$.

I $[2, 5]$ gælder det samme for den lineære og [[Differentiabilitet|differentierbare]] funktion $2x-2$.

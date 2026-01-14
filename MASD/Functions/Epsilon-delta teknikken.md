---
tags:
  - Math
  - Calculus
  - Functions
---
Epsilon-delta definitionen er den formelle definition på $\lim$

For all $\epsilon > 0$ there is $\delta > 0$ such that, whenever $0 < |x-x_{0}|<\delta$, then $|f(x)-y_{0}|<\epsilon$. These two statements are equivalent formulations of the definition of the [limit](https://mathworld.wolfram.com/Limit.html)

$\epsilon$ and $\delta$ are very small values.
## Definition

$$
\forall \epsilon > 0 \land x \not = x_{0}:|f(x) -f(x_{0})|< \epsilon 
\implies
\exists \delta > : |x-x_{0}| < 0
$$
For alle $\epsilon$ og $x$ ikke lig $x_0$ hvorom det gælder at den absolute forskel mellem $f$...
**Bemærk** at rækkefølgen er vigtig: Først vælger man ε, derefter beviser man at δ eksisterer

![[epsilon-delta.excalidraw]]

For ethvert epsilon som IKKE er højden af skærings punktet skal der findes et tilsvarende delta som IKKE er nul.
Alle y-værdier mellem to vilkårlige punkter skal være berørt

https://www.youtube.com/watch?v=kfF40MiS7zA&t=569s

For en IKKE-kontinuert funktion kan du ikke finde et tilpas lille epsilon som er inden for rækkevidde af skæringspunkterne

Vær OBS på når grafer har huller. Computere tegner ikke disse pga. sampling.
f.eks. $\frac{0}{0}$

![[Pasted image 20250904113125.png]]
Du kan altså forskyde epsilon funktionen

## Eksempel

Et simpelt eksempel pa udregning af en grænseværdi er følgende:
Betragt polynomiet $f(x) = 3x^2 − 2$, vis at  $$\lim_{ x \to 3 } f(x) = 25$$
$x_{0}$ er altså givet ved $x_{0}=3$
Vi ser at $f(x_{0})=f(3)=25$, men dette er ikke en del af øvelsen - vi skal benytte epsilon-delta teknikken for at vise det samme.

Vi skal altså vælge et vilkårligt $ε > 0$ og vise at der findes et $δ > 0$ således at:
$$
|x-3|<\delta, x \not=3 \implies |f(x)-25|<\epsilon
$$
Vi kan så starte med at omskrive funktionen så at den er lettere at arbejde med:
$$
f(x)-25=3x^2-2=3x^2-27=3(x+3)(x-3)
$$
Hermed kan man indse, at $| f(x) − 25| < ε$ er ensbetydende med :
$$
\begin{align}
|f(x) − 25| = \\
|3(x+3)(x-3)| =  \\
3(x-3)(x+3) < \epsilon
\end{align}
$$
Vi bemærker at $x − 3$ optræder i det udtryk, og at $ε - δ$ teknikkens andet trin er at finde $δ > 0 : |x − 3| < δ$ givet $ε$ og $x_0$
Sa vi vil nu arbejde p å at få isoleret $x − 3$. 
Først indser vi, at da $3 > 0$ og da $|ab| = |a||b|$ kan vi omskrive den ovenstående ulighed som
$$
|x-3||x+3|< \frac{\epsilon}{3}
$$
Lad os nu betragte værdier af $x$ tæt på $x_0 = 3: x ∈ (2, 4)$ ([[Intervaller]])
For det interval, lad os undersøge $|x + 3|$ og $|x − 3|$ enkeltvis.

Ved indsættelse af værdierne $2$ og $4$ finder vi at 
$$
\begin{align}
(2-3) < x − 3 < (4-3)  \\
⇒ |x − 3| < δ_{1} = 1
\end{align}
$$
og at 
$$
\begin{align}
(2+3) < x + 3 < (4+3)  \\
⇒ 5 < |x + 3| < 7
\end{align}
$$
Da $x + 3 > 0$ kan vi omskrive $|x-3||x+3|< \frac{\epsilon}{3}$ til:
$$
|x-3|< \frac{\epsilon}{3(x+3)}
$$
da $5 < x + 3 < 7$ følger at $\frac{\epsilon}{21}< \frac{\epsilon}{3(x+3)} < \frac{\epsilon}{15}$, og dermed kan vi konkludere at:
$$
|x-3|< \frac{\epsilon}{21}
$$
Givet et $ε$ har vi dermed fundet et $δ = \frac{ε}{21}$ således at dette gælder: 
$$
|x-3|<\delta, x \not=3 \implies |f(x)-25|<\epsilon
$$
Da ovenstående gælder både for værdier større og mindre end $3$, betyder det, at grænseværdien er uafhængig af om man gar mod $3$ fra højre eller venstre, og dermed har vi bevist, at $f$ er [[Kontinuerte funktioner|kontinuert]] i nærheden af $x_0 = 3$

Ved gennemgang af ovenstående kan man indse at alle argumenterne gælder for vilkårlig værdi af $x_0 ∈ \mathbb{R}$ og dermed at $f$ kontinuert ved alle værdier $x_0 ∈ \mathbb{R}$.
# Substitution method
>[!INFO] Purpose
>The substitution method is used to find upper- (and lower) bounds on [[recurrences]] using mathematical [[induction]].

Substitutionsmetoden er reelt set [[Induction#Strong induction|stærk induktion]].
Metoden består af følgende skridt:
1. Gæt formen af løsningen (typisk [[Køretidsanalyse#Big-O|O-notation]], eller [[Køretidsanalyse#Omega|omega]])
2. Benyt stærk induktion til at finde de konstanter som skal gælde for at vise at gættet (1.) holder

[[Recursion trees|Rekursionstræ-metoden]] kan bruges til at finde et fornuftigt gæt.
Vi beviser altså at gættet er korrekt. 
## Antagelser

Vi noterer sjældent basistilfældet som i [[Mergesort#Køretid|denne rekursionsligning]]
For værdier af $n=1, 2,\dots,k$ (vælg selv et relativt småt $k$) kan vi antage, at $T(n_{k})= 1$
**Dette gælder kun op indtil konstanten, ikke for alle $k$**

_Man vælger selv k, det skal bare være en fast værdi på forhånd_
## Eksempel
**Preamble**
$$
T(n)=2T(\lfloor n /2 \rfloor )+n, n>1
$$
Vi antager $T(1)=1$
Vi gætter: $T(n)=O(n \lg n)$
Vi skal altså vise, at $T(n)\leq cn \lg n$, for alle $n \geq n_{0}$, for en konstant $c  >0$ og $n_{0}>0$
$$
\exists c, n_{0}>0 \space \forall n\geq n_{0}: T(n)\leq cn \lg n
$$
Uligheden gælder ikke når n = 1: $1 \leq 0$ hvilket er usandt.
Så vi vælger $n_{0}=2$
Vi ser inde i udtrykket $T\left( \left\lfloor  \frac{n}{2}  \right\rfloor \right)$, at hvis $n_{0}=2, 3$ så bliver udtrykket $T(1)$
Vi har lige set, at $T(1)$ ikke kan bruges i vores induktion da uligheden ikke holder.

---
**Base step**
Siden $T(n) = 2T\left( \left\lfloor  \frac{2}{n}  \right\rfloor \right)+n$ for $n>1$, har vi at 
- $T(2)=2(1)+2=4$
- $T(3)=2(1)+3=5$

>[!QUESTION] Hvorfor vælger vi ikke base case $n_0= 3$?
>Problemet opstår når vi skal vise for $n=4$, den afhænger nemlig af $n=2$ som vi så ikke har fået vist

Hvis vi vælger $c\geq 2$, har vi at $T(n)\leq cn \lg n$ for $n=2, 3$
- $T(2)=4\leq c\cdot 2 \lg 2=2c$
- $T(3)=5\leq c\cdot 3 \lg 3\simeq3c$

---
**Induction step**
Vi kan antage, at $n>3$ da vi havde to basistilfælde.
Vi kan også antage (pga. stærk induktion), at $T(m) \leq cm \lg m$ for $m=2,3,\dots, n-1$
_(1 galt jo ikke)_

Så hvis den gælder for $[2;n-1]$, så må den også gælde for $\lfloor n /2 \rfloor$, da det ligger i intervallet.
$$
T(\lfloor n /2 \rfloor )
\leq c \lfloor n /2 \rfloor \lg \lfloor n /2 \rfloor  
$$
Nu kan vi bruge definitionen:
$$
\begin{align}
T(n) & =2T(\lfloor n /2 \rfloor )+n \\
 & \leq 2c \lfloor n /2 \rfloor \lg \lfloor n /2 \rfloor +n \\
 & \leq c n \lg (n/2) +n \\
 & = cn \lg n - cn \lg 2 + n \\
 & = cn \lg n - cn + n
\end{align}
$$
Det vi skulle vise var $T(n)\leq cn \lg n$
Vi satte $c\geq2$ (i.e. lig med $2$), så der står reelt:
$$
\begin{align}
T(n) & \leq cn \lg n -2n+n \\
 & \leq cn \lg n-n \\
 & < cn \lg n 
\end{align}
$$


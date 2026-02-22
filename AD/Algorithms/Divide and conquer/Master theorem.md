# Master metoden

>[!TIP]
Master metoden er et formelt argument for køretiden - ikke et gæt

>[!INFO] Forudsætninger
>Hvis en rekursionsligning er på denne formel
$$ T(n)=aT(nb)+f(n)$$
>hvor $a\geq 1$ og $b > 1$ er konstanter. Så kan man bruge master metoden

>[!NOTE] Definition
>Master metoden giver med det samme $\Theta$ hvis man kan finde $a, b, f$
>1. Hvis $f(n)= O(n^{\log_{b}a-\epsilon})$ for konstanten $\epsilon>0$, så gælder det:
>$$T(n)=\Theta(n^{\log_{b}(a)})$$
>_Hvis $f(n)$ i en hvis forstand er "lille" ift. funktionen T_
> ---
>2. Hvis $f(n)= \Theta(n^{\log_{b}a})$, så gælder det:
>$$T(n)=\Theta(n^{\log_{b}a})\lg n$$
>_$f(n)$ har "samme" vækstrate som T_
>---
>3. Hvis $f(n)= \Omega(n^{\log_{b}a+\epsilon})$ for konstanten $\epsilon>0$ og $af(n /b)\leq cf(n)$ for $c<1$ og nødvendigt stort $n$, så gælder det:
>$$T(n)=\Theta(f(n))$$
>_$f(n)$ vokser hurtigt ift. funktionen T_

>[!QUESTION] Hvad med floor / ceiling?
>Man ignorerer bare floor og ceiling. 
## Eksempel 1

Vi bruger [[mergesort|merge-sort]] som eksempel.
$$
T(n)=2T(n /2)+\Theta(n)
$$
✅Den er på den rigtige form.
- $a=2$
- $b=2$
- $f(n)=\Theta(n)$
 
>[!QUESTION]
>Skal $f(n)$ være en [[Asymptotic notation|asymptotisk]] funktion?
>**nej**, se [[#eksempel 2]]

Eftersom $\log_{2}2=1$, kan vi se at 2. holder:
$$
f(n)=\Theta(n^{\log_{2} 2})=\Theta(n)
$$
Af dette kan vi se, at:
$$
T(n)=\Theta(n) \log n= \Theta(n \log n)
$$
## Eksempel 2
$$
T(n)=T(\lfloor n /2 \rfloor )+T(\lfloor n /2 \rfloor )+3
$$
- $a=2$
- $b=2$
- $f(n)=3$
Eftersom at $\log_{2}2=1$, har vi at $n^{\log_{b} a}=n$
$f(n)$ skal være polynomielt mindre en $n^{\log_{b}a}$, siden at $\epsilon$ trækkes fra.
Da $f(n)$ er en konstant, er den i alle fald polynomielt mindre.
Vi har altså at 1. holder, og derfor:
$$
T(n)=\Theta(n^{\log_{b}a})=\Theta(n)
$$
## Eksempel 3
![[Pasted image 20260209174910.png]]

- $a=4$
- $b=2$
- $f(n)=n^{2}$
Vi har altså at $n^{\log_{b}a}=n^{2}$, og derfor:
$$
T(n)=\Theta(n^2\cdot \lg n)
$$
## Eksempel 4
![[Pasted image 20260209175018.png]]
# Undtagelser

>[!QUESTION] Hvornår kan man **ikke** bruge master metoden?
Her kan man ikke:
>$$T(n)=4T(n/2 +2)+n$$
>da den ikke følger formen


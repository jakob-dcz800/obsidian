# Rekursionsligninger

>[!TIP]
>Målet med at løse en rekursionsligning er 

Kan løses vha. 
- [[Recursion trees]]
- [[Master theorem]]
- [[Substitution method]]
## Eksempel

Hvordan løser man en rekursionsligning som denne her?
$$
T(n)=
\begin{cases}
\Theta(1) & \text{if } n=1 \\
T(\lceil n/2 \rceil )+T(\lfloor n/2 \rfloor ) + \Theta(n) & \text{if } n > 1
\end{cases}
$$
_Denne er fra [[Mergesort#Køretid|merge-sort]]_
Vi kan sommetider ignorere loft og gulv sådan at vi kan simplificere:
$$
T(n)=
\begin{cases}
\Theta(1) & \text{if } n=1 \\
2T(n/2) + \Theta(n) & \text{if } n > 1
\end{cases}
$$
Vi må gerne ignorere floor og ceil når vi skal bruger [[Master theorem|master theorem]] eftersom at den giver os et gæt på køretiden.
Når vi bruger [[Substitution method|substitutionsmetoden]] skal vi huske floor og ceiling.
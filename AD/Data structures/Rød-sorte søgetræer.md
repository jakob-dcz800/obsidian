
# Rød-sorte søgetræer

>Standard [[Binære søgetræer|binært søgetræ]]
## Egenskaber

1. En knude er enten sort eller rød
2. Rodknuden er sort
3. Alle blade er `NIL` og er sorte
4. Hvis en knude er rød, er dens børn sorte
5. For enhver knude, indeholder alle stier til knudens blade det samme antal sorte knuder.

>[!TIP] Højde
> Et rød-sort træ med $n$ indre knuder, har maksimalt højden $2 \lg (n+1)$

>[!INFO] Sort højde
> Sort-højden er antal sorte knuder fra en knude, og ned til bladene
> Rodens sort-højden er altid mindst $h/2$
> Derfor gælder det, at 
$$ n \geq 2^{h/2}-1$$
## Køretider

`RB-Insert` tager $O(\lg n)$ tid
Søgning er $O(\lg n)$

`RB-Delete` tager også $O(\lg n)$ tid
`RB-Fixup` er del af `RB-Delete` og tager også $O(\lg n)$ tid

## Rotation
>Se 337 CLRS for eksempel

![[Pasted image 20260406202939.png]]

## Successor

En successor for $x$, er den mindste i mængden af tal, som er større end $x$.
I et træ er en successor dét tal, som besøges efter $x$ i en **in-order tree walk**
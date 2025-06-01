---
tags:
  - Math
  - DMA
---

# Funktioner og størrelsesordener
## Tidskompleksitet

Tidskompleksitet fortæller noget om, hvor hurtig kører en algoritme på en computer.
Køretiden afhænger af størrelsen af inputtet og ikke selve algoritmen som har en konstant køretid.

#RAM = random acces machine
Meget simpel model af computere, men alligevel realistisk

I en køretidsanalyse tæller vi hvor mange skridt algoritmen foretager for hver linje.
Vi tæller også hvor mange gange hver linje kan køres.
$\theta(n)$ = køretidsanalyse (theta)
Køretiden er proportional med $n$

**Asymptotisk notation**, her fjerner konstanter og efterlader det hurtigst voksende led
En løkke i en løkke som begge kører $n$ gange, resulterer i køretiden ⇒ $\theta(n^2)$

## Køretid og rekursive funktioner

**`⌊x⌋ = Math.floor(x)`**

Når en rekursiv algoritme kalder sig selv, opstår en “kopi” af algoritmen
Den originale algoritme som kalder sig selv afventer fortsat et `return` 

Variablene i de forskellige algoritmer gemmes in memory for hver enkelt funktion der kaldes

Hver gang algoritmen kaldes halveres array

$\log_2{n}$

Antallet af kald er højst $log_2 n$

I datalogi er $log_{10}$ ikke særligt interessant

hvis man skriver log i theta betyder det ikke noget hvilken log det er, da logaritmers base vokser konstant

Rekursive funktioner bruger langt mere plads da computeren skal huske noget for hvert kald - dette gøres $log (n)$ gange

### Toppunkter

_Eksempel på algoritme vist i lektionen_

Om et tal er et toppunkt defineres ud fra naboerne. Et tal er et toppunkt hvis naboerne er mindre eller lig med tallet

Rækkefølgen i et if (or statement) betyder noget. Tjek om man kan indeksere et tal før det benyttes i et sådant statement.

`if (i == 0 or A[i] >= A[i - 1]) and (i == n - 1 or A[i] >= A[i + 1])`

_Vi skal i opgaver og lektioner ikke blive ved med at udregne køretid ved at fjerne konstanter osv_
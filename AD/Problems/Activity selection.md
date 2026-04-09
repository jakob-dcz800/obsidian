# Activity selection
Here, we use [[Greedy algorithms]]

![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=8&rect=40,160,383,762|Slides_Greedy_uden_indlagte_pauser-1, p.8]]

Vigtigt at: $s_i \not=f_{i}$
$[s_{i},f_{i})$: starter på $s_{i}$ og slutter lige inden $f_{i}$ se [[Intervaller]]
To aktiviteter er kompatible hvis deres tidsintervaller er [[Datastrukturer for disjunkte mængder|disjunkte]]
	Det betyder at der ikke er noget overlap.

## Eksempel

Her er en optimal løsning:
![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=10&rect=171,161,437,763|Slides_Greedy_uden_indlagte_pauser-1, p.10]]

Denne er optimal, da man ikke kan finde 5 tider som parvist er kompatible.
4 er det største antal.
Målet er at maksimere antallet er planlagte resurser.

## Løsning / algoritme

### Dynamisk programmering
[[Dynamisk programmering]]

![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=11&rect=263,169,531,755|Slides_Greedy_uden_indlagte_pauser-1, p.11]]
![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=12&rect=269,162,530,756|Slides_Greedy_uden_indlagte_pauser-1, p.12]]
![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=13&rect=267,163,529,757|Slides_Greedy_uden_indlagte_pauser-1, p.13]]
### Grådig algoritme
[[Greedy algorithms]]

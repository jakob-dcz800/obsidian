- [ ] # Grådige algoritmer

>[!DEFINITION] Hvad er en grådig algoritme?
>En grådig algoritme løser et problem, ved gentagne gange at vælge den mulighed som er bedst på det *nuværende* tidspunkt
>Den laver altså et grådigt valg hele tiden.

## Forskel fra dynamisk programmering

- [[Dynamisk programmering]] udregner først og foretager valget bagefter
- Grådige algoritmer vælger først og udregner efter

Grådige algoritmer er som regel hurtigere end dynamisk programmering.
Ikke alle problemer kan løses med grådige algoritmer og kræver derimod dynamisk programmering. (f.eks. 0/1 knapsack problem, fractal knapsack kan godt løses)

# Greedy choice property

> Paradigme/skabelon for problemløsning

- Når først et valg er taget, kan det ikke ændres
- Vi skal altså sikre os, at efter et valg kan vi fortsat finde en optimal løsning for problem $P$

> [!DEFINITION]
> Vi har "greedy choice property" hvis der findes en optimal løsning for problem $P$ som indeholder grådige valg.
> Uden denne property kan det ske, at et grådigt valg tages som udelukker alle optimale løsninger.

## Optimal delstruktur

![[Slides_Greedy_uden_indlagte_pauser-1.pdf#page=6&rect=34,153,548,760|Slides_Greedy_uden_indlagte_pauser-1, p.6]]
> Ovenstående er uformelt
> Hvis vi kan påvise greedy choice property, så er ovenstående altid gældende.


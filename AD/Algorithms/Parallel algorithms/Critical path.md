# Parallelle algoritmer
## Critical path
**Kritisk sti**: "critical path" Længste sti i parallelforløbet
**Spand**: "span" Antal knuder på den kritiske sti, betegnes med $T_∞$
>[!TIP]
>Uanset hvor mange processorer der er til rådighed kan vi ikke udføre beregningen i færre end $T_∞$ parallelle skridt

![[Pasted image 20260318140232.png]]

Hver kasse er et kald til algoritmen
Hver bold er en udregning af $x$, $y$, eller $x+y$
Pilene viser hvilke afhængigheder der er.

**Arbejde** (“work”): Antal knuder i [[Grafmodel for parallelforløb|parallelforløbet]], betegnes med $T_1$
## Arbejde og spand

Work
Span

![[Pasted image 20260318141613.png]]

For parallelle processer er span udregnet til at være den process som tager længst tid
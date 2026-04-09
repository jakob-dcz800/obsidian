# Dijkstra's algoritme
>[!DEFINITION]
>Algoritmen finder korteste vej til fra ét til alle punkter i en **vægtet og orienteret graf**
>Returnerer listen af distancer
>Dijkstra’s algoritme er kun garanteret korrekt når der **ikke er negative vægte**

Denne resulterer ikke i et [[Minimum spanning tree]], som Kruskal og Prims algoritme gør.

## Metode

- Vælg startknude
- Hav en liste af ubesøgte knuder
- Hav liste af distancer for alle knuder (opdateres løbende)

![[Pasted image 20260406134202.png|235]]
> Så vælger vi {c, b} da denne er mindste vægt
![[Pasted image 20260406134427.png|235]]
> Nu vælges d
![[Pasted image 20260406134539.png|235]]
![[Pasted image 20260406134607.png|235]]

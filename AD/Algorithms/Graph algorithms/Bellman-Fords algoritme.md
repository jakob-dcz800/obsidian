# Bellman-Fords algoritme

Udregner distancer med udgangspunkt i en knude
Returnerer en liste af korteste veje (samme som [[Dijkstras algoritme]])


## Egenskaber
- Fungerer godt med **negative vægte**
- Benytter en vægtet, orienteret graf
- Kører max b-1 iterationer
- Tidskompleksiteten er $O(|V|\cdot|E|)$
	- For hver iteration gennemgås all knuder og deres kanter
	- Dette kan ske samtlige gange, men O simplificerer

## Metode
- Går gennem alle kanter for hver iteration
	- Tip: kig på alle knuder og deres udadgående kanter
- Vedligehold en liste af distancer for alle knuder

## Pseudokode

![[Pasted image 20260407131610.png]]

## Forskel fra Dijkstra's algoritme

Kører på grafer med negative vægte
Begge fejler ved **negative cyklusser**

Dijkstra er en [[Greedy algorithms|grådig algoritme]]
	Dijkstra vælger først og efterberegner ikke
Bellman ford er ikke grådig
	Bellman ford kører over samtlige iterationer og kan opdatere valg
![[Pasted image 20260407132149.png|333]]

> Her vil Dijkstra først vælge s,a:3 og ikke opdatere valget
> Bellman ford vil også først vælge s, a,  men efterfølgende opdatere den korteste vej fra s til a som at være s -> b -> a: 2
### Negativ cyklus
En negativ cyklus bliver mindre og mindre for hver iteration
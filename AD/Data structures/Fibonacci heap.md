# Operationer

| Operation      | Running time |
| -------------- | ------------ |
| `Make-heap`    | $O(1)$       |
| `Insert`       | $O(1)$       |
| `Minimum`      | $O(1)$       |
| `Extract-min`  | $O(\lg n)$   |
| `Union`        | $O(1)$       |
| `Decrease-key` | $O(1)$       |
| `Delete`       | $O(\lg n)$   |
[[Amortized analysis|Amortiserede]] køretider, ikke worst-case ligesom [[binary heap]]. Dvs. omtrent gennemsnitlige køretider 
## Heap-Insert
![[Pasted image 20260216161513.png]]

## Extract-Min
![[Pasted image 20260216161540.png]]

Sidste skridt i `Extract-Min`, der leder til bedre amortiseret kompleksitet: 
	`Consolidate` sørger for at der ikke findes to rodknuder med lige mange børn

## Consolidate

![[Pasted image 20260216162218.png]]

# Definition

Fibonacci [[Stakke, køer, lister, hobe#Hobe|hoben]] er et samling af rodfæstede træer.
Hver knude `x` har nøgle `key(x)`$\in \mathbb{R}$. Nøglen svarer til den indsatte reelle værdi.

### Attributter

| Attribut  | Betydning                           |
| --------- | ----------------------------------- |
| `x.deg`   | Antallet børn som er koblet til `x` |
| `x.mark`  | `bool` om `x` er markeret           |
| `x.p`     | parent                              |
| `x.child` |                                     |

### Egenskaber
Alle træer har [[Min heap|min-heap]] egenskaben, altså at:
> [!INFO]
> Enhver knude `x`, som har en forældre `p`, skal have en værdi `key(x) <= key(p)`
> Altså, et barns værdi skal være mindre eller lig med forælderens værdi
> 
> Roden er altså af lokal minimal værdi 

- Alle knuder er forbundne via. en [[Stakke, køer, lister, hobe#Hægtede lister|dobbelt-hægtet liste]]
- Alle knuder har pointer til forældre (hvis en sådan findes).
- Alle knuder har pointer **et enkelt barn** (hvis en sådan findes).
	- Se på eksempel herunder (4 til 7 og 5 til 7)
	- *Usikker: Der er ingen regler om hvilket barn som vælges?*
- Søskende er forbundne i en cirkulær [[Stakke, køer, lister, hobe#Hægtede lister|dobbelt-hægtet liste]]
	- Hvis en knude er enebarn, peger den på sig selv.
- Der findes en pointer til den mindste værdi i skoven som er roden af et træ.
- Rødderne er hægtet sammen i en cirkulær [[Stakke, køer, lister, hobe#Hægtede lister|dobbelt-hægtet liste]]

En knude kan have et ubegrænset antal børn
#### Eksempel
Her vises fire træer i en heap
Bemærk at H, kan referere til en samling a heaps.
En heap kan have op til flere træer.

![[Slides_Fibonacci_uden_indlagte_pauser-1.pdf#page=6&rect=273,154,560,767|Slides_Fibonacci_uden_indlagte_pauser-1, p.6]]

![[Pasted image 20260216160641.png]]
## Fordele

Det, at `Decrease-key` kører i tid $O(1)$ er en fordel når det kommer til 
[[Dijkstras algoritme|Dijkstra]]'s- og [[Prims algoritme]]
## Ulemper

Fibonacci heaps er i praksis ret langsomme, men giver gode teoretiske begrænsninger for køretid.
Man skal op på meget store problemstørrelser før at fibonacci heaps slår [[binary heap|binary heaps]]

# Amortiseret omkostning

Se [[potentialmetoden]]

![[Slides_Fibonacci_uden_indlagte_pauser-1.pdf#page=9|Slides_Fibonacci_uden_indlagte_pauser-1, p.9]]

Hvis vi kan finde en øvre grænse for den amortiserede omkostning, så finder vi den også for den faktiske omkostning.

## Diverse

>[!QUESTION] Hvordan tegner jeg et fibonacci træ?

![[Pasted image 20260216160938.png]]
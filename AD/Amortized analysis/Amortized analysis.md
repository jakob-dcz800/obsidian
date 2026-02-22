# Amortisering

> [!TIP] Dele en omkostning jævnt ud over tid
>- Amortiseret analyse kan give mere præcise grænser for samlet (worst case) [[Time complexity|tidsforbrug]] når visse operationer tager mere tid end andre
>- Summen af amortiserede tider er en øvre grænse for den samlede tid
>- [[Potentialmetoden|Potentialfunktioner]] kan bruges til at lave præcise argumenter for amortiseret tid

## Eksempel 

- Amortiseringslån i banken (fast rente): 
	- Betal samme beløb hver måned 
	- I starten er en større del **renter**, senere er det meste $\text{afbetaling}$

![[Pasted image 20260211160728.png]]

## Amortisering i datastrukturer

> Læg løbende “penge” til siden for at betale for fremtidige dyre operationer

[[Regnskabsmetoden]]

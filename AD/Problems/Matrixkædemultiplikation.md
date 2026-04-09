# Matrixkædemultiplikation

Optimer antallet af udregninger ved at sætte parenteser de rigtige steder.
## Metode for læsning

![[Pasted image 20260407135900.png]]
## Pseudokode

![[Pasted image 20260404145126.png]]

## Eksempel

![[Pasted image 20260405142919.png]]

nej: 3, 4, 1, 5
✅ **ja: 2**
Process: 
- Kig på højre hjørne $p[1, 6]$, split hér
- Gå så ned ad stien $p[1, j]$ og split når tallet ændres.
- Hver gang værdien i $p[i, j]$ skifter, så split og gå rekursivt ned af træet
- Udeluk muligheder en efter en.
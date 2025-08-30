# Gram-Schmidt processen

Lad $\mathcal{U}$ være et underrum af $\mathbb{R}^n$ . 
Hvis $\mathcal{U}$ er af en bestemt type, fx $\text{row A},\text{ col A eller null A}$, så har vi lært af bestemme en basis for $\mathcal{U}$.

For at beregne [[Ortogonal projektion|ortogonale projektioner]] på $\mathcal{U}$ skal man bruge en [[Ortonormale baser|ortonormal basis]] (eller en ortogonal basis) for $\mathcal{U}$. 

Spørgsmål. 
Givet en (almindelig) [[Baser|basis]] for $\mathcal{U}$, er der så en metode til at konstruere en ortonormal basis for $\mathcal{U}$ ? 

Svar. 
Ja! Brug **Gram–Schmidt processen**.

## Algoritme 4.52: Gram–Schmidt processen

![[Pasted image 20250513222137.png]]

u1 ... un er en (grim) basis.
Vi vil gerne lave det om til en køn normeret basis.
Nævneren er bare længde, så vektoren normeres

[[Lineær uafhængighed]]
[[Underrum]]

### Illustration
![[Pasted image 20250513222304.png]]

tre vektorer u1..3
q1 = normeret u1
## QR-faktorisering

Ved at holde lidt nøjere regnskab med hvad der foregår i [[#Gram-Schmidt processen]] kan man opnå følgende:

![[Pasted image 20250513222556.png]]
![[Pasted image 20250513222650.png]]

Ved løsning af problemer som kræver lineær algebra kan det, i datalogiske sammenhænge, være ganske tidsbesparende at lave QR-faktoriseringer af de involverede matricer
## Eksempel

### 1 Gram–Schmidt processen

![[Pasted image 20250513222333.png]]
![[Pasted image 20250513222345.png]]
![[Pasted image 20250513222355.png]]
![[Pasted image 20250513222426.png]]

### 2 Øvelse

![[Pasted image 20250513222504.png]]

### QR-faktorisering
![[Pasted image 20250513222752.png]]
![[Pasted image 20250513222807.png]]

#### 2

![[Pasted image 20250615143213.png]]
![[Pasted image 20250616114332.png]]
![[Pasted image 20250616114320.png]]
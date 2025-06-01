# Rækkerum

## Definition

En $m \times n$ matrice har $m$ rækker
$_{1}A$ er første række og $_{n}A$ er n'te række.
Vi opskriver typisk rækker som søjler.

![[Pasted image 20250506213602.png]]

Rækkerummet er endnu et underrum af $\mathbb{R}^n$.
Vi vil selvfølgelig altid finde basen for underrum.
Udtyndingsalgoritmen fortæller os, at vi kan gå igennem alle rækker og smide de ud, som er unødvendige for en udspænding af underrummet. Her bruger vi dog en bedre metode [[#1|her]]
## Theorem

### 3.14
![[Pasted image 20250506214236.png]]

"$\mathbf{B}$ har $r$ rækker som ikke er nul"
"$r = \text{rank }\mathbf{A}$"
## Eksempel

### 1
Metode som er **bedre** end udtyndingsalgoritmen.
Vi vil gerne finde basen for rækkerummet i dette eksempel.
![[Pasted image 20250506213636.png]]

Vi ved, at den første række i $\mathbf{B}$ er en linearkombination af de originale rækker. [[Rækkeoperationer#Betydning af rækkeoperationer|læs her]]
Vi kan altså udtrykke rækker i $\mathbf{B}$ som i følgende eksempel:
Når vi er kommet frem til rækkerne i $\mathbf{B}$, kan vi selvfølgelig omvende operationerne for at komme frem til rækkerne i $\mathbf{A}$

![[Pasted image 20250506213651.png]]

Dvs. hvis vi har en linearkombination af rækkerne i A, er det også en kombination af rækkerne i B
Det samme gælder omvendt.

**Alle ikke-nulrækker udspænder rækkerummet.**
Det er altså ikke-nulrækkernes numre (i den reducerede form) som vi benytter i A, til at bestemme hvilke rækker som udspænder rækkerummet. 

![[Pasted image 20250506213702.png]]
Når vi har nullerne placeret på denne måde, har vi et lineært uafhængigt sæt af vektorer.
De er altså basis for rækkerummet.
### 2
![[Pasted image 20250506214249.png]]

---
tags:
  - Matrices
  - Math
  - LINALG
---
# Rækkeoperationer

## Elementære rækkeoperationer 

• Lægge et multiplum af en række til en anden række (rækkeoperation, eng: row replacement ) 
• Bytte om på to af rækkerne (rækkeombytning, eng: row interchange) 
• Gange en række igennem med et tal (tal gange række, eng: row scaling) 

### Rækkeombytning

• At lave en rækkeombytning i totalmatricen for et ligningssystem svarer blot til at skrive ligningerne i systemet i en anden rækkefølge 
• En rækkeombytning ændrer derfor ikke løsningsmængden til ligningssystemet

### Multiplikation af en række
Multiplikation af en række med et tal ̸= 0

• At multiplicere en række i totalmatricen for et ligningssystem med et $tal \not= 0$ svarer til at gange en af ligningerne i systemet igennem med et $tal \not= 0$
• Multiplikation af en række med et $tal \not= 0$ ændrer derfor ikke løsningsmængden til ligningssystemet
## Definition 
• At udføre en rækkeoperation på totalmatricen for et ligningssystem svarer til at lægge et multiplum af en ligningerne til en af de andre ligninger 
• En rækkeoperation ændrer derfor ikke løsningsmængden til ligningssystemet

## Theorem

### 2.7 morale
At lave en rækkeoperation på en matrix er det samme som at gange den tilsvarende elementærmatrix på matricen fra venstre


## Betydning af rækkeoperationer

Hvad betyder det at lave en rækkeoperation?
Tag eksempelvis: $r_{2}-2r_{1}\to r_{2}$.
Det betyder, at den nye række er en [[Span#Eksempel på linearkombination|linearkombination]] af den gamle række.
Den er en kombination af den gamle $r_{1}$ og den gamle $r_{2}$.
$$
\text{ny-}r_{2} \in \text{span}\set{\text{gamle-}r_{2}, \text{gamle-}r_{1}}
$$
Vi kan altså nå den nye $r_{2}$ ved en kombination af de gamle $r_{1}, r_{2}$
Når vi altså har den reducerede echelonform, er alle rækkerne et resultat af kombinationer af de originale rækker.

## Eksempel

### 1
![[Pasted image 20250616113856.png]]
![[Pasted image 20250616113827.png]]

### 2
![[Pasted image 20250616113939.png]]
![[Pasted image 20250616113951.png]]

### 3
![[Pasted image 20250616114011.png]]
![[Pasted image 20250616114023.png]]

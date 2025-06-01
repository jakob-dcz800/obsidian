# Mindste kvadraters metode

For $m × n$ matrix $A$ betragter vi et lineært ligningssystem
$$
Ax = b
$$
Hvis ligningssystemet er inkonsistent (dvs. det har ingen løsning), så efterspørger vi i stedet den vektor $\mathbf{x}$ som gør størrelsen
$$
\|\mathbf{b-Ax}\|
$$
mindst mulig. [[Ortogonal projektion#4.13 Projektion som bedste tilnærmelse|4.13]] viser, at vi skal vælge $\mathbf{x-\bar{x}}$ hvor
$$
\mathbf{A\bar{x}}=\text{proj}_{\text{col }\mathbf{A}}(\mathbf{b})
$$
![[Pasted image 20250513223231.png]]

![[Pasted image 20250513223248.png]]

Men kan normalligningerne overhovedet løses?

I det oprindelige inkonsistente ligningsystem 
$$
\mathbf{Ax} = \mathbf{b} 
$$
(hvor $A$ er en $m × n$ matrix) er der typisk flere ligninger end ubekendte ($m > n$) og $\text{rank A} = n$.

## Opsummering

![[Pasted image 20250513223514.png]]
![[Pasted image 20250513223531.png]]
## Theorem

### 4.16 (a) Løsning af normalligningerne
![[Pasted image 20250513223436.png]]

## Eksempel

### 1 Mindste kvadraters metode
![[Pasted image 20250513223722.png]]
![[Pasted image 20250513223734.png]]
![[Pasted image 20250513223822.png]]

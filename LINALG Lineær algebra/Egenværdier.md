# Egenværdier

## Definition

![[Pasted image 20250521132826.png]]

Et tal $\lambda$ er en **egenværdi** for en $n × n$ [[LINALG Lineær algebra/Matricer/Matricer|matrix]] $A$ hvis der findes en vektor $\mathbf{x} \not= 0$ sådan, at $Ax = λx$ 
En sådan vektor $x$ er en **egenvektor** hørende til egenværdien $λ$.

Ligningen $Ax = λx$ udtrykker, at vektorerne $Ax$ og $x$ er proportionale (dvs. peger i samme eller modsat retning).

![[Pasted image 20250521132711.png]]

## Hvordan?

### Det karakteristiske polynomium
![[Pasted image 20250521133553.png]]

Vi får et polynomium in n'te grad

![[Pasted image 20250521133648.png]]
![[Pasted image 20250521133803.png]]

2) Vi skal finde rødderne i det karakteristiske polynomium


## Eksempel

### 1
![[Pasted image 20250521133204.png]]

Billedet af $x_{1}, x_{2}$ ligger i forlængelse af vektorerne
Vi udregner dette:

![[Pasted image 20250521133348.png]]

### 2
![[Pasted image 20250521133912.png]]

### 3
![[Pasted image 20250521133935.png]]

### 4
![[Pasted image 20250521133951.png]]

Årsagen til at vi kan rykke $\lambda+2$ uden for determinanten er, at når vi faktoriserer determinanten, svarer det til at gange faktoren på for kun én række.

![[Pasted image 20250521134004.png]]
Vi kan aflæse rødderne uden at gange ud, da rødderne fremgår i ligningen. Første led bliver nul hvis lambda = -2 osv.

### 5

![[Pasted image 20250528093338.png]]
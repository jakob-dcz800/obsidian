# Elementærmatrix
En matrix er en **elementærmatrix** hvis den er resultatet af at udføre *netop en* af tre nedenstående rækkeoperationer på [[Kvadratmatricer#Enhedsmatrix|enhedsmatricen]]:
	• tal gange en række lægges til en anden række 
	• en række ganges med et tal, forskellig fra 0 
	• to rækker ombyttes
Elementærmatricen er lig med resultatet af matricen efter en rækkeoperation.
## Multiplikation med elementærmatricen

![[Pasted image 20250429210732.png]]

At lave en rækkeoperation på en matrix er det samme som at gange den tilsvarende elementærmatrix på matricen fra venstre
Rækkeoperationer er nøjagtigt det samme som at gange matricer
### Eksempel
Eksemplet viser, at flere rækkeoperationer efter hinanden svarer til at gange flere elementærmatricer på i den rigtige rækkefølge!
![[Pasted image 20250430102843.png]]
Er det samme som
![[Pasted image 20250430102856.png]]
Godt til algoritmer og programmering!
Rækkefølgen er meget vigtig.
Når man ganger på fra venstre, går man ind fra højre
[[LINALG Lineær algebra/Matricer/Matrixmultiplikation|Matrixmultiplikation]]
## Theorem

### 2.8
Elementærmatricer er [[Invers matrix#Definition|invertible]]

Hvorfor er det nu sådan? 
	• Har du byttet om på to rækker, så byt om igen
	• Har du ganget en række med $t \not= 0$, så gang den med $\frac{1}{t}$ 
	• Har du lagt $s$ gange række $i$ til række $j$, så læg $−s$ gange række $i$ til række $j$

Alle virkningerne kan gå ud med hinanden.
### Eksempel
![[Pasted image 20250430103443.png]]

### 2.9

![[Pasted image 20250430104910.png]]
## Produkter

1. Antag, at A er [[Invers matrix#Definition|invertibel]]
2. Lav rækkeoperationer ($k$ stk. i alt) sådan, at $[A|I] \to [I|A^{−1}]$ 
3. Rækkeoperationerne svarer til $E_k · · · E_1A = I$
4. Dette giver: $A = E^{−1}_1 · · · E^{−1}_k$
5. Da er $A$ et **produkt af elementærmatricer**
## Eksempel

### 1

![[Pasted image 20250429211149.png]]
Svar: E1 men ikke E2
E1 er resultatet af 2r3+r1
udgangspunktet er en elementærmatrix

![[Pasted image 20250429211216.png]]
Svar: F2, for at omgøre det, tag -2 i toppen

### 2
Elementærmatricer som byggeklodser. Kan vi bygge følgende matrix af elementærmatricer.
Igen er rækkefølgen vigtig.
Dette kan godt gælde for n x n matricer
A må nødvendigvis være invertibel hvis den er et produkt af elementærmatricer om ER invertible.
Systemet bryder sammen hvis ikke.
![[Pasted image 20250429211429.png]]
![[Pasted image 20250429211437.png]]
![[Pasted image 20250430104547.png]]
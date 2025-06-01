# Lineære transformationer

Hvis du ikke fatter dette her, så se f6-del6.mp4
Det at have en lineær transformation svarer til at gange med en matrix.
## Definition

![[Pasted image 20250507141904.png]]

**Lineære transformationer er altså funktioner som gør noget, bare udtrykt som en matrix**

$T_A$ kaldes matrixtransformationen 
Matricer er bare talskemaer, nu kigger vi altså på funktioner der afbilleder vektorer over i nogle andre vektorer.
Vi skal altså kigger på nogle x'er og hvor ryger de hen i den nye vektor?
## Theorem

### 3.17
![[Pasted image 20250507141927.png]]

### 3.18
![[Pasted image 20250506214534.png]]
## Eksempel

Her er tre eksempler hvor vi skal finde de matricer som hører til.
### 1

![[Pasted image 20250506214520.png]]
Her sætter vi en vektor fra $\mathbb{R}^5$ over i $\mathbb{R}^4$
Transformationen $T_{A}()$ tager altså en vektor $v \in \mathbb{R}^5$ 
Værdien af transformationen afbilledes over i resultatet, altså en vektor $v \in \mathbb{R}^4$
Transformationen består af at gange matricen A med vektoren.
Hver gang vi kender en x-værdi, så kan vi regne $T_{A}(x)$ ??
### 2
Her har vi en funktion $\mathbf{R}_{\Theta}$ som afbilleder ind i sig selv.

![[Pasted image 20250506214549.png]]

Vi skal nu finde den matrix **der svarer til den lineære transformation** ($A_{\Theta}$)
Vi har altså brug for rotationens værdi for 1. og 2. basisvektor sat op som en matrix.
Vi skal vide, hvad gør transformationen ($\mathbf{R}_{\Theta}$) ved $e_{1}$? 
$e_{1}$ er den vektor som ligger ned.

Vi kan se, at billedet af den første basisvektor er $\begin{pmatrix}\cos \Theta \\ \sin \Theta\end{pmatrix}$
Vi ser så, at den anden basisvektor er $\begin{pmatrix}-\sin \Theta \\ \cos \Theta\end{pmatrix}$

![[Pasted image 20250506214559.png]]

Nu vil vi dreje en konkret vektor $\begin{pmatrix}3 \\ 2\end{pmatrix}$ med vinkel $\Theta = 40\degree$
Vi ganger den derfor på vores matrix som svarer til vores lineære transformation

![[Pasted image 20250506214607.png]]

### 3
Nu har vi $S$ som er en lineær transformation

![[Pasted image 20250506214619.png]]

Dette er en lineære transformation fordi:
Hvis vi lægger to vektorer sammen og spejler summen, er det det samme som at spejle to vektorer og dernæst lægge dem sammen!
### 4
![[Pasted image 20250506214626.png]]

Her har vi to lineære transformationer: $S, T$, Dvs. vi skal have to matricer.
Lad os tage udgangspunkt i $S$.

Sætning [[#3.18]] siger, at søjlerne i $A$, er billedet af $S$ af de tre [[Baser|basisvektorer]]
Dvs. første søjle i A er billedet af $S(e_{1})$

Vi ser geometrisk på figuren for at undersøge hvad $S(e_{n})$ bliver.
Når vi roterer omkring $x_{2}$ kommer $x_{1}$ over på $x_{3}$'s akse (bare $-x_{3}$)
$x_{2}$ bliver hvor den er og $x_{3}$ kommer ned på $x_{1}$

![[Pasted image 20250507150410.png]]


## Sammensætning af lineære transformationer


![[Pasted image 20250506214653.png]]

Man kan altså sammensætte lineære transformationer.
F.eks. først roter vektor, og så spejl den i førsteaksen.

## Eksempel 2

### 1
![[Pasted image 20250507150720.png]]
![[Pasted image 20250506214701.png]]

## Inverse lineære transformationer

![[Pasted image 20250506215004.png]]

Hvis din [[Lineære transformationer|lineære transformation]] både er [[Injektivitet og surjektivitet|injektiv og surjektiv]] (altså bijektiv), så er den reversibel, og kan derfor omgøres. Dette gør man ved at gange den inverse matrix på.
## Eksempel 3

### 1
![[Pasted image 20250506215011.png]]
![[Pasted image 20250506215023.png]]

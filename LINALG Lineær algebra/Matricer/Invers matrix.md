# Invers matrix

Den inverse matrix er uformelt at dividere en matrice.
Ikke alle matricer er invertible.

$Matrix⋅invers=I$
## Definition
En $n × n$ matrix $A$ er **invertibel** hvis der findes en $n × n$ matrix $X$ så
$$
XA = AX = I_{n}
$$
Matricen $X$ kaldes en invers til $A$. 
En invertibel matrix $A$ kaldes også **regulær** (eng. non singular), ellers kaldes den **singulær**.

Er der mere end en invers matrix for en invertibel matrix? **Der er kun en**
Hvis både $X_1$ og $X_2$ er inverse til $A$ så gælder
$$
X_2 = X_2I_n = X_2(AX_1) = (X_2A)X_1 = I_nX_1 = X_1.
$$
Konklusion: den inverse er entydigt bestemt. $X_{2}=X_{1}$
Den betegnes $A^{−1}$ 
og IKKE $\frac{1}{A}$

## Theorem

### Theorem 2.9 Highlight I: n ligninger med n ubekendte
Hvis $A$ er invertibel så har ligningen $Ax = y$ netop en løsning $x = A^{−1}y$

#### Bevis
Vi ganger med den inverse matrix fra venstre
$$
Ax = y \iff A^{−1}Ax = A^{−1}y  x = I_nx = A^{−1}y
$$
### 2.5 og 2.6
En $n × n$ matrix $A$ er invertibel *hvis og kun hvis* rank $A = n$

![[Lineær uafhængighed#3.5]]

### 5.6 Invers matrix og determinant
![[Pasted image 20250519143442.png]]

### 5.23
![[Pasted image 20250519144008.png]]

![[Pasted image 20250519144019.png]]
## Regning med inverse matricer

1. Hvis $A$ og $B$ er invertible, så er $AB$ også invertibel og der gælder
$$
(AB)^{−1} = B^{−1}A^{−1}
$$
	Bemærk rækkefølgen for A og B!
2. Hvis $A$ er invertibel, så er $A^T$ også invertibel og $(A^T )^{−1} = (A^{−1} )^T$
3. Hvis $A$ er invertibel, så er $A^{−1}$ også invertibel og $(A^{−1} )^{−1} = A$
4. Hvis $A$ er invertibel, og $s \not= 0$ så er $sA$ også invertibel og $(sA)^{−1} = s^{−1}A^{−1}$

## Spørgsmål
• Hvordan afgør vi om en given matrix er invertibel?
• Hvis en matrix er invertibel, hvordan kan vi så bestemme den inverse? 
	Hvordan finder vi X? 
	Vi bruger rækkeoperationer og rang til at bestemme dette

## Eksempel

### 1
![[Pasted image 20250519144142.png]]
## Dominometoden

![[Pasted image 20250429210154.png]]
![[Pasted image 20250429210205.png]]

### Udregning
Laver simple regneoperationer, resultatet bliver den inverse matrix på højre side.

## Bestemmelse af invers ved rækkeoperationer

### Computation
![[Pasted image 20250429210336.png]]
Computation kan også bruges til at løse matrixligninger af formen $AX = B$
Hvis A får en nulrække eller ikke bliver enhedsmatricen, har A ingen invers matrice.
Rangen skal være lig n. (n som i: n x n, antal rækker og søjler)

#### Opgave

![[Pasted image 20250430101911.png]]
![[Pasted image 20250430102037.png]]

### Formel uden rækkeoperationer for 2x2 matricer
![[Pasted image 20250430102200.png]]

Formlen for en 3x3 matrix fungerer ikke på denne måde.
## Højre- og venstreinverse

### Definition
• $X$ er en venstreinvers til $m × n$ matricen $A$ hvis $XA = I_n$ 
• $X$ er en højreinvers til $m × n$ matricen $A$ hvis $AX = I_m$
### Theorem 2.9
Lad $A$ være en $n × n$ matrix. 
1. Hvis $A$ har en venstreinvers $X$ så er $A$ invertibel og $X = A^{−1}$ 
2. Hvis $A$ har en højreinvers $X$ så er $A$ invertibel og $X = A^{−1}$
En ikke [[Kvadratmatricer|kvadratisk matrix]] kan have venstre- men ikke højreinverse (eller omvendt) og der kan være mange venstre- eller højreinverse!

### Theorem 2.10 generelle inverse
Lad $A$ være en $m × n$ matrix med rank $A = r$. Da gælder
1. $A$ har en højreinvers netop hvis $r = m ≤ n$
2. $A$ har en venstreinvers netop hvis $r = n ≤ m$

### Eksempel
1. Rang A = 2 fordi antallet af ikke-nulrækker. Rangen af A = Rangen af den transponerede A
2. Find X som ganget med A giver enhedsmatricen I
3. Der må være 4 ligninger med 6 ubekendte
	4 ligninger fordi produktet af AX giver 2x2 matrix (4 tal)
4. Der bliver gjort rækkeoperationer, resultatet giver to [[frie variable]]
	Frit valg for $s$ og $t$ - giver altid svaret uanset værdien.


![[Pasted image 20250429212151.png]]

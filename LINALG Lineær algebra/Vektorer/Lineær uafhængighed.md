# Lineær uafhængighed

![[Pasted image 20250505141809.png]]

På hvilken måde kan jeg opnå 0-voektoren som en linearkombination?
Hvis den eneste løsning er at sætte alle x'er til nul, er de **lineært uafhængige** (nulløsningen)
Hvis ikke kun nulløsningen gælder, er vektorerne **lineært afhængige**

![[Pasted image 20250505142248.png]]

## Theorem
### 3.3
Alternativ måde at udtrykke afhængighed på:
![[Pasted image 20250505143348.png]]
Hvis vektorerne er lineært afhængige, er det det samme som at skrive, at der findes en vektor der udgør spannet af de andre. 
Bemærk at i sættet undlades $v_{i}$
### 3.4
![[Pasted image 20250505142915.png]]
### 3.5
![[Pasted image 20250505142933.png]]
### 3.6
![[Pasted image 20250505142943.png]]

Uafhængighed = KUN nulløsningen
Afhængighed = mindst en fri variabel, altså flere end bare nulløsningen 
## Eksempel

### 1
![[Pasted image 20250505141943.png]]

Kan vi slutte, at alle $x$ skal være lig nul? Hvis ja, så er sættet af vektorer lineært uafhængige

![[Pasted image 20250505142009.png]]

Frie variable = uendeligt mange løsninger
Nu kigger vi kun på de to første vektorer:

![[Pasted image 20250505142159.png]]

### 2
![[Pasted image 20250505143334.png]]
Fordi der er flere end 4 vektorer må de være lineært afhængige.
Aka. hvis der er flere en $n$ vektorer, må de være lineært afhængige ($n$ som i $\Bbb{R}^n$)

# Lineær afhængighed

![[Pasted image 20250505142557.png]]

Her kunne man godt sætte en nulrække i matricen, det gør ikke noget at undlade den, men tag den for en god ordens skyld med.
Vi får:
$1v_{1}-1v_{2}+1v_{3}=0$
Der ER en fri variabel, derfor er der uendeligt mange løsninger = de er lineært afhængige.
Ydermere: rangen er kun 2, og der er tre vektorer, derfor er de lineært afhængige ([[#3.4]])
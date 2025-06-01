# Span

Span = udspænding

![[Pasted image 20250504173849.png]]
Vi har et set af $k$ vektorer $S$, i $\Bbb{R}^n$ 
$span\set{v_{1}, \dots, v_{k}}$ er alle de vektorer vi kan nå med at kombinere vektorerne $v_{1},\dots,v_{k}$

![[Pasted image 20250505135610.png]]

### Ordlyd
$v_{i}$ udspænder en delmængde:
$v_{i} = span\set{v_{1},\dots, v_{i-1}, v_{i+1},\dots , v_{k} }$
### Eksempel
![[Pasted image 20250504173932.png]]

findes der skalarer sådan at man opnår $u$, eller $e_1$?
Dette kan vi skrive op som et ligningssystem hvor vi først løser for $e_{1}$ og så $e_{2}$

![[Pasted image 20250505134633.png]]
![[Pasted image 20250505134820.png]]

Her har vi valgt $t=0$ som et eksempel. $t$ kan være hvad som helst.

![[Pasted image 20250505134910.png]]

$A$ er en matrix med søjlerne $v_{1},\dots,v_{k}$
$u$ ligger i spannet hvis og kun hvis ligningssystemet $\mathbf{Ax=u}$ kan løses (altså har en eller flere løsninger)

### Øvelse
![[Pasted image 20250507100403.png]]

## Eksempel på linearkombination:

![[Pasted image 20250505134351.png]]

(man kan ikke bevæge sig ud af dimensionen)
Aka. span er alle vektorer i planen
Vi **kombinerer vektorer for at få en ny vektor**, ved at gange vilkårlige konstanter på de originale vektorer. 

## Theorem

### 3.2

![[Pasted image 20250505135549.png]]
[[Underrum]]


![[Lineær uafhængighed#3.3]]
### Eksempel
Vi kan finde x'er som rammer alle u'er uanset hvad
![[Pasted image 20250507100737.png]]

Hvis vi skifter $v_{3}$ ud med $e_{1}$ så udspænder $v_{1},v_{2},e_{1}$ planen U
Dette vises her:

![[Pasted image 20250505135858.png]]

Hvis vi smider en ekstra vektor $w \in \Bbb{R}^3$ ind, så vil sættet fortsat udspænde $\Bbb{R}^3$, da den originale mængde gør.
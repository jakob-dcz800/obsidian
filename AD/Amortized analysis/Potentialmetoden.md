# Potentialmetoden

Variant af [[regnskabsmetoden]], mere generel og præcis:
Summen af opsparede $ udtrykkes ved en funktion
$$
\Phi(i) \geq 0
$$
>[!IMPORTANT] Defintion
>Den [[Amortized analysis|amortiserede]] omkostning $\hat{c}_{i}$ er den faktiske omkostning $c_{i}$ plus ændringen i potentialet, $\Phi(i)-\Phi(i-1)$:
$$ \hat{c}_{i}=c_{i}+\Phi(i)-\Phi(i-1) $$

>[!QUESTION] Eksempel
>$\Phi(i)$: antal 1'ere i den binære repræsentation af $i$ 
>Lad $t_{i}$: antal 1'ere der bliver til 0'er mellem $i-1$ og $i$
>Omkostningen $c_{i}$ ved at ændre $i-1$ til $i$ er $c_{i}=t_{i}+1$
>$$ \begin{align} \\
\hat{c}_{i} & = c_{i}+(\Phi(i)-\Phi(i-1)) \\
 & \leq (t_{i}+1)-(t_{i}-1)  \\
 & = 2
\end{align}   $$

>[!TIP]
>En gyldig potentialfunktion må aldrig være lavere end dens udgangspunkt
>"Vi må aldrig have mindre i banken end hvad vi startede med"
>
>Denne funktion er f.eks. aldrig lavere end hvad den starter med. $H$ er antallet af hobe:
>$$\Phi (H)=t(H)+2m(H)$$
## Samlet tid via amortisering

Vi vil gerne udtrykke den samlede tid for en sekvens af $n$ operationer.

![[Pasted image 20260211162525.png]]

>[!tip] Betydning af led
>$$ \hat{c}_{i}=c_{i}+\Phi(i)-\Phi(i-1) $$
>Vi har led:
>- $c_{i}$: 
>- $\Phi(i)$: Potentialet lige efter $i$'te operation
>- $-\Phi(i-1)$:Potentialet lige før $i$'te operation


# Rod cutting
## Eksempler

### Juni 24

![[Pasted image 20260330130052.png]]
Hvad betyder hvad her?
$p$ er listen af værdier.
$p_{1} = 2$ er værdien af stangen med længde 1
$$
p_{1} = 2,
p_{2} = 3,
p_{3} = 5,
p_{4} = 7,
p_{5} = 11,
p_{6} = 12,
$$
Lad os prøve iterationerne
1. først 0 pga. linje 2
2. så 2, pga. linje 6: $max\set{0, 2 + 0}$

svaret er **3**.
![[Pasted image 20260403192112.png|319]]
Når vi kommer til $p_{5}$, så får vi mere værdi pr. enhed.
> Kig på værdi pr. enhed:
>$$
 p_{1} = \frac{2}{1},
p_{2} = \frac{3}{2},
p_{3} = \frac{5}{3},
p_{4} = \frac{7}{4},
p_{5} = \frac{11}{5},
p_{6} = \frac{12}{6},
$$
> Eftersom, $\frac{11}{5}> \frac{1}{2}$, er det denne som vinder ved $p_5$


![[Pasted image 20260403185420.png|321]]

## Choosing a method

![[Pasted image 20260405162833.png]]
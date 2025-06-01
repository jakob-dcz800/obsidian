---
tags:
  - Algorithm
  - DMA
---
# Algoritmer, Basale Begreber

## Introduktion
### Hvad er en algoritme?

 - Sekvens af “computational” skridt som omdanner input til output
 - Redskab for at løse et veldefineret problem (computational)
 - Instance of a problem definerer en facet af det givne problem - f.eks. hvor input er en specifik værdig eller sæt af værdier
 - En algoritme er korrekt, når den spytter et korrekt resultat ud, inden for en endelig mængde tid
 - En ukorrekt algoritme, stopper måske ikke ved et givent input, eller giver et forket resultat
 - En algoritme skal være præcis i sin beskrivelse, men kan defineres som skriftsprog, computersprog mv.
 
### Eksemler på problemer, som algoritmer løser:
- The human genome project
- Internettet
	- search algorithms
	- sider som kan håndtere store datamængder
- e-Commerce
    - håndtering af personlige data (kryptering)
- NP complete problems
    - Ingen ved, om der findes en effektiv algoritme for NP-complete problemer
    - Hvis en effektiv algoritme findes for ét NP-complete problem, findes der en for alle
    - For NP-complete problemer, gælder det at bevise at problemet hører inde for den klasse af problemer, og i stedet udvikle en algoritme for at approksimere løsningen
    - Travelling salesman problemet er et af disse
    - Kun algoritmer som resulterer i et ja/nej svar kan være NP-complete
- Bogen antager at al data (input) er til stede når algoritmen kører
    - Algoritmer som modtager data over tid kaldes online algorithms (se kap 27 CLRS)
## Pseudokode

Der er ingen fastsat syntaks i pseudokode. Der er altså ingen præcis definition på, hvad som er korrekt pseudokode. Dog er det en fordel at holde sig til standarden for læsbarhedens skyld.

### Variabler

```
Example1(n)
	a = 5
	b = a + n
	return b
```

Variabler findes ikke før de er defineret. `return` definerer, at kodeblokken er slut og returnerer den givne værdi. 

```
Example2()
	x = 7
	x = x + 1
	y = x + 2
	return y
```

### Brug af funktioner

```
Example3(n)
	a = Example1(2n)
	b = Example2()
	return a + b
```

Undgå at genbruge samme navn for flere variabler.

### If / else

```
Example4(n)
	a = 5
	if n ≥ 4
		return a
	else
		return n
```

```
Example5(n)
	x = 7
	x = x + 1
	if n == 3 or n is even
		x = x + 1
		n = n + 1
	x = x + n
	return x
```

Hvis `n == 3 or n is even` returnerer `false` , springer koden til linje 6. Den springer altså koden inde i `if` over.

### For loops

```
Loop1(n)
	for i from 1 to n
		print i
	print 15
```

Kodeblokken inde i loopet, kaldes en _iteration._

### While loops

```
Loop2(n)
	i = 1
	while i ≤ n
		print i
		i = i + 1
	print 15
```

Hvis testen er `true` , løber kodeblokken i `while` en ekstra gang. Så snart den er `false` hopper vi ud af loopet.

### Detaljeniveau

Det er vigtigt at overveje om din pseudokode er detaljeret nok. I nogle kontekst skal den være rimelig detaljeret.

```
PrimeSum(n)
	s = 0
		for i from 1 to n
			if i is a prime number
				s = s + i
	return(s)
```

Her kan man tilføje en paragraf som refererer til metoden der benyttes, f.eks:

> “Testing in line 3 whether i is a prime number can be done as described in Chapter X of the book Y.”

Common knowledge skal i de fleste tilfælde uddybes og forklares.

### Uendelige løkker

Pas på med loops som ikke stopper - særligt ved brug af `while`

```
L(n)
	i = 5
	while i ̸= n
		print i
		i = i + 1
```

### Nested vs. sequential loops: The importance of indentation

```
TwoLoops1(n)
	for i from 1 to n
		print i
	for j from 1 to n
		print j
```

```
TwoLoops2(n)
	for i from 1 to n
		print i
		for j from 1 to n
			print j
```

### Arrays

Et array er en afgrænset mængde af værdier. Ethvert element kan indekseres: $A[i]$.

Arrays kan i princippet 1-indekseres, altså hvor 1 specificerer den første værdi i et array, men det er smartest at 0-indeksere:

$A[0], A[1],...,A[n-1]$
	
Man kan 0- eller 1-indeksere som man har lyst og det afhænger af algoritmen.

Tanken med $n$, er som udgangspunkt at fortælle algoritmen hvor langt arrayet er hvorimod $n-1$ bruges til at indeksere.

$array[index] = entry$

_Entries_ kan være alle former for værdier.

Entries kan også tildeles en værdi på lige fod med variabler

`A[0] = x`

Eksempel på algoritme, som summerer værdierne af et array

```
Sum(A, n)
	s = 0
	for i from 1 to n
		s = s + A[i]
	return s
```

Eksempel på algoritme, som inverterer rækkefølgen på _entries_

```
Reverse(A, n)
	let B be a new array of length n
	for i from 0 to n − 1
		B[i] = A[n − 1 − i]
	return B
```

I nogle tilfælde vil længden af et array være repræsenteret som værdien `A.length`. `n` vil i så fald ikke være nødvendig.

For at opdatere et entry, må det gøres enkeltvist: `A[i] = x`.


## Imperative/funktionelle paradigme

Imperativ programmering minder om pseudokode, og fungerer som en computer vil gøre det. Maskinkode er også imperativ, derfor er det imperative paradigme tæt på computerens hardware.
Man bruger imperativ programmering når man tænker og udvikler algoritmer.

Funktionsprogrammering oversættes til imperativ maskinkode.
Ingen variable og ingen loops - alt kaldes i funktioner (ligesom i f# hvor alt er en expression).
Det siges, at det er lettere at læse.
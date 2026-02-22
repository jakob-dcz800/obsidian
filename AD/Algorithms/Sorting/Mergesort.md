# Merge-sort

> [!INFO]
> Merge-sort kører i værste tilfælde $\Theta(n \lg n)$

Merge-sort gør brug af [[divide and conquer]] ved at dele den originale array `A[1:n]` op, og derefter løse samme problem for en sub-array som passes ned i samme funktion (`A[p:r]`)

1. Divide: Del arrayet op i sub-arrays `A[p:r]` ved at finde mid: $q=\lfloor \frac{r-p}{2} \rfloor$. Sub-arrays bliver altså `A[p:q] & A[q + 1 : r]`
2. Conquer: Ved at sorterer resultatet af de to sub-arrays rekursivt. De sorteres ved at vi kalder funktionen vi er i: `MERGE(A, p, q, r)`
3. Combine: Ved at sammenlægge de to sorterede arrays `A[p:q] & A[q + 1 : r]`. Vi ender altså med `A[p:r]`

Funktionen kan ikke kalde sig selv igen når `A.length == 1` altså når `p == q`
Som tidligere nævnt er et array med kun 1 element altid sorteret.
Nøglen er derfor i *combine*-delen af algoritmen når vi bevæger os tilbage op ad træet.

## Køretid

> Merge-sort kører i værste tilfælde $\Theta(n \lg n)$

For at undersøge [[Time complexity|køretiden]] indfører vi rekursionsligningen:
$$
T(n)=
\begin{cases}
\Theta(1) & \text{if } n=1 \\
T(\lceil n/2 \rceil )+T(\lfloor n/2 \rfloor ) + \Theta(n) & \text{if } n > 1
\end{cases}
$$
Hvor $T(n)$ er worst-case køretid for liste af $n$ elementer - ikke et udtryk for den [[Asymptotic notation|asymptotiske køretid]].
Se [[Rekursionsligninger#Eksempel|løsning]]

![[Recursion trees#Mergesort Merge-sort]]
## Merge funktionen

> [!INFO]
> Merge kører i tid $O(k_{1}+k_{2})$, hvor $k_{n}$ er længden af liste $n$

`MERGE` er en hjælpe funktion som er del af `MERGE-SORT` funktionen. `MERGE` antager at de to sub-arrays allerede er sorterede internt.

For at merge de to arrays, kigger [[Algorithms|algoritmen]] på den første værdi i begge arrays, og lægger den mindste værdi af de to i output-arrayet.

```jsx
if (arr1[first] > arr2[first]) {
	output_array.push(A[0])
}
```

Siden operationen som udføres tager konstant tid, tager denne algoritme altså $\Theta(n)$ tid.

Forklaring:

$L$ er en kopi af det ene sub-array `A[p : q]`
$R$ er en kopi af det andet sub-array `A[p + 1 : r]`
$n_L$ og $n_R$ er længden af de respektive arrays

$i$ indekserer $L$
$j$ indekserer $R$

$k=p$ fortæller hvor i $A$ algoritmen skal placere de sorterede tal

![[Pasted image 20260209142217.png]]
![[Pasted image 20260209142415.png]]
## Pseudo kode

```python
def MergeSort(A, p, r)
	if p < r:                            # check for base case
		q = floor((p + r) / 2)           # divide
		MergeSort()                      # conquer
		MergeSort()                      # conquer
		Merge()                          # combine
```

```python
def Merge(A, p, q, r)
	n1 = q - p + 1
	n2 = r - q
	let L[1 .. n1 + 1]    # be a new array
	let R[1 .. n2 + 1]    # be a new array
	
	for i = 1 to n1:
		L[i] = A[p + i - 1]
		
	for j = 1 to n2
		R[j] = A[q + j]
	
	L[n1 + 1] = ∞
	R[n2 + 1] = ∞
	i = 1
	j = 1
	
	for k = p to r:
		if L[i] <= R[j]
			A[k] = L[i]
			i = i + 1
		else A[k] = R[j]
			j = j + 1
	
```

> Antal elementer, der skal sorteres: **`n = r − p + 1`**

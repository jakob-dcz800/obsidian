
# Parallel Pseudocode

![[Pasted image 20260318135813.png]]
### Sekventiel
```python
SUM-ARRAYS(A, B, C, n)
	for i = 1 to n
		C[i] = A[i] + B[i]
```

### Parallel
```python
SUM-ARRAYS(A, B, C, n)
	parallel for i = 1
		C[i] = A[i] + B[i]
```

![[Pasted image 20260318135900.png]]

**Spawn**: kald en procedure parallelt
**Sync**: vent på at alle parallelle kald returnerer fra denne procedure (altså de kald som er foretaget i denne procedure)
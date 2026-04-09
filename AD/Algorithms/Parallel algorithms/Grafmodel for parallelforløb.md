# Grafmodel for parallelforløb
parallel trace

**Knuder**: (Grupper af) instruktioner 
	“strands"
**Kanter**: Afhængigheder mellem instruktioner
	“Hvad er nødt til at være beregnet før denne instruktion kan udføres?”
![[Pasted image 20260318124528.png|250]]

## Eksempel

```python
RECURSIVE_SUM(A, l, r)
	if l = r
		return A[l]
	mid = floor((l + r)/2)
	lSum = RECURSIVE_SUM(A, l, mid)
	rSum = RECURSIVE_SUM(A, mid + 1, r)
	return lSum + rSum
```

![[Pasted image 20260318130022.png]]


## Spatial locality 

Accessing data that **is close** to the data **that was recently accessed**
![[Pasted image 20260108181750.png]]
## Temporal locality

Accessing data that was **recently** accessed
![[Pasted image 20260108181759.png]]
## Stride 
How large are the jumps between memory accesses?


### Example

```c
for(i=0: i<8; i++) {
	for(j=0; j<8000; j++)
		A[i][j] = B[i][0] + A[j][i]
}
```

q: Which variable reference(s) exhibit temporal locality?
a: 
- `i`: remains constant each time J runs
- `B[i][0]`:  is accessed 8000 times within each `i` loop
- `j`: is accessed more times in each iteration of the inner loop

q: Which variable reference(s) exhibit spatial locality?
a:
- `A[j][i]`: succeeds the previous `A[j - 1][i]` and preceeds `A[j + 1][i]`
- As `j` increases in the loop, (`A[I][0]`, `A[I][1]`, `…`, `A[I][J]`) the elements are accessed consecutively in the same row for `A`

## Order
![[Pasted image 20260108182008.png]]

### Row-major order 
(used in C)

![[Pasted image 20260108181957.png]]

### Column-major order 
(used in MatLab)

![[Pasted image 20260108182026.png]]
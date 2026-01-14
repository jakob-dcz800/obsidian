# Cache performance metrics
Huge difference between a hit and a miss!
Could be 100 × between L1 and main memory.
99% hit rate may be twice as good as 97%

Cache hit time: 1 cycle 
Miss penalty: 100 cycles 
Average access time
$$
\begin{align}
97\% \text{ hits} & : \space 1\text{ cycle }+ 0.03 \times 100 \text{ cycles }=4 \text{ cycles} \\
99\% \text{ hits} & : \space 1\text{ cycle }+ 0.01 \times 100 \text{ cycles }=2 \text{ cycles}
\end{align}
$$
> This is why we use miss rate instead of hit rate. 
## Miss rate
Fraction of memory references not found in [[Cache|cache]]
$$
\frac{\text{misses}}{\text{hits}}
$$
Typical values:
- 3-10% for [[CompSys/Hardware/Memory hierarchy#Cache|L1]]
- Can be very small for [[CompSys/Hardware/Memory hierarchy#Cache|L2]] (<1%)

## Hit time
Time to deliver a cache block to the [[Hardware terms#CPU|processor]].
Includes time to determine whether a [[Cache#Cache hit|hit]] (checking tag).

Typical values:

L1: 4 clock cycles
L2: 10 clock cycles
L3: 40-75 cycles (depends on sharing, since L3 is shared)

## Miss penalty

Additional time needed because of a [[Cache#Cache miss|miss]].
Often over 100 cycles for main [[Hardware terms#DRAM|DRAM]] memory, historically increasing. 


# Writing cache friendly code

Make the common case go fast. 
- Focus on inner loops. 
- Optimising non-loopy code is almost never worth it

Ensure good locality. 
- Avoid chasing ad-hoc [[pointers]]
- If you [[Dynamic memory#malloc|malloc()]] a million tiny blocks of [[Virtual memory|memory]], there is no guarantee they will be anywhere near each other. 
- [[Linked lists]] are terrible. 

Minimise footprint. 
- E.g. if all the data you work on fits in L3 cache, then you will never see an L3 cache miss after the initial ones.

## Example - matrix multiplication

- Multiply n-by-n matrices in [[LINALG/Matricer/Matrixmultiplikation#Order|row-major order]]. 
- Each element is a double
- $O(n^3)$ total operations. 
- $n$ values summed per destination

```c
// for each row
for (int i=0; i<n; i++) { 
	// for each column
	for (int j=0; j<n; j++) { 
		double sum = 0.0; 
		
		for (int k=0; k<n; k++) {
			// for each row in b
			sum += a[i][k] * b[k][j]; 
			// k = n^3
			// j = n^2
			// i = n
		}
		c[i][j] = sum;
	} 
}
```

Assume:
- Assume Cache block size `B = 64 bytes` 
	- Enough for 8 doubles. 
- $n$ is very large - approximate $1/n$ as $0$. 
- Cache is not even big enough to hold a single row or column.

**Look at access pattern of inner loop**
When accessing successive elements miss rate is `sizeof(double)/B = 0.125`
$$
\text{miss rate } =
\frac{\text{sizeof(double)}}{B}
=\frac{8}{64}
=0.125
$$

```c
for (int k=0; k<n; k++) 
	sum += a[0][k]
```

When accessing distant elements miss rate is `1`.
```c
for (int k=0; k<n; k++) 
	sum += a[k][0]
```

### Matrix multiplication (ijk)
```c
for (int i=0; i<n; i++) { 
	for (int j=0; j<n; j++) { 
		double sum = 0.0; 
		
		for (int k=0; k<n; k++) {
			sum += a[i][k] * b[k][j];  
		}
		c[i][j] = sum;
	} 
}
```

Misses:

| a       | b   | c   |
| ------- | --- | --- |
| $0.125$ | $1$ | $0$ |
### Matrix multiplication (jik)
> column first

```c
for (int j=0; j<n; j++) { 
	for (int i=0; i<n; i++) { 
		double sum = 0.0; 
		for (int k=0; k<n; k++) {
			sum += a[i][k] * b[k][j]; 
		}
		c[i][j] = sum 
	} 
}
```

| a       | b   | c   |
| ------- | --- | --- |
| $0.125$ | $1$ | $0$ |

### Matrix multiplication (kij)
```c
for (int k=0; k<n; k++) { 
	for (int i=0; i<n; i++) { 
		double r = a[i][k]; 
		
		for (int j=0; j<n; j++) {
			c[i][j] += r * b[k][j]; 
		}
	} 
}
```

| a   | b       | c       |
| --- | ------- | ------- |
| $0$ | $0.125$ | $0.125$ |
### Matrix multiplication (ikj)
```c
for (int i=0; i<n; i++) { 
	for (int k=0; k<n; k++) { 
		double r = a[i][k]; 
		
		for (int j=0; j<n; j++) {
			c[i][j] += r * b[k][j]; 
		}
	} 
}
```

| a   | b       | c       |
| --- | ------- | ------- |
| $0$ | $0.125$ | $0.125$ |
### Matrix multiplication (jki)
```c
for (int j=0; j<n; j++) { 
	for (int k=0; k<n; k++) { 
		double r = b[k][j]; 
		
		for (int i=0; i<n; i++) {
			c[i][j] += a[i][k] * r;
		}
	} 
}
```

| a   | b   | c   |
| --- | --- | --- |
| $1$ | $0$ | $1$ |
### Matrix multiplication (kji)
```c
for (int k=0; k<n; k++) { 
	for (int j=0; j<n; j++) { 
		double r = b[k][j]; 
		
		for (int i=0; i<n; i++) {
			c[i][j] += a[i][k] * r; 
		}
	} 
}
```

| a   | b   | c   |
| --- | --- | --- |
| $1$ | $0$ | $1$ |
### Overview

ijk and jik (inner loop): 
- 2 loads, 0 stores 
- 1.125 misses/iter

kij and ikj (inner loop): 
- 2 loads, 1 store 
- 0.25 misses/iter

jki and kji (inner loop): 
- 2 loads, 1 store 
- 2 misses/iter 
-
![[Pasted image 20260108181502.png]]
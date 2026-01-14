**Latency**: essentially the running time ($T_{n}$) of a program ($P_{n}$)
	Then the speedup in latency of $P_2$ over $P_1$ is
$$
	\frac{T_{1}}{T_{2}}
$$
**Throughput**: when programs run 'forever'. How much data does it produce in a given time.
	Then the speedup in throughput of $P_2$ over $P_1$ is
$$
	\frac{Q_{2}}{Q_{1}}
$$
**Strong scaling**: How the runtime varies with the number of processors for a fixed problem size.
**Weak scaling**: How the runtime varies with the number of processors for a fixed problem size relative to the number of processors.

> Strong scaling is **not** better than the weak one


## Amdahl's Law

Predicts strong scaling.

If $p$ is the proportion of execution time that benefits from parallelisation, then $S(N)$ is maximum theoretical speedup achievable by execution on $N$ threads, and is given by
$$
S(N) = \frac{1}{(1-p) \frac{p}{N}}
$$
Note that $S(N)\leq \frac{1}{1-p}$
Potential speedup by optimising part of system is bounded by proportion of part in overall runtime.
> We should optimise the parts that take a long while to run.

![[Pasted image 20251008132315.png]]

## Gustafson's Law

Predicts weak scaling.

![[Pasted image 20251008132345.png]]


![[Pasted image 20251008132431.png]]
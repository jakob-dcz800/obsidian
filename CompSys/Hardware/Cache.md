---
tags:
  - Hardware
  - Datastructure
---
> **Definition**
> A smaller, faster storage device that acts as a staging area for a subset of the data in a larger, slower device
> 
> **Idea**
> The smaller and faster device at level k acts as a cache for the larger and slower device at level k+1

![[Pasted image 20260108112536.png]]
# Structure

![[Pasted image 20260108113436.png]]

$$
\text{Cache size} = 
\text{Sets } \times
\text{ Lines } \times
\text{ Bytes in block}
$$
## Address structure

We have sets: $S=2^n$ with data size in (bytes) $B=2^m$.
A $w\text{-bit}$ address into fields (each bit is $x_{i}$)

![[Pasted image 20260108114029.png]]
We look up an address in the cache by splitting the address into fields and looking up and checking based on their values. 

- **tag**: The rest
	- $t=\text{bytes in address }-(S+B)$
- **set index $S$**: How many bits needed to represent the sets
	- $\text{set count }= \frac{\text{cache size in bytes}} {n\times\text{block size in bytes}}$
	- $S = \log_{2}(\text{set count})$
- **block offset $B$**: How many bits needed to represent a block
	- $B = log_{2}(\text{Block size in bytes})$

![[Pasted image 20260108114247.png]]

![[Pasted image 20260108120145.png]]

# Types of cache
## [[Direct mapped cache]]
![[Direct mapped cache#Characteristics]]

## [[Associative cache]]
![[Associative cache#Characteristics]]

## [[Set-associative cache]]
![[Set-associative cache#Characteristics]]

# Cache hit

![[Pasted image 20260108112642.png]]
## Example


# Cache miss

![[Pasted image 20260108112849.png]]

## Types of misses

**Cold / compulsory miss**
Occur when the cache is empty. Unavoidable when a program first starts.

**Conflict miss**
Most caches limit blocks at level $k + 1$ to a small subset of the slots at level $k$. 
	Example: Block $i$ can only be located in slot $i \space \% \space 4$.
Causes conflicts when cache is large enough, but the blocks being accessed all map to the same slot.

**Capacity miss**
Occurs when program *working set* exceeds size of cache. 

# Questions

What if there is no space?
	Is FIFO or other types used?
What about writing
## Direct mapped cache 

### Characteristics
> one line per set
- **Simplicity :** Very simple to implement due to fixed mapping.
- **Low Cost :** Requires fewer hardware resources.
- **Collision :** High chance of conflict misses because multiple blocks compete for the same cache line.
- **Tag Size :** Relatively smaller, as each cache line corresponds to only one memory block.

### Example scenario 
- Cache size = 8 lines (Line 0 to Line 7)
- Main memory has 32 blocks (Block 0 to Block 31).

**Mapping Rule:** Each block maps to one specific cache line using the formula:
$$
\text{Cache Line}=\text{(Block Number) } \space \% \space \text{ (Number of Cache Lines)}
$$
**Mapping Process:**
- Block 0 → Line 0
- Block 1 → Line 1
- Block 8 → Line 0
- Block 17 → Line 1
If both Block 0 and Block 8 are frequently accessed, they will compete for Line 0. This results in **conflict misses**, as only one block can occupy Line 0 at a time.

## Example 1

![[Pasted image 20260108120728.png]]

## Example 2

- Addresses are 10 bits
- Lines have length 8 bytes (of data, i.e. the block size) 
- There are **4 sets** of **1 line**

![[Pasted image 20260108123618.png]]

1. [[Cache#Types of misses|Cold miss]], since the cache is empty, a miss is compulsory. Block is written to cache.
2. [[Cache#Cache hit|Cache hit]], set `00`, tag `00000` is found and data is returned
3. [[Cache#Cache miss|Cache miss]], set `11` is empty and block is written to cache from memory
4. [[Cache#Cache miss|Cache miss]], set `00` is found, but tag `00001` is not present. Data is missing and thus overwritten with memory.
5. [[Cache#Cache miss|Cache miss]], set `00` is found, tag `00000` is not found. Data is missing and thus overwritten with memory.
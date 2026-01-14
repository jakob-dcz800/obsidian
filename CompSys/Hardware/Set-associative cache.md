## Set-Associative Mapping

How many sets are in $n$-way associative cache?
$$
\text{set count }= 
\frac{\text{cache size in bytes}}
{n\cdot\text{block size in bytes}}
$$


Set-associative mapping is a hybrid approach that combines aspects of direct and associative mapping. The cache is divided into sets, and each memory block maps to exactly one set. Within that set, a block can occupy any cache line.
### Characteristics
- **Flexibility in Sets :** Reduces conflict misses compared to direct mapping.
- **Moderate Cost :** Balances cost and complexity between direct and associative mapping.
- **Replacement Policy :** Similar to associative mapping, replacement policies like LRU or FIFO are used within each set.
- **Tag Size :** Smaller than fully associative mapping, as the tag identifies blocks within a set.
- **Example scenario:**
- Cache size = 8 lines (Line 0 to Line 7)
- Cache is divided into **4 sets**, with 2 lines per set (2-way set-associative).
- Main memory has 32 blocks (Block 0 to Block 31).
$$
\text{Set Number }=\text{ (Block Number) } \space \% \space \text{ (Number of Sets)}
$$
### Mapping
$$
\text{Set Number }=\text{ (Block Number) } \space \% \space \text{ (Number of Sets)}
$$
**Mapping Rule:** Each block maps to a specific set using the formula:
_Set Number=(Block Number) mod (Number of Sets)_

Within the set, the block can occupy **any line**.

**Mapping Process:**
- Block 0 → Set 0 (can go into Line 0 or Line 1 within Set 0).
- Block 8 → Set 0 (competes with Block 0 for one of the two lines).
- Block 1 → Set 1 (can go into Line 2 or Line 3 within Set 1).

### Example Access
1. Block 0 is placed in Set 0, Line 0.
2. Block 8 is placed in Set 0, Line 1.
3. If Block 16 (also maps to Set 0) is accessed, one of the lines in Set 0 will be replaced (e.g., evicting as per replacement policy used in implementation).

## Example 1

- Addresses are ?? bits
- Lines have length 8 bytes (of data, i.e. the block size) 
- There are **4 sets** of **2 lines**

![[Pasted image 20260108124720.png]]

## Example 2
$$
\text{10-bit addresses, } B=8,S=1,L=2
$$
Simulation of 2-way set-associative [[cache]]
- Addresses are 10 bits
- Lines have length 8 bytes (of data, i.e. the block size) 
- There are **2 sets** of **2 lines**
- 
But it says $S=1$?
This is because we need one bit to represent which set we need: 0 or 1.
![[Pasted image 20260108125054.png]]
Lines are vertical instead of horizontal here:
![[Pasted image 20260108125353.png]]
1. [[Cache#Types of misses|Cold miss]], compulsory and block inserted at line `0`
2. [[Cache#Cache hit|Cache hit]], set `0` is found with correct tag, block is returned
3. [[Cache#Cache miss|Cache miss]], set `1` is empty and memory is inserted at line `0`
4. [[Cache#Cache miss|Cache miss]], set `0` has room for one more since tags are different. Miss and insert.
5. [[Cache#Cache hit|Cache hit]], set `0` with tag `010001`
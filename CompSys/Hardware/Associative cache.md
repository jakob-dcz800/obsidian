---
tags:
  - Hardware
  - OS
---
## Associative mapping
### Characteristics
- **Cache is one set.**
- **Flexibility :** Any block can go into any cache line, reducing *conflict misses*.
- **High Cost :** Requires associative hardware to search all cache lines simultaneously (Content Addressable Memory or CAM).
- **Replacement Policy :** Requires an algorithm like *LRU* (Least Recently Used) or *FIFO* (First In, First Out) to handle cache replacements.
- **Tag Size :** Larger compared to direct mapping, as the tag must uniquely identify blocks in all cache lines.
In associative mapping, a memory block can be placed in any cache line. There is no fixed mapping; **the placement is entirely flexible**.

> Probably unused in this course
> Aka. "fully associative"

If the cache has space for 8 blocks, and it is fully associative, it would be **8-way set associative**
### Example scenario
- Cache size = 8 lines (Line 0 to Line 7)
- Main memory has 32 blocks (Block 0 to Block 31).

**Mapping Rule:** A block can be placed in **any cache line**.
**Mapping Process:**
- Block 0 can go into any cache line (Line 0 to Line 7).
- Block 8 can also go into any cache line.

**Example Access:**
1. Block 0 is placed in Line 3.
2. Block 8 is placed in Line 5.  
    There’s no restriction, so blocks don’t compete for specific lines.

If the cache is full, a **replacement policy** is applied. For example if LRU (Least Recently Used) is used and Line 3 is the least recently used, Block 0 will be evicted to make space for the next incoming block.
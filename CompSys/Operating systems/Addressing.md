---
tags:
  - OS
---

# Virtual addressing

Virtual memory is provided by the the [[Operating systems|operating system]].
A process can request access to a virtual [[Memory and registers|memory]] address, and the OS will then access the address for the program.
The operating system will manage and [[Address translation#Address translation|map virtual memory]] to the physical memory.

Conceptually, virtual [[CompSys/Hardware/Memory hierarchy|memory]] is an array of N contiguous bytes stored on [[Hardware terms#Disk|disk]] (from a [[CompSys/Hardware/Memory hierarchy|caching]] perspective!)

![[Pasted image 20250928175254.png]]

- Used in all modern servers, laptops, and smart phones
- One of the great ideas in computer science

- Makes better use of memory
	- Some VM can be stored in [[Hardware terms#DRAM|DRAM]] as a cache
- Each process gets the same uniform address space
- One process can't interface with another processes memory

[[Pointers|Pointer]]-[[Values and data|values]] are all within the virtual address space

![[Pasted image 20250928181559.png]]

- Unallocated: there is an address, but it is unused
- When it *is* allocated, it can either be cached or un-cached
- Cached: data is physically in the RAM
- Un-chached: not in RAM but written back to disk
## Address spaces

- Linear: Ordered set of contiguous non-negative integer addresses
	- $\{0,1,2,3\dots\}$
- Virtual: Set of $N = 2^n$ virtual addresses
	- $V=\{0,1,2,3,\dots N-1\}$
	- Is linear
- Physical: Set of $M = 2^m$ physical addresses
	- $P=\{0,1,2,3,\dots M-1\}$
	- Is linear

Virtual and physical are not necessarily the same size.
# Physical addressing

Direct addressing.
This isn't really used in modern computers.

![[Pasted image 20250928175219.png]]
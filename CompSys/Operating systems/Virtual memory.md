
# Definition

*Memory management technique that creates an “idealized abstraction of the storage resources” available on a large, contiguous [[Memory hierarchy|memory]] space regardless of the underlying physical memory.*

**Purpose**
It enables systems to run larger applications or multiple programs simultaneously by utilizing both physical memory (RAM) and secondary storage (disk).
## Benefits

- Isolation: Each process operates in its own virtual address space, enhancing security and stability. 
- Efficient Memory Use: Allows for more processes to run concurrently by utilizing disk space to extend RAM. 
- Simplified Programming: Programmers can write code without worrying about the physical memory limitations or allocation.
## Key Concepts
- **Virtual Address space**: The range of addresses that an application can use, which the [[Operating systems|operating system]] maps to physical. 
- **Paging**: Divides virtual memory into **fixed-size blocks called pages**, which correspond to blocks in physical memory known as frames. 
- **Segmentation**: Divides virtual memory into **variable-sized** segments based on logical divisions within a program, such as functions or data structures.

![[Pasted image 20260120103129.png]]

## Functionality

### [[Address translation]]
Address Translation: The Memory Management Unit ([[MMU]]) translates virtual addresses (**VA**) to physical addresses (**PA**). 

### Page Tables
Data structures that store the mapping between virtual pages and physical frames.

### Demand Paging: 
Pages are loaded into physical memory only when they are needed, reducing the initial load time and memory usage. 

## Page Replacement Algorithms

- FIFO (First-In-First-Out): Replaces the oldest page in memory. 
- LRU (Least Recently Used): Replaces the page that hasn’t been used for the longest period. 
- Optimal: Replaces the page that will not be used for the longest time in the future (Theoretical). 

## Allocation Strategies

- Equal Allocation: Each process receives an equal share of the available frames. 
- Proportional Allocation: Frames are allocated based on the size or priority of each process. 
- Global vs Local Allocation: Determines whether page replacement can occur across all processes (global) or is restricted to the process that caused the page fault (local). 
# OS managing

Most of memory management takes place in software.
Only the [[MMU]] exists in hardware.

Each process memory might have a structure like this:

![[Pasted image 20251004111756.png]]

Text is program code i.e. 'read only'.
Data is variables and dynamic declarations.
[[Dynamic memory#malloc|Malloc]] will occupy the space in between sl and data

## Virtual memory areas

Every vm area is backed up by a disk object (a location on disk) since we cannot write to virtual memory - as it is not writeable.

[[Address translation|terms]]
Translation between VA and PA is called **mapping**

### Backing
Any area can be **backed**
This is when we populate a vm area with initial values from a file on [[Hardware terms#Disk|disk]]
Anonymous file = empty file

## Challenges and Considerations
- **Thrashing**: Occurs when excessive paging operations reduce overall system performance.
- **Overhead**: Maintaining page tables and performing address translations can introduce computational overhead.
- **Security**: Ensuring that processes cannot access each other’s memory spaces without permission.
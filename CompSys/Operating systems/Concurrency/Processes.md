
## Traditional model of a process

A process consists of three parts: 
1. A [[Virtual memory|virtual memory space]].
	1. Contains stack, code, heap, data, etc. 
2. A kernel context. 
	1. PID, open files, signal mask, parent PID, list of children, etc. 
3. An execution context.
	1. Registers (including special ones like the program counter). 

When processes are running [[Concurrency|concurrently]] on the same CPU, these are the things that are swapped out.
## Multi-threaded process model

A process consists of three parts: 
1. A virtual memory space.
	1. Contains stack, code, heap, data, etc. 
2. A kernel context. 
	1. PID, open files, signal mask, parent PID, list of children, etc. 
3. One or more [[Threads]], each containing.
	1. An execution context - Registers (including special ones like the program counter).
	2. A kernel thread context - Thread ID (TID), and a few other things that do not matter.

## Threads contra processes

### Similarities

Each has its own logical control flow. 
Each can run concurrently with others (possibly also parallel). 
Each is context switched.

### Differences

Threads share code and data. 
	[[Processes]] typically do not. 
Threads are cheaper to create and maintain than processes. 
	Take with a grain of salt; both are plenty fast on Linux. 
	But switching between threads within a process does not require switching to a new virtual address space.
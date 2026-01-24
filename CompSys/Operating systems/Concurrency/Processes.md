# Definition
**Program**: a file containing code. Stateless and dead. 
**Process**: a running instance of a program. 
	The same program can be running in multiple instances. Stateful and alive

Program der kører med egen ”address space”
More [[threads]] can exist in the same process. Therefore they share recourses.
## Traditional model of a process

A process consists of three parts: 
1. A [[Virtual memory|virtual memory space]]. 
	1. Contains stack
	2. code
	3. [[heap]]
	4. data, etc. 
2. A [[Kernel|kernel]] context. 
	1. PID (Page ID)
	2. open files
	3. *signal mask*
	4. list of children, etc. 
3. An execution context.
	1. [[Registers]] (including special ones like the program counter). 

When processes are running [[Concurrency|concurrently]] on the same CPU, these are the things that are swapped out.

### Termination


1. **Orphaned Processes**: If a parent process terminates while its child processes are still running, those child processes become orphaned. Orphaned processes are adopted by the `init` system process (or a similar process, depending on the operating system). This way, they can continue running independently. 
2. **Zombie Processes**: If a process (parent) terminates and its child process is still running, the exit status of the child cannot be retrieved until the child process also terminates. The child remains in a "zombie" state until the parent process calls `wait()` or `waitpid()` to read its exit status.
3. **Explicit Termination**: If the parent process wants to ensure that all its child processes are terminated, it can explicitly kill them using functions like `kill()` or by handling specific signals.
4. **Signal Behaviour**: If a parent process receives a termination signal (like `SIGKILL`), the kernel won't automatically send a termination signal to any child processes, leaving their status unchanged.
## Multi-threaded process model

A process consists of three parts: 
1. A virtual memory space.
	1. Contains stack, 
	2. code, 
	3. [[heap]], 
	4. data, etc. 
2. A kernel context.
	1. PID, 
	2. open files, 
	3. signal mask, 
	4. parent PID, 
	5. list of children, etc. 
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
	But switching between threads within a process does not require switching to a new virtual **address space**.
# Definition

**System calls**: 
a request by a process, that the kernel carries out some operation on its behalf.

Why system calls?: processes does not have direct access to hardware and system memory. 
System calls are **slow** as CPU switches to kernel space, kernel executes the request, then return to user space. But **safe** as only the kernel has access to hardware

Only the [[kernel]] has direct access to hardware and system [[Memory hierarchy|memory]].
Whenever we want to do IO (input / output) we have to perform a system call.

> Definition
> A request by a [[Processes|process]] that the kernel carries out some operation on its behalf.
> Much like a function call, but implemented very differently. 

These system calls are both very basic, but also 'higher level' than assembly calls (instructions).
Recall that most input/output really is just file manipulation.
**Many of these OS calls are really just shortcuts to reading or writing to certain files**

>System calls are low level interactions for dealing directly with the hardware. They provide security and robustness to their operations so have a certain amount of overhead that is not needed for user functions. This overhead is very much a feature and not a bug as it enables a lot more isolated user programming where we do not need to worry about what other processes might be running, or what other users are currently operating. There are also some very quick system calls, though often times these have been replaced by slower, more robust implantations.
## Technicalities

The `ecall` (environment call) instruction transfers control to the kernel. 
	- Kernel then inspects [[registers]] (mostly a0-a7) to see what it has been asked to do. 
	- Specific interpretation varies between [[operating systems]]. 
	- System call identified by a number. 

### Example

![[Pasted image 20260119180205.png]]
![[Pasted image 20260119180303.png]]

## System calls in C

C exposes system calls as functions.
- Internally use `ecall` instruction or architecture-specifc equivalent.
Not observably distinct from other C functions, except typically more primitive and tedious to use

![[Pasted image 20260120102725.png]]

## Examples
### a) `fopen()`

**No (not a syscall itself).**
- `fopen()` is a **C standard library (glibc) function**.
- It manages buffered I/O and `FILE *` structures in user space.
- Internally, it **usually calls the `open()` syscall** to actually open the file.
- But `fopen()` itself runs entirely in user space.

✅ _Uses syscalls internally, but is not a syscall._

---

### b) `fwrite()`

**No (not a syscall).**

- `fwrite()` writes to a `FILE *` stream with **user-space buffering**.
- Data may stay in memory until the buffer fills or is flushed.
- When flushing is needed, it typically calls the **`write()` syscall**.

✅ _Buffered library function; may trigger a syscall later._

---

### c) `fread()`

**No (not a syscall).**

- Like `fwrite()`, this is a **buffered stdio function**.
    
- It may read from an internal buffer without entering the kernel.
    
- When the buffer is empty, it typically calls the **`read()` syscall**.
    

✅ _Library function, not a syscall._

---

### d) `fork()`

**Yes (this _is_ a syscall).**

- `fork()` creates a new process.
    
- Creating processes requires **kernel involvement** (process table, memory mappings, copy-on-write).
    
- Even though you call it via libc, it directly invokes the **`fork` (or `clone`) syscall**.
    

✅ _True system call._

---

### e) `read()`

**Yes (this _is_ a syscall).**

- `read()` directly asks the kernel to read data from a file descriptor.
    
- Requires kernel access because file descriptors and I/O are kernel-managed.
    

✅ _True system call._

---

### f) `malloc()`

**No (not a syscall).**

- `malloc()` is a **memory allocator in user space**.
    
- It manages a heap using bookkeeping structures.
    
- When it needs more memory, it may call **`brk()` or `mmap()` syscalls**.
    
- Many `malloc()` calls require **no syscall at all**.
    

✅ _Pure library function, may use syscalls internally._

---

## Summary Table

|Function|Is it a syscall?|Why|
|---|---|---|
|`fopen()`|❌ No|stdio wrapper; uses `open()` internally|
|`fwrite()`|❌ No|buffered user-space I/O|
|`fread()`|❌ No|buffered user-space I/O|
|`fork()`|✅ Yes|process creation requires kernel|
|`read()`|✅ Yes|kernel-managed file I/O|
|`malloc()`|❌ No|user-space allocator; may call `brk`/`mmap`|

---
### Key idea to remember
> **Syscalls cross the user–kernel boundary.  
> Library functions may _wrap_ syscalls, but are not syscalls themselves.**
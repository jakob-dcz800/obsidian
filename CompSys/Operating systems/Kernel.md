The kernel is interfacing between programs and [[Hardware terms|hardware]] which limits the amount of jobs it has to do. **System calls are typically slow** as they involve a switch to [[#Kernel space|kernel space]], so are best avoided if possible

Always resident in memory

> In this course, when we say [[Operating systems|operating system]] we really mean the kernel
> The kernel uses the same CPU, [[Memory hierarchy|memory]], and other hardware as ordinary code.

When running [[Processes|process code]], the CPU is in unprivileged state, and many operations are restricted (e.g. access to hardware devices).
When an interrupt happens, the CPU switches to privileged state and jumps to kernel code, which handles it and then resumes the previously running process.
Interrupts can be outside events (keyboard press, network trac) or special instructions (invalid memory accesses, system calls). 

## Responsibilities

Key responsibilities: 
- **Process Management**: creating, scheduling and terminating [[processes]] 
- **Memory Management**: allocating RAM, handling [[virtual memory]] 
- **Device Management**: controlling I/O devices through drivers 
- **[[System Calls]]**: providing a safe interface for application to request OS services
## Example
### Question 2.1.2 (23/24)
Consider the following function, which copies from one file to another (via file descriptors):
```c
void copy(int from, int to) {
	unsigned char c;
	while(read(from, &c, 1) != 0) {
		write(to, &c, 1);
	}
}
```

_This program will certainly uses the minimum amount of memory, only 2 file descriptors and a byte for the data. This is efficient in terms of memory usage, but how might this be an inefficient solution, and how might it be improved, assuming we have more memory available?_

>This program is **inefficient**, because it performs two **system calls** per byte being copied. A better way of copying is to **use buffering**, such that we read a large block of bytes per system call (say, 4KiB, but the optimal amount is situation-dependent), and also write that entire block at once. 
>
>This is most easily done by using the standard IO facilities and fwrite()/fread(). This is an example of a time/spacetradeoff, because the buffer will take up memory—hence, it should be large enough to amortise the system calls, but no larger.

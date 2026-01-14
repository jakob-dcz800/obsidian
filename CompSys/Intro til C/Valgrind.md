- Runs your program and tracks all memory allocations/frees.
- Reports **leaks** (memory you allocated but never freed) and **invalid memory access** (read/write outside allocated space).

**summary explained:**
`definitely lost: 0 bytes in 0 blocks`
👉 Memory that you lost all pointers to (a real leak).

`indirectly lost: 0 bytes in 0 blocks`
👉 Memory that can only be reached through leaked memory (like malloc’d members of a leaked struct).

`possibly lost: 0 bytes in 0 blocks`
👉 Memory that Valgrind _thinks_ may be leaked because it’s only pointed to by things like registers or interior pointers.

`still reachable: 11,700,740 bytes in 20,004 blocks`
👉 Memory that was allocated and never freed, **but you still have a pointer to it when the program exits**.  
This is not a strict leak — it’s just memory you didn’t free before exit.  
E.g. global caches, static buffers, or memory you didn’t bother to free because the OS reclaims it at process exit.

`suppressed: 0 bytes in 0 blocks`
👉 Memory Valgrind didn’t report because of suppression rules (e.g. known harmless leaks in system libs).
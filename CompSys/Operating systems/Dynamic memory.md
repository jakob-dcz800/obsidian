
## malloc

[[Memory and registers|Memory]] allocation
Reserve memory until freed
Works in runtime

- Not a system call itself like `mmap`
- Requests memory from [[System calls]] ([[kernel]]) like `mmap` and `sbrk` and then parcels it out
- [[Fragementations#Internal fragmentation|Internal fragmentation]] is when allocated blocks have wasted space
- [[Fragementations#External fragmentation|External fragmentation]] is when free space is split into many small blocks


> Allocates a block of memory of a given size. Accessing uninitialised memory is undefned behaviour (E.g. don't do it)

- Allocating memory means you claim it, no one else can use it. 
- Eventually the OS will step in and clear it up for you, but depending on that is seen as VERY BAD practice. 
- Submitting code that does this is seen as something to be penalised.
- Valgrind detects these sorts of errors
## calloc

Exactly the same as malloc, except that the memory is initialised the zero
Slower than malloc!

> writing new values is slow, better to just allocate and take the values that are there. Calloc is a handy shortcut to initalise all data to zero but shouldn’t be used if you’re just going to overwrite it with other values. This means the onus is on your to initialise any memory as necessary. free also doesn’t change values meaning that anything written is still technically on disk. this means that other processes could potentially still read that data, though it is very much non trivial to do so in a usable format. This is why when you really need to delete things such as bank details, you should do more than just delete files as that just unallocates but should instead overwrite them with blank data.
## realloc

Takes an already allocated block of memory and resizes it. No new initialisation takes place (both a blessing and a curse)

> Note that use of realloc is often discouraged unless managed correctly, but its worth mentioning here as you will see it online. 

- int `*ptr = malloc(12);`
- If this fails then no memory is allocated. The pointer returned by malloc will be NULL, so we can detect this, but don't need to free anything. 
- But now consider if the above was followed by: 
- `ptr = realloc(ptr, 16);` 
- If this fails then no memory is allocated and the pointer is again returned as [[Pointers#Null pointer|NULL]]. But now we've lost the pointer to that first malloc, and that still needs free'd. 

## free

- Always always always, free any allocated memory use the `free(ptr)` command to free allocated memory, as pointed to by the given pointer 
- You can test your program using valgrind

### How does free know the size of the block given just a pointer?
Standard method:
Store the length of the block in a preceding byte. This is also called the header field.
We could even store more metadata if we wanted to.

This requires an extra word for each allocation. 
The pointer points towards the first word and not the header.

![[Pasted image 20251004122919.png]]

### How do we keep track of free blocks?
keep a list

## Example

```c
#include <stdlib.h>
#include <stdio.h>

int main(void) {
  int size = 10;
  int *arr = malloc(size * sizeof(int));
  
  printf("&arr: %p\n", (void*)&arr);
  printf("arr:  %p\n", (void*)arr);
  
  for (int i = 0; i < size; i++) {
    arr[i] = i*2;
    printf("&arr[%d]: %p ", i, (void*)&arr[i]);
    printf("arr[%d]: %d\n", i, arr[i]);
  }

  free(arr);
}
```

## mmap

`mmap()` is a syscall that allows processes to map to [[Virtual memory|virtual memory]]
- Can map files to memory or map anonymous files
- Can share memory between processes

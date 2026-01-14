[[Processes]] are an example of concurrent execution.
	Generally just work because they are isolated from each other. 
	Interleaved execution often not noticeable. 
	Process isolation makes close collaboration inefficient and awkward. 
	
Instead we use threads. 

## Threads in the same process

Each thread has its own logical control flow. 
Each thread has its own stack. 
Threads share open files. 
Threads share the same [[Virtual memory|virtual memory space]]. 
	Therefore they are faster to swap out than swapping out processes
	It takes twice as many clock cycles to swap a process
They are peers, there is no "main thread".

> Implication:
> Threads can interact by modifying memory. 
> Even unintentionally. 

Each process has one or more threads. 
Each thread belongs to exactly one process

## Threads in C

Library is called POSIX threads (pthreads).
![[Pasted image 20251008113614.png]]

```C
#include <pthread.h> 
#include <assert.h> 
#include <stdio.h> 

void* thread(void *arg) { 
	int* p = arg; 
	printf("Hello world! %d\n", *p); 
	return NULL; 
} 

// main is executed on a thread (not the one we're creating)
int main(void) { 
	int x = 42; 
	pthread_t tid; 
	
	assert(pthread_create(&tid, NULL, thread, &x) == 0);
	// wait until thread has returned NULL
	// we must wait, since main will end if wait is not given
	assert(pthread_join(tid, NULL) == 0); 
} 
```

## Sharing

```C
// create pointer to pointer
char **ptr; 
int cnt = 0; 

void* thread(void *vargp) { 
	int j = (int)vargp; 
	printf("%d: %s (cnt=%d)\n", j, ptr[j], ++cnt); 
	return NULL; 
}

int main() { 
	pthread_t tid; 
	char *msgs[2] = { 
		"Hello from foo", 
		"Hello from bar" 
	}; 
	// assign ptr to msgs (now a global variable)
	ptr = msgs; 
	
	// create two threads
	for (int i = 0; i < 2; i++) {
		pthread_create(&tid, 
						NULL, 
						thread, 
						(void *)i); 
	}
	// waiting for created threads by closing the initial 'main' thread
	pthread_exit(NULL); 
}
```
Outcome depends on arbitrary scheduling decisions elsewhere.
If two people book the same seat on an airplane at the exact same time - who gets the ticket?

This example will mess up counts for large arguments because of concurrency

```C
#include <pthread.h> 
#include <stdio.h> 
#include <stdlib.h> 

int cnt = 0; 

void *thread(void *vargp) { 
	int n = *((int*)vargp); 
	for (int i = 0; i < n; i++) 
	cnt++; 
	return NULL; 
}

int main(int argc, char **argv) {
	int n = atoi(argv[1]); 
	pthread_t tid1, tid2; 
	
	pthread_create(&tid1, NULL, thread, &n); 
	pthread_create(&tid2, NULL, thread, &n); 
	pthread_join(tid1, NULL); 
	pthread_join(tid2, NULL); 
	
	if (cnt != 2 * n) 
		printf("Bad: %d\n", cnt); 
	else 
		printf("Good: %d\n", cnt);
}
```

## Mutexes

> Mutual exclusion

This is to protect **shared variables** between threads

Mutexes have two states:
- Locked
- Unlocked
They start *unlocked*
Ensures that critical sections do not overlap.

![[Pasted image 20251008125631.png]]

We associate each critical section with a mutex. 
When entering the critical section: lock the mutex. 
When leaving the critical section: unlock the mutex.

C doesn't have a language-level notion of "critical section", and typically it isn't code that we need to protect.
In practice we associate mutexes with shared variables. Sometimes a single mutex protects multiple variables

### Example

#### Protecting the critical section in the counting program

```C
pthread_mutex_t cnt_mutex = PTHREAD_MUTEX_INITIALIZER; 
int cnt = 0; 

for (int i = 0; i < n; i++) { 
	pthread_mutex_lock(&cnt_mutex); 
	cnt++; 
	pthread_mutex_unlock(&cnt_mutex); 
}
```

#### Gotta go fast

```C
int local_cnt = 0; 

for (int i = 0; i < n; i++) { 
	local_cnt++; 
} 

pthread_mutex_lock(&cnt_mutex); 
global_cnt += local_cnt; 
pthread_mutex_unlock(&cnt_mutex);
```

### How mutexes are implemented
Real mutexes contain more features, but this captures the essence:

```C

```
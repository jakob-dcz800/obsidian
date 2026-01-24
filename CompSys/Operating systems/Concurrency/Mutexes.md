
# Mutexes

> Mutual exclusion

This is to protect **shared variables** between [[threads]]

Mutexes have two states:
- Locked
- Unlocked
They start *unlocked*
Ensures that critical sections do not overlap.

![[Pasted image 20251008125631.png]]

We associate each critical section with a [[Mutexes|mutex]]. 
When entering the critical section: lock the mutex. 
When leaving the critical section: unlock the mutex.

C doesn't have a language-level notion of "critical section", and typically it isn't code that we need to protect.
In practice we associate [[mutexes]] with shared variables. 
Sometimes a single mutex protects multiple variables

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
Concurrency has two goals: modularity and parallel execution ([[Running times|performance]]).
	The latter is increasingly important. 
Concurrency causes nondeterministic execution. 
	Hard to reason about. 
	The machine is certain to betray you. 
Use [[Races#Mutexes|mutexes]] to ensure mutual exclusion to variables or critical sections. 
	Ultimately based on tiny operations that the hardware guarantees are atomic.

Concurrency vs parallelism

%% Use these terms correct %%

**Concurrency** is multiple programs executing at the same time.
Two or more logical flows of events that may happen in any order, and even be interleaved.
This is partly done by the CPU doing a bit of processing on one program and then switching to the next.

**Parallelism**
Two or more logical flows of events happening or existing at **literally** the same time.
As in, on two parallel processors. This of course depends on hardware - how many cores are available.

For parallel proceses, there must be some shared state.
They're using the same memory and variables.
This can cause issues since **concurrent** processes can interleave and the order of operations is not predetermined.

![[Pasted image 20251008105555.png]]

## Problems

> This is a field that has more terms for how things can go wrong than go right.

By far the most difficult form of programming I know of. 
Our own brain is poorly suited for this kind of thinking.
	We shall see C is not much better. 
Many aspects are outside the scope of CompSys.

[[Starvation]]
[[Deadlock]]
[[Races]]

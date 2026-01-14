*Fundamental idea:*
"The smaller and faster device at level *k* acts as a cache for the larger slower device at level *k + 1*"

*Why do they work?* 
Because of locality, most accesses tend to be towards the top of the hierarchy.



![[Pasted image 20260108111706.png]]

Each of the 8 cores have their own L1 and L2 caches, but L3 cache is shared.
## Cache
There are multiple types of [[cache]]
- L1, L2 are [[Hardware terms#CPU|CPU]] level
- L3 Cache is chip-level and often shared across cores
- Lower levels of cache (present in [[Hardware terms#DRAM|RAM]])
- Whatever exists in a high level also exists in all the lower levels (existance cascades downwards)


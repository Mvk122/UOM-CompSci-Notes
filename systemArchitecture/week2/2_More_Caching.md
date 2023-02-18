# More Caching

## Set Associative Cache
* Each item can be cached in one of N places. N being 2, 4, 8 etc.
	* The set from one of N for an address is determined through the index bits of the address to be cached.
	* The memory is placed in one of the cache lines of the set with its corresponding tag.
	* Searching thus only needs to be done on the specifc set for a given memory address.
* It increases performance by reducing conflicts and the amount of tags that need to be probed to find an element.
* However it comes at an increased chip cost and decreases the hit speed over a direct mapping due to the additional calculation that needs to be done to determine which set to search as well as time spent probing through the set.

## Cache Lines
* Takes advantage of spacial locality by storing consecutive words with a single tag.
* Reduces the tag overhead with a small loss in performance as multiple operations are required to check if a tag contains a certain address .

## Cache Architecture Decisions
* `Cache Size`: Based on the amount of space available and the amount of resources that are available to be invested into the cache.
* `Cache Line Size`: Depends on the type of data that is being cached. Some data types like `TLB` have less data locality hence a larger cache line size leads to performance degradation with less benefit.
* `Power`: The more associative the cache, the higher the power usage as the cache is larger and more probing needs to be done.
* `Multiple Levels`: Caching with multiple levels to store more data and create more layers between the cache and the memory. 
	* Often each processor core has 2 L1 caches, one for data and one for instructions.
	* Both instructions and data are cached on the processor's L2 cache.
	* The L3 cache is shared between all processor cores.

## Cache Replacement Policy
* The strategy chosen to remove an item from a cache when creating space to add another item to the cache.
* `Round Robin`: A First In First Out policy where the oldest block in the set is removed. Easy to implement.
* `Least Recently Used`: Removes the item that hasn't been used in the longest. It is hard to implement it in a performant way in hardware however it provides good results.
* `Random`: Removes a random element, it is easy to implement but less effective than LRU.

## Cache Writes

### Modifying Cache Entry and Memory Copy
* It is slow as writing to the memory is much slower than writing to the cache.
* Uses more power as signals need to be sent down the cache hierarchy.
* It is simpler than only modifying the cache as cache eviction thus becomes simpler.
* It can be sped up by sending a signal to modify the memory without waiting for a response. Thus it occurs in the background.
	* This strategy won't work if cache writes are very common as it could create a backlog of writes.
	* However, in general there are more reads than writes.
* Less common in modern chips than modifying the cache entry only.

### Modifying Cache Entry Only (Write Back Cache)
* Writes only to the cache without writing to memory.
* Much faster as intermediary writes before cache eviction are not propogated to the memory.
* Time penalty when the cache is evicted or a context switch occurs.
* Can use the concept of  the cache being `dirty` to signal that the cache has been modified since retrieving it from the memory to decide if the cached item needs to be written back to memory on eviction. This strategy saves time at the cost of additional memory.

## Write Misses
* When memory needs to be written to however the memory address in question is not stored in the cache. There are 2 strategies to deal with this.
* `Write Through`: Just write straight to the memory.
* `Load the Cache`: Load the cache line with the value and other corresponding memory and proceed with the `write back cache` strategy.
* The cache loading strategy is often faster because spatial locality suggests that the line ought to be cached as the memory location and nearby memory locations might also be read soon.
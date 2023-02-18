# Caches
* Used to speed up a spatially small subset of accesses with the assumption that this subset is used significantly more than other accesses.
* The assumption is required as "cache misses", which is when the processor tries accessing memory that isn't in the cache are slower than if there was no cache in the first place as the cache is checked and the memory is accessed after, using 2 operations as opposed to just 1 memory access if the cache wasn't used.
* Makes the best use out of the fact that big memories are usually slow (SRAM) and little memories are usually fast (SDRAM).

## Calculating Cache Performance
$$T_{average} = T_{hit} + (P_{miss} \times T_{miss})$$
* Most computers have $P_{miss}$ at lower than 10%.

## Cache Locality
* Caches work due to code statistically having data locality.
* `Spacial locality`: If some data was used, the data around it will also likely be used.
* `Temporal locality`: If data was used once, it will likely be used again.

## Cache Operation Specifics
* Caches store 2 main data fields:
	* The tags that store which locations are cached.
	* The data which represents what is cached for those specific locations.

## Cache Associativity
* A `fully associative` cache can store 'N' different items with N available entries without restriction.
* This is expensive however, as $O(N)$ operations will be required each time to check if a tag exists in the cache.
* Reducing the associativity by restricting the locations in the cache that specific addresses can be located helps to speed up the runtime of the cache.

### Direct-Mapped Cache
* Solves the speed issues of `fully associative` caches by requiring that any particular item has a predetermined place it might be cached in.
* The location is determined by the address's lower address bits hence only 1 tag comparison is needed per memory access.
* This also allows for data to be looked up speculatively, looking it up in both the memory and the cache in parallel which is faster in the cases that the cache misses.

## Types of Cache Misses
* `Compulsory misses`: Data was not previously used hence is not in the cache.
* `Capacity Misses`: The cache is full and more space is needed so a memory location needs to be evicted.
* `Conflict Misses`: Cache architecture limits tag flexibility. This can't occur in fully associative caches.
## Cache Prefetch
* Some memory access patterns are predictable, eg matrix column accesses.
* It can be done by simulating a `cache miss` without actually wanting the data, thus adding the data to the cache.
* It can be initiated either through software, which takes up bandwith on the instruction cache.
* Or by smart hardware that makes the predictions.

## Cache Location
* Cache entries are tagged by their address, this can either be `virtual` or `physical`.

### Virtual Address Caching
* Faster as it does not have to wait for address translation.
* Can be expensive as it is invalidated on process context switching.
* Used on L1 Caches.

### Physical Address Caching
* Longer access latency due to address translation. 
* Less expensive as it can persist over context switches.
* Used for everything below L1.
# Data Coherence and Consistency
* Data coherence is an important aspect of multi-core systems as `threads` typically share the same memory. This leads to problems such as: 
### Memory Coherency
*  Ensuring that changes are seen everywhere. 
* If multiple cores have different L1 caches storing copies of the same data, a modification of the data in 1 cache needs to be propagated to the other caches.
* The above can become very expensive as updates need to be propagated to many places.
### Memory Consistency
* Ensuring the correct ordering of memory accesses to prevent issues like `write-after-write` or `read-after-write` data hazards.
* Memory is consistent if: 
	* A read operation returns the same value from all copies.
	* A write operation updates all copies before any other operation takes place.

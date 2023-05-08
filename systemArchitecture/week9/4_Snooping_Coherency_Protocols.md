# Snooping Coherency Protocols
#snoopingCoherencyProtocol
## Snooping Protocols
* All caches snoop for activity concerned with its cached addresses.
* All caches are aware of all events.
* Requires a `broadcast` communications structure, typically a `bus` or a `network-on-chip`.
* This can be done by either using:
	* `Write Update`: The address and new data is broadcasted, so all caches update their value with the new value.
	* `Write Invalidate`: Only the address is broadcasted to tell other caches to invalidate their copy of the data, any shared reads in other cores will now miss and get the value from the updated shared cache. The shared cache is updated on each write.
* In both protocols, only 1 core can use the bus at any one time.
## Update vs Invalidate
* Invalidate is better in general.
* Messages are shorted in invalidate as the data does not need to be sent with the address.
* Only 1 message needs to be sent if there are multiple writes to the same word or same cache line. As spatial and temporal locality dictate that there would be many writes on the same location, this savings is significant.
* This savings is useful as bus bandwidth is a precious commodity.
* However, invalidate can be slower as it requires a #writeThrough  to the memory on each write. This can however be changed to #copyBack with the use of the `MESI Protocol`.

## MESI Protocol
* In both instances of snooping protocols, we can prevent sending messages if we know a cached value is not shared.
* Furthermore, we can prevent going to main memory or using #writeThrough by using the `MESI Protocol`.
* This can lead to:
	* Better latency.
	* Lower bandwidth consumption.
	* Less contention for use of the bus.
* It is done by assigning a value to each cache line and making state transitions/ bus actions in response to memory actions or bus actions sent by other caches.
* The values are:
	* `Modified`: This cache line has been modified and is different from the main memory.
	* `Exclusive`: The cache line is coherent with main memory and is the only cached copy.
	* `Shared`: Coherent with main memory but copies may exist in other caches.
	* `Invalid`: cache data is invalid.

## MESI Local State Transitions
![[Pasted image 20230508181103.png]]
### Invalid State Transitions
* `Read Miss`: Do a memory read and request if other caches have the value. If they don't, then transition to `Exclusive`, if they do, cancel the memory read and transfer to `Shared`.
* `Write Miss`: Do a memory read and request if other caches have the value. Send a `Read With Intent To Modify` on the bus. If the cache value exists in other caches, snooping cores set their tags to `Invalid`. Local copy is always set to `Modified`. 
* `Read Hit`: Not possible
* `Write Hit`: Not possible
### Modified State Transitions
* Always do nothing
### Shared State Transitions
* `Write Hit`: Send an `Ivalidate` on the bus, other caches with the value are set to `Invalidate` and local is set to `Modified`.
* `Read Hit`: Do nothing
* `Read Miss` and `Write Miss` are not possible
### Exclusive State Transitions
* `Read Hit`: Do nothing
* `Write Hit`: Change to modified
* `Read Miss` and `Write Miss` are not possible.

## MESI Snooping Cache Transactions
![[Pasted image 20230508181057.png]]
### Invalid State Transitions
* None
### Modified State Transitions
* `Read With Intent To Modify`: Set to `Invalid`.
* `Memory Read`: Set to Shared
### Shared State Transitions
* `Read With Intent to Modify`: Set to `Invalid`.
* `Invalidate`: Set to `Invalid`.
* `Memory Read`: Do nothing
### Exclusive
* `Memory Read`: Set to `Shared`. 
* `Invalidate`: Set to `Invalid`.
* `Read with Intent to Modify`: Set to `Invalid`.

## MOESI Protocol
* A modification of the `MESI Protocol` with the addition of `Owned` state wherein the cache line has been modified and is different from the main memory while there can be cached copies in the `Shared` state.
* This is used to avoid the need of copying back to main memory on a write update.


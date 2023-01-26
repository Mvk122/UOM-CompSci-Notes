# Hash Maps and Hash Tables

* Hash Maps can be used to efficiently store and look up elements for use in a set or a dictionary.
* They use a hashing function to find an index to place elements.
* They have a $O(n)$ space complexity.
* On average $O(1)$ time complexity for all operations.
* Worst case $O(n)$ time complexity for all operations.

## Separate Chaining
* Make an array of elements that can contain the data as well as space for another memory address.
* To `insert` a value, run it through the hashing function to find where to place it.
* If the memory location is empty, add the element to that memory address.
* If it is not empty, go down the linked list at that address and at the end, point the last element's next pointer to the current element to be inserted, thus extending the linked list.
* To `find`, do the hashing function and iterate through the linked list to find the element.

## Hash Functions
* Hash functions need to exist due to the `pigeonhole principle` wherein there are fewer buckets than items hence at least one bucket has to have more than 1 item.
* It is desireable that hashing functions uniformly maps each key to an integer in the range [0,N).
* Hash tables should ideally be `prime sized` to prevent clustering. 
* Hashing functions should ideally avoid symmetry.
* Bad hash functions lead to clustering which reduces the efficiency of hash tables.

### Polynomial based hash code
* Can be used to avoid symmetry.
* For some sequence a<sub>0</sub>, a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub> and some constant c,
* hash using a<sub>0</sub>c<sup>n-1</sup> + a<sub>1</sub>c<sup>n-2</sup> + a<sub>2</sub>c<sup>n-3</sup>
* The value of c is ideally prime, java uses 31.

## Open Addressing
* A separate method of implementing hash tables using `rehashing`.
* To `insert` a value, run it through the hashing function to find where to place it.
* If it is occupied, `probe` using the rehash function to find another place to put the item.
* Continue probing and rehashing until a place is found. A place is either an empty slot or a slot that has been marked as `deleted`.
* To `delete` an item mark the location of the item as `deleted`.
* To find, run the hashing function. If the location yields empty, then the item does not exist. However if it is `deleted` or `occupied`, probe using rehashing until it is found or an empty location is found.
* `deleted` and `empty` need to be separate concepts as open addressing places the item in the closest empty spot. If the spot is taken, the item must be placed elsewhere. Hence by maintaining the record of deletion, the find algorithm knows to continue looking because a spot could have been occupied during the insert, leading to the element not being in the closest spot.

### Rehashing Types
* `Linear Probing`: `(hash(k)+i) % N for i = 0 -> N`
* `Quadratic Probing`: `(hash(k)+i^2) % N for i = 0 -> N`
* `Double Hashing`: `(hash(k)+ (i* hash2(k))) % N for i = 0 -> N`


## Rehashing
* `The Load Factor` refers to how well utilized the hash map is.
* `Rehashing` refers to creating a new table that is a fixed percentage larger, reinserting all existing elements. It is done when the load factor reaches a particular level.
* For `open addressing`, the ideal load factor to rehash is between $0.5$ and $0.75$.

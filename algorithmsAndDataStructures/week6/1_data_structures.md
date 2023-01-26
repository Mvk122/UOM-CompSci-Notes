# Data Structures and Data Types

## Data Structures vs Data Types
* A data structure is a way to store and organize data to facilitate access and modifications.
* Data structures implement `data types` which are a theoretical concept that defines:
    * The possible values it can take
    * The operations that can be performed
    * The behaviors of these operations
* Eg linked lists are a data structure that implements the list data type.

## Dynamic Array
* Space is allocated for memory.
* When the space is full, a new larger array is allocated and the old data is moved to the new array.
* Arbitrary access is done in $O(1)$.
* Dynamic arrays have $O(N)$ wasted space plus the expensive copy operation when the list is full

## Linked Lists
* Nodes contain the memory being stored as well as a pointer to the next node.
* Arbitrary access is done in $O(N)$
* Memory scales with $O(N)$ but there is no wasted space or expensive copy.

## Queue vs Stack
* `Queue`: First in First Out
* `Stack`: First in Last Out
* Either can be implemented with either dynamic arrays or linked lists.

## Sets and Dictionaries
* `Set`: An unordered collection of unique elements
* `Dictionaries`: Key value pairs

## Priority Queues and Disjoint Sets
* `Priority queue`: Queue that is ordered by priority
* `Disjoint set`: Collection of disjoint sets that can be merged
# Trees

## Definitions
* `Trees`:  A data structure with nodes that are connected to other nodes.
* `Parents and Children`: Parents point to children.
* `Leaf nodes`: Nodes with no children
* `Internal nodes`: Nodes with both parents and children

## Array Representation of Trees
* A bad way to implement Binary Trees.
* The child nodes of a parent stored in `i` are stored in `2i + 1` and `2i +2`.
* Wastes a lot of storage space for trees that are very tall but not wide. Can waste $2^N$ space.

## Linked Representation of Trees
* A better way to implement trees.
* Each parent has pointers to their respective children and parent. This has no wasted space.
* For trees that have arbitrary numbers of children, each node has a pointer to its parent as well as a pointer that points to a container that contains the pointers to the children.

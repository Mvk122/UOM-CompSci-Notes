# Binary Heaps

* Binary Trees that are `complete` and have one of the heap order properties:
    * `Min heap`: Each node's value is greater than that of its parents.
    * `Max heap`: Each node's value is less than that of its parents.
* `Space Complexity`: $O(n)$
* `Height`: $O(log(n))$
* `Building`: $O(N)$ As at each level, there isn't additional traversal.

## Implementing Binary Heaps in Arrays
* Since they are complete, they can be implemented using arrays without wasting space.
* The children of a parent are stored at `2i + 1` and `2i + 2`.
* The end of the array can be used to store other variables.

## Maintaining a Max Heap
* This algorithm can be used to ensure that the max heap order property has not been violated and to fix it.
* Assume that the left and right children are roots of valid max heaps.
* At the root node, consider its children and swap the root with the largest of its children if it is larger than the root.
* For the node that was swapped, recurse onto it thus making the node's position the parent and running the algorithm on it and its children.

```python
def maxHeapify(H, i):
    largest = i
    l = H.left(i)
    r = H.right(i)

    if L < H.HeapSize and H[l] > H[largest]:
        largest = l

    if L < H.HeapSize and H[l] > H[largest]:
        largest = r

    if largest != i:
        H[i], h[largest] = h[largest], h[i]
        maxHeapify(H, largest)
```

## Converting an Array into a Max Heap
* Can be done using a "bubbling up and down" method. 
* Starting at the bottom, run the `maxHeapify` algorithm throughout the breadth of the tree.
* Move upwards and run the algorithm again. (bubbling up)
* If there is a change, run the algorithm on the position of the node that was changed. (bubbling down)
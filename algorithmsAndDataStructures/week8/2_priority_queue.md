# Priority Queue

* A queue that has some priority associated with the element.
* The element with the `highest` priority is exited first.

## Implementing using a Max Binary Heap
* The highest priority element is always the root.

## Removal from a Max Binary Heap
* Remove the root.
* Replace it with the last value in the max binary heap.
* Run the `maxHeapify` algorithm from the root of the tree downwards.

## Insertion into a Max Binary Heap
* Insert it at the next available insertion point.
* Compare it to its parent. If it is larger then swap it. 
* Continue to do the comparisons and swaps with parents until the comparison yields false and there is no swap.
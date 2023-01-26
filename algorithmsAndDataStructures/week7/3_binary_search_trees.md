# Binary Search Trees

* An In Order traversal of a BST gives the elements in ascending order.
* `Searching`: Go left if the current node is smaller than what is being searched for, right if larger.
* `Insertion`: The same pattern however, elements are only stored at leaf nodes.
* `Removal`: 
    * if the element is a leaf node, just remove it. 
    * If it has a single child, elevate the child to its parent's parent.
    * If the next highest element to it (its in order traversal) is a leaf node, replace it with that node.
    * Otherwise, replace it with its in order successor and place the successor's child in the place of the in order successor.

## BST Time Complexity
* The Average case applies when the BST is a `Balanced BST`.
* On average, all operations are of time $Olog(n)$
* Worst case, all operations are of time $O(H)$ where H is the height of the tree.
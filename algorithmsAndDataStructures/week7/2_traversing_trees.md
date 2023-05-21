# Traversing a Tree

* Pre and post refers to when the current node is visited in relation to the left and right sub trees.

## Pre Order Traversal
* Essentially visiting self, then the left subtree then the right subtree. 
```python
def pre_order(T, v):
    visit(v)
    if T.isInternal(v):
        pre_order(T, T.leftChild(v))
        pre_order(T, T.rightChild(v))
```

## In Order traversal
* Exploring the entirety of the left subtree, then the node and then the right subtree
```python
def in_order(T, v):
    if T.isInternal(v): 
        in_order(T, T.leftChild(v))
    visit(v)
    if T.isInternal(v): 
        in_order(T, T.rightChild(v))
```

## Post Order Traversal
#postOrderTraversal
* Exploring the left, then right then itself.
```python
def post_order(T, v):
    if T.isInternal(v):
        post_order(T, T.leftChild(v))
        post_order(T, T.rightChild(v))
    visit(v)
```

## Depth First Search and Breadth First Search
* Uses a stack to search through a tree. 
* Breadth first search uses the same implementation except it uses a queue.
* Depth first search can also be done using recursion instead of a stack.
```python
    def dfs(T, v):
        s.push(v)
        while len(s) > 0:
            v = s.pop()
            if not visited(v):
                s.push(T.rightChild(v))
                s.push(T.leftChild(v))
```
# Infinite Data

* Lists can have recursive definitions to have infinite lists as lists are strict in the head of the list but non strict in the tail.

## Fibonacci Sequence List Comprehension

```haskell
fibb = 1:1:[(fibb !! n) + (fibb !! (n + 1)) | n <- [0..]] -- !! operator gets the element at an index

main = print(take 6 fibb) -- method to get the first 6 elements of the infinite list
```
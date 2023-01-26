# Divide and Conquer Strategy

* A strategy that uses recursion to:
* `Divide` the problem into one or more smaller instances of the same problem.
* `Conquer` the sub problems by solving them recursively.
* `Combine` the sub problems to form a solution to the original problem.

## Merge Sort
* Works by breaking up an array in half.
* Continues to break these subarrays into half until the base case with 1 element.
* By definition, the array with 1 element is sorted.
* Recurses back up the tree by merging the sorted arrays layer by layer up the tree.
* Has a time complexity of `O(n log(n))` as the recursion tree has `log(n) + 1` levels and the cost of each level balances out as `constant * n`.

```python
def merge_sort(A, left, right): 
    if left < right:
        mid = math.floor((left + right)/2)
        merge_sort(A, left, mid)
        merge_sort(A, mid+1, right)
        merge(A, left, mid, right) # Uses helper merge function

# Merges 2 sorted subarrays
# considers the smallest element of each side, chooses the smaller one, copies it to the final array and moves the pointer to the next element of that array.
# Uses this 2 pointer strategy to merge the sorted arrays
def merge(A, left, mid, right):
    pass
```

## Proof by induction using substitution
* Consider that merge sort's recurrence has a relation `T(n) = 2T(floor(n/2)) + Θ(n)`.
* Make a guess that `T(n) <= c n lg(n)` for all n >= n0.
* If `n >= 2n0`, it holds for `floor(n/2)`, yielding `T(floor(n/2)) <= c floor(n/2) log(floor(n/2))`
```
T (n) ≤ 2(c ⌊n/2⌋ lg(⌊n/2⌋)) + Θ(n)
≤ 2(c(n/2) lg(n/2)) + Θ(n)
= cn lg(n/2) + Θ(n)
= cn lg n – cn lg 2 + Θ(n)
= cn lg n – cn + Θ(n)
≤ cn lg n
```
> This proof makes no sense

# Complexity Analysis

## Complexity Analysis Computational Model
* All memory is equally expensive to access.
* Instructions are executed one after another,
* All reasonable instructions take 1 unit of time and rely on the number of primitive steps taken.
* The word size is constant.

## Complexity Analysis Types
* `Worst Case`: Provides an upper bound on running time and is usually an absolute guarantee.
* `Average Case`: Provides the expected runtime given either random or real life inputs.

## Asymptotic Notation
* `O-notation`: Characterizes an upper bound of a function. Hence a function that is `O(n^2)` is also` O(n^3)` etc.
* `Ω-notation (Omega`): Characterizes a lower bound of a function. Hence a function that is `O(n^2)` is also `O(n)`.
* `Θ-notation (Theta)`: Characterizes a tight bound of a function.

## Analyzing Insertion Sort
* The left side of the array from the current considered element is already sorted.
* The current element being considered is stored in key.
* Moving left in the sorted array, if that element is larger than the key, move it to the right to make space for the key. Then decrement j to move on to the next element to consider.
* When the element being considered is larger than key, given that the left of the array is sorted, this is the only place that the key can be kept, hence insert the key and move on to the next key to consider. 
```python
def insertion_sort(A, n):
    for i in range(1, n):
        key = A[i]
        j = i - 1

        while j >= 0 and A[j] > key:
            A[j+1] = A[j]
            j = j -1
        A[j+1] = key
```

### Loop Invariants
* Insertion sort uses `loop invariants` to prove its correctness. They are statements that are:
* `Initialized`: True prior to the first iteration of the loop.
* `Maintained`: If it is true before an iteration of a loop, it remains true before the next iteration.
* `Terminated`: The invariant gives a useful property that helps show the algorithm is correct when the loop terminates.
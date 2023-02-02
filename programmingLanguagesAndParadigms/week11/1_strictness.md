# Strictness

* A function is `strict` in its argument when the function always returns an error if its argument is an error.
* A pair that contains errors can be pattern matched successfully if neither of the elements are used however a pair that is an error cannot be pattern matched on.
```haskell
-- eInt and eBool are already assumed to be errors
error_pair = (eInt, eBool) -- Can be pattern matched
ePair = error "Error message"

h :: (Int, Bool) -> Int
h (x,y) = 42 -- fails for ePair but not for error_pair

j :: (Int, Bool) -> Int
j p = 10 -- does not unpack the arguments hence works for both
```

## Creating errors in Haskell
* Errors can be created with the `error` keyword.
* They are however, bad practice and it is better practice to use the `Maybe` datatype for functions that are not defined for all inputs.
```haskell 
eInt::Int
eInt = error "Error Message"
```

## Compiler Guarantees
* If the value of an expression is an error, its theoretical value is the set of all errors which could result from evaluating in any order.
* Hence based on the specific version of Haskell/ Compiler used, a different error can be reached with the same code.
* This thus means that operations like `+` aren't commutative when considering errors.
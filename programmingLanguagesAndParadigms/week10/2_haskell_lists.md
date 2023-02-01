# Haskell Lists

* Lists can be defined by wrapping types in square brackets
```haskell
myIntHead:: [Int] -> Maybe Int
myIntHead [] = Nothing -- Empty list syntax
myIntHead (x:xs) = Just x -- the ":" is the prepend operator

main = print(myHead([1,2,3])) -- syntax for defining lists
```

## Strings
* Strings are represented as a list of characters using type `[Char]` which is the same as `String`.

## List Comprehensions
* Numerical lists can be represented using patterns such as `[1,3..10]` eg the list from 1-10 excluding 2.
* List comprehensions can be of the form:
```haskell
l = [(w, n) | w <- "Hi!", n <- [1..3], w /= 'i'] -- conditions are chained using commas

-- the above returns
[("H", 1), ("H", 2), ("H", 3), ("!", 1), ("!", 2), ("!", 3)]
```
# Haskell Definitions

```haskell
-- defining values
b = False || (False && True)

-- if statements
v = 7 * (if b then 5 else 6)

-- function I/O and calling functions
add7 n = n + 7
main = print add7(5)

-- defining functions with pattern matching
-- Order matters as if n was before 1, small of 1 would become False as the pattern applies.
small 0 = True
small 1 = True
small n = False

-- guard expressions allow for more secure pattern matching using boolean expressions.
sideOfFive n
    | d > 0 = 1
    | d < 0 = -1
    | otherwise = 0
    where d = n - 5
```

## Higher Order Functions
* Functions that either take one or more functions as arguments.
* Functions that return functions as a result.

```haskell
addConst n m = n + m

-- adds the inputs to addThree to the end of addConst
addThree = addConst 3

-- can also be defined explicitly
addThree x = addConst 3 x

v = addThree 4 -- v is 7
```

## Anonymous Functions
* Functions that don't have names.
```haskell
-- \m refers to the inputs to this anonymous function
-- The arrow shows that the body of the function is on the right
addConst n = \m -> n + m
```

## Let Statements
* Allows for explicit scoping of variables
```haskell
let variable = expresssion in expression
(let x = 2 in x*2) + 3 -- returns 7 as the value of x being 2 is subbed into the equation.
```
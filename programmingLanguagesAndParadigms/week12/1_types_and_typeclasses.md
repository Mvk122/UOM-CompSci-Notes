# Types and TypeClasses

## Parametric vs ad-hoc polymorphism
### Parametric Polymorphism
* Without the use of `type classes`, polymorphism in Haskell is `parametric` as the same function definition is used for all types.
* They are quantified using `for all` which comes before the type which is why the below definitions make no sense.

```haskell
f::a -> Bool -- parametric polymorphism
f _ = True -- same implementation for every type a

-- function definition that makes no sense
-- Makes no sense as it takes a function that takes in a type b and returns bool
-- But the type of b is used twice when the input to h is 7 and then it is False
-- Thus b seems to have 2 types which is not allowed.
g :: (b -> Bool) -> Bool
g h = (h 7) && h False

p :: (a,a)
p = (1,1) -- Also does not make sense as p is in the type (a, a) for every type a which is impossible to satisfy without bottom or errors
```

### Ad-hoc Polymorphism
* Refers to `overloading` which means that a function name can be defined for several types and behave differently for each type.
* Uses `typeclasses` which are like interfaces.
* Uses `class` to define the functions and type signatures, then uses `instances` to define the methods for a specific type.

```haskell
-- General class defining functions (like java interfaces with generics)
class Descriptive a where
    describe :: a -> String

-- Instance defining describe for type of Bool. More instances can be made for different types.
instance Descriptive Bool where
    describe False = "False"
    describe True = "True"
```

## Merging Ad-Hoc and Parametric Polymorphism
* These 2 types of polymorphism can be merged as type classes can be used to define functions that only work for types that are instances of a typeclass.
* This is done using the `=>` syntax to denote the class that a must be a subclass of.
```haskell
descrLen :: Descriptive a => a -> Int
descrLen x = length (describe x)
```

## Ad-hoc Polymorphism with Lists
* reads as if b is descriptive then so is [b].
```haskell
instance (Descriptive b) => Descriptive [b] where
    describe [] = "Nothing Left"
    describe (x:xs) = (describe x) ++ "," ++ describe(xs)
```

## Built in TypeClasses
* There are built in type classes such as `show` which provide helper functions that can be used in code.
* These can be overridden to provide definitions for them as shown:
```haskell
data Pcolours = R | G | B

instance Show Pcolours where
    show R = "Red"
    show G = "Green"
    show B = "Blue"

--- The default implementation can be used with the deriving keyword
data Colour = RGB Int Int Int | HSV Int Int Int deriving (Show)
```
* This can also be done for the equality operators using the `Eq` typeclass
```haskell
instance Eq Mobile where
   Toy a == Toy b = a == b
   Stick w x == Stick y z = (w == y && x == z) || (w == z) && (x == y)
   _ == _ = False
```

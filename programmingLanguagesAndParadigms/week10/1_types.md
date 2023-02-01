# Types and Type Inference in Haskell

## Typing Functions
* All objects in Haskell have `types`.
* If type annotations are not present, type declarations are inferred at runtime based on parameters (generic types).
```haskell
f::Int -> Int -- Type annotations for the function
f x = x + 1

f::Integer -> Integer -- can also be used to store arbitrarily long integers

j::a -> Bool -- Function that can accept any input but outputs only Booleans, 'a' can be any other identifier
```

## Type Constructors
* Can be used to combine types into new types.
* Can be chained to show the transformation of types from one function to another for functions that call other functions.
```haskell
f::Integer-> Boolean
f x = True -- dummy function

-- atTen takes an input of a function that converts integers to booleans and returns a boolean which is the result of inputting 10 to the aforementioned function.
atTen::(Integer -> Bool) -> Bool
atTen f = f 10
```

## Algebraic Datatypes
* The ability to create types using the `data` keyword.
* Data types are created using constructors that can act on their own for enumerations or have inputs and thus act as functions to create what is more commonly known as a class. In this case it is known as a `data field`.
* Algebraic datatypes connect the concept of enum data types as well as data fields.
* Algebraic data types can also be recursive which is helpful when defining lists.

### Data Types Without Arguments (Enums)
```haskell
data SwitchState = On | Off -- On is a constructor that constructs of type SwitchState. This kind of no-input data can be used as enums.

toggle On = Off
toggle Off = On

isOn On = True
isOn Off = False

main = print(isOn (toggle On)) -- Prints False
```

### Data Types with Arguments
```haskell
data MyIntPair = IntPair Int Int -- Intpair is a function that takes 2 ints and returns a MyIntPair, essentially like:
IntPair:: Int -> Int -> MyIntPair

mySumPair (IntPair x y) = x + y
```

### Algebraic Data Types
```haskell
data BoolOrInt = Abool Bool | Anint Int

intval::BoolOrInt -> Int
intval (Abool True) = 1
intval (Anint x) = x
```

### Algebraic Recursion
```haskell
data MyList a = Empty | Append a (MyList a) -- Append and Empty are new constructors, MyList can either be Empty or be a function that takes a value and a previous list of values, thus appending it.

myHead Empty = Nothing -- Nothing is a built in type
myHead (Append x l) = Just x -- Just is a built in type that corresponds with Nothing to show that a value has been returned instead of Nothing.

main = print(myHead (Append 10 (Append 11 Empty)))
```
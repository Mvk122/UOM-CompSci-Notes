# Input Output in Haskell

## IO Type 
* Input Output is done via the `IO` type.
* Thus haskell programs are definitions of the main function which is of an IO type.
* IO values are same as other values and can be returned or operated on.
```haskell
main = (print "Hi":: IO())

greet n = print("Hi" ++ n) -- Function that takes in n and prints
main = (getline:: IO String) -- Takes in an input from the user
```

## Return operator
* Return is an IO action that passes IO values to other functions, doing nothing on its own.

## >> and >>= Operator
* `>>`  Sequences actions together, creating a chain of actions that do not pass their return values to each other.
* `>>=` Is the bind function that sequences actions together, but also passes results from the first function to the inputs of the second function.
* The types of IO cannot be converted directly into types as it depends entirely on what the user types in. `>>=` helps with that.
```haskell
main = print "Enter your name:" >>
       getLine >>= (\n -> print (n ++ " is so cool!"))
-- >>= Can also be used to cast, it is essentially equal to the following type definition
>>= :: IO b -> (b -> IO c) -> IO c
```

## Recursively Defined IO
* `>>` and `>>=` can be used to recursively define IO, making loops in the code by referencing functions that call themselves (similar to GOTO).
```haskell
-- main is pointing to main based on the condition that the input was not "Joe"
main = putStrLn "Who is the greatest?" >>
       getLine >>=
      (\n -> if n == "Joe"
             then putStrLn "Don't forget it!"
             else (return "Be serious!" >> main))
```

## Do Notation
* Do notation can be used to write chains of functions, similar to that of an imperative style without overusing the `>>` and `>>= operators`.
* The behaviour of `>>=` can be replicated by using `variable <- value` to store values in variables.
```haskell
main = do
         putStrLn "Enter a name:"
         n <- getLine
         putStrLn "Enter another name:"
         m <- getLine
         putStrLn ("Hello " ++ n ++ " and " ++ m)
```

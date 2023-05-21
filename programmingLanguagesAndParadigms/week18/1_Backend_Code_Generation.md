# Backend Code Generation 
* The backend needs to take the partly optimised intermediate representation and select target language instructions through pattern matching.
* It needs to be optimised for the target language.

## Code Generation for Arithmetic Expressions
* Can be easily pattern matched with the IR.
* Can be easily locally optimised, assuming there are enough registers.
* Is done by parsing the left subtree first and then the right.
* There is a second pass to minimise register usage.
* Optimisations can be made in the form of using shifts and adds instead of using expensive multiplication operations.
## Arrays
* Arrays can be allocated in `row-major` form where to get element `array[i][j]` from an array size `array[n][m]` we use:
$$
element = base + (i*(m+1)+j)*w
$$

## Control Flow
* If-Else can be coded as such:
```
if false goto B1
// Code inside if statement goes here
goto B2
B1
// Code inside else block
B2 // call ends here
```
* For loops and while loops can be coded as such:
```
B1 if false goto B2
// Code inside loop
goto B1
B2
```
## Procedures
* Procedures are expensive as for every call:
	* Memory allocations need to be done for procedure specifics.
	* Memory needs to be deallocated after the call is over.
	* Variables need to be initialised.
	* The state of the registers prior to entering the function need to be pushed to the stack/ memory so that registers can be used by the function call.
	* The state of the registers on exiting the function call need to be replaced with the previous register state except for any registers containing return values.
* Optimisations called `method-inlining` can be used wherein the code for methods is embedded in the code that they are called from.
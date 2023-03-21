# Introduction to Compilers

## Definitions
* `Compiler`: A program that accepts an input as a program text in a certain language and produces as output a program text in a different language while preserving the meaning of the text.
* `Interpreter`: A program that reads a source program and produces the results of executing this source.

## Aims of a Compiler
* The aims of a compiler are to balance the following antagonistic principles in accordance with the requirements for each.
* `Preservation`: Preserving the meaning of the program.
* `Speed`: To ensure that the compiled code runs as fast as possible.
* `Space`: To ensure that the compiled code adheres to space constraints.
* `Feedback`: To ensure that the compiled code provides adequate information to the user.
* `Debugging`: To ensure that the compiled code works with debuggers as transformations otherwise obscure the relationship between the source code and target.
* `Compilation`: To ensure the compilation is as fast as possible given the above constraints and the requirements given for each.

## Structure of a Compiler
![[Pasted image 20230307174506.png]]
### Front End
* Takes the source code and analyses it for errors that make the source code legal or illegal.
* Collects the semantics of the source code and collects it in an `Intermediate Representation`.
* The `Internal Representation` is used as the source code is not an ideal state for the compiler to manipulate the program to the above aims.
* Typically runs in $O(N)$.
### Back End
* Chooses instructions to implement each IR operation based on the target system.
* Needs to conform to system interfaces.
* It is `NP-Complete` (A problem that we do not know how to solve in less than polynomial time).

## Intermediate Representations
![[Pasted image 20230309123155.png]]
* Allows for frontends for any language supporting the IR to be compiled with any backend that supports the IR.

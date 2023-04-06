# Compiler Frontend Structure
![[Pasted image 20230309123352.png]]

## Lexical Analysis
* Reads characters in the source of the program and breaks them into words.
* Creates tokens which have a pair of the form `<type, lexeme>` eg:
```
a = b + c becomes:
<id,a> <=,> <id, b> <+,>, <id,c>
```
* It also stores all the id attributes in a symbol table.
* Outputs a series of tokens.
## Syntax Analysis
![[Pasted image 20230403200831.png]]
* Analyses if the tokens in the lexical analysis are in a sensible order using a hierarchal structure defined by a context free grammar.
* This creates a hierarchal parse tree that is expressed using recursive rules.
* Outputs a parse tree. Before outputting the parse tree, the nodes used to check syntactic correctness, (the yellow nodes) are removed.
## Semantic Analysis
* Collects context information and checks for semantic (logic) errors. The errors are annotated in the nodes of the tree.
* Includes the checking of errors that could not be done in syntax analysis as the context is not analysed eg checking that the code does not try to add a string and an int.

## Intermediate Code Generation 
* Takes the abstract syntax tree from above and converts into more general constructs that are straightforward to be used to generate target code from the intermediate representation.
* An example is 3 address code wherein there is an operand and at most 3 operators. This is useful as it is analogous to assembly code.
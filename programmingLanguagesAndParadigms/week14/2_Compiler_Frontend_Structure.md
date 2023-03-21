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
## Syntax Analysis
* Analyses if the tokens in the lexical analysis are in a sensible order using a hierarchal structure defined by a context free grammar.
* Outputs a parse tree.
## Semantic Analysis
* Collects context information and checks for semantic errors. The errors are annotated in the nodes of the tree.
* Includes the checking of errors that could not be done in syntax analysis as the context is not analysed eg checking that the code does not try to add a str and an int.
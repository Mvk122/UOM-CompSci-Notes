# The Middle End 
* The middle end is used to transform the code represented by the IR into equivalent but more efficient code.
* It can also be used to detect semantic errors unrelated to syntax such as:
	* Calling a function that has not been defined in the current scope.
	* Type checking at compile time.
	* Ensuring functions have taken in the right number of inputs.
* Semantic errors in general need to answer context sensitive questions.
* This can be done either by:
	* `Formal Methods`: Using context-sensitive grammars to parse the language. This method is difficult as it is difficult to encode these questions in a context-sensitive grammar in a manner that is small enough to manage.
	* `Ad-hoc methods`: Using methods like `symbol tables`. This is the preferred method.

## Symbol Tables
* First created during #lexicalAnalysis and is used to check semantic questions by associating a snippet of code that would execute every time the parses reduces a production rule in the CFG. (Reductions are done in the front-end via either #bottomUpParsing or #topDownParsing).
* It stores information on many items such as: 
	* Variable names
	* Defined constants
	* Defined functions

> This is just a discussion on how to implement a dictionary, most will remember it from Algorithms and Data Structures
## Symbol Table Implementations
* It can be implemented in either:
	* `Linear List`: Simple but slow, $O(n)$
	* `Binary Trees`: Need to ensure it does not become unbalanced otherwise it would have $O(1)$ time complexity. The balanced tree would have a complexity of $O(log_2(n))$
	* `Hash Table`: Uses a hash function to map names into integers, can be $O(1)$ but needs an inexpensive hash function that reduces collisions. This solution can be optimised to be faster if functions are scoped so not all functions need to be on 1 hash table. #hashTables 
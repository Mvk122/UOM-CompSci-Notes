# Syntax Analysis
* Analyses if the tokens in the lexical analysis are in a sensible order using a hierarchal structure defined by a context free grammar.
* Uses a `context free grammar` as regular languages are constrained as they do not have means of doing operations that require memory like counting or nesting. For example, the language of balanced parentheses cannot be encoded by a regular language.

## Expressing Context Free Grammars 
* Context-Free Grammars have 4 constructs:
	* The starting symbol `S`.
	* Non-terminating symbols `N`
	* Terminating symbols `T`
	* Production rules `P` which show which constructs can lead to other constructs.
* For example the cat language of 1 or more MIAUs can be expressed as:
	* S -> miauS | miau
* Each string can be created through the production rules in 1 or more ways hence there is no 1 parse tree for any given syntactically correct string. This means that the grammar is `ambiguous`
* Hence we choose by convention to either use leftmost or rightmost derivation wherein either the leftmost or rightmost non-terminal symbol is replaced. However, even with these conventions, there can still be multiple leftmost/rightmost derivations for a language.
* Ambiguous grammars can lead to incorrect parsing of languages based on the algorithm used to build the parse tree, hence languages need to be rewritten to remove ambiguity.


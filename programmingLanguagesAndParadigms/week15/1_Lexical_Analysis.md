#lexicalAnalysis
* The act of reading characters in the program to produce a sequence of tokens.

## Performing Lexical Analysis
* Lexical analysis is conducted using regular expressions.
* They are done using regular expressions such that:
	* The specification of the language is simplified.
	* We are be able to use existing lexical analysers.

## Matching Regular Expressions
![[Pasted image 20230406061018.png]]
* Regular expressions can be matched using transition diagrams wherein each state has transitions into and out of it.
* At each step, a character is consumed, transitioning from one state to another. If the final state that the string ends on is an accepting state, then the string is part of the regular language described by the regular expression.
* The transition diagram can be stored in a transition table where there is a column for each input symbol and a row for each state. Eg:
| State     | 'a' | digit |
| --------- | --- | ----- |
| 0         | 1   | -     |
| 2 (final) | -   | 2     |
* The transition table is able to encode `Deterministic Finite Automatas`. All regular expressions can be described using a DFA, usually through creating a `Non-Deterministic Finite Automata` then converting it to a DFA.

## Regular Expressions to NFAs using Thompson's construction
![[Pasted image 20230406062203.png]]

## Converting NFAs to DFAs
* TODO: Get the algorithm from fundamentals of computation

## Minimisation Of DFAs
![[Pasted image 20230406070218.png]]
* Minimisation is used to reduce the number of states in a DFA. 
* It is done by finding group of states where for each input symbol, every state of such a group will have transitions to the same group.
* The algorithm is as follows:
	* Create 2 groups of states, final and non-final states.
	* For each character transition, check if there are any transitions that lead to another group, if so, split on this group.
	* If there is a transition from one of the states in the group to another state, split the state out on the next iteration.
	* Stop on the iteration wherein there is no more splitting. The states of the groups can then be combined.

## Direct Coding from the Transition Table
* Tables can be inefficient as a means of storing regular expressions as tables use an abundance of slow memory operations.
* Thus automatically generated code can be used instead.
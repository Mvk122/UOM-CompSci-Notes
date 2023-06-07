# Intractability
* Refers to how difficult a problem is to solve. There are different types of problems:
	* `Class P`: Problems that are solvable in polynomial time.
	* `Class NP`: Problems that are verifiable in polynomial time or problems that are solvable in polynomial time by a `non-deterministic machine`.
	* `Class NP-Hard`: Problems that are at least as hard as all problems in `NP`.
	* `Class NP-Complete`: Problems that are both in `NP-Hard` and `NP`.
* Thus $P <= NP$

## Decision vs Optimization Problems
* Decision problems are not harder than optimization problems as optimization problems need to be decided before producing an optimal answer (eg an answer needs to exist for there to be an optimal one.)
* Hence if we can show that the decision problem is hard, the optimization problem will also be hard (reduction).

## Encoding Problems
* In problem descriptions, inputs to functions are abstract eg they can be of any datatype.
* In algorithms they need to be concrete eg represented in a way that computers understand.
* Hence there is a standard encoding of integers and lists to a binary representation.
* Hence we can assume that all inputs are binary strings hence a decision problem can be defined as "the set of binary strings where the answer is 1".
* There are caveats to his system eg:
	* in encoding numbers as the encoding of numbers is logarithmic to its value, the encoding of a number $n$ takes $k = log_2(n)$ bits.
	* An algorithm that is linear in $n$ is exponential in $k$.
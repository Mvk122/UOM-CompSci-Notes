#topDownParsing
# Top Down Parsing
* Starting with the starting symbol of the grammar, repeatedly match the leftmost non-terminal rule with the left hand side of a production rule and replace it with the right hand side.
* If the wrong production rule is chosen however, the parser will need to backtrack if a dead end is encountered.

## Issues with Top Down Parsing: Left Recursive Grammars
* Top down parsing can recurse indefinitely in the case of a `left recursive grammar` if the production rule chosen can recurse indefinitely.
* A `left recursive grammar` is a grammar that has a rule wherein  $A => Aa$
* This can recurse indefinitely in the following manner:
```
production rule: A => Aa
current string = A , apply the rule:
A => Aa, apply the rule: 
A => Aaa, apply the rule: 
A => Aaaa indefinitely
```
* Left recursion can be eliminated by substituting the rule wherein $A => Aa | b$ with $A=>bA'$ and $A => aA' | Ɛ$

## Look Ahead to Prevent Backtracking
* If a top down parser chooses the wrong rules and reaches a dead end, backtracking is required to correct the mistake.
* Backtracking can be prevented by looking ahead at the next tokens in the input to decide which production rule to choose.
* In general, an arbitrarily large amount of looking ahead is required however if a language has the  `LL(1)` property, only looking ahead once is required.

## LL(1)
* `LL(1)` refers to wherein if $A =>B$ and $A =>C$ both exist, we need to make sure that any first terminal symbol produced by B is different from any first terminal symbol produced by C.
* If the `LL(1)` property doesn't exist, the grammar can be transformed by factoring any common prefix eg $A => ab_1 | ab_2 | ab_3$ becomes $A => aZ$ and $A => b_1 | b_2 | b_3$
* 
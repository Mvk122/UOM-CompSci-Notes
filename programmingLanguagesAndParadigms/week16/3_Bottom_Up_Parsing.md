#bottomUpParsing
# Bottom Up Parsing
![[Pasted image 20230519161031.png]]
* Parsing of a string by starting from the leaves and working towards the root.
* Done by matching some right-hand-side grammar rule to some left hand side until reaching a goal state.

## Handles
![[Pasted image 20230519161446.png]]
* The pair of `position` and `production` rule is called a `handle`.
* If a grammar is unambiguous, then every right-sentential form has a unique handle which can be used to find a derivation.

## Shift Reduce Parser
* The bottom-up parsing, given the handles can be implemented using a `shift-reduce` parser:
```python
def shift_reduce(stack, tokens, goal_token):
	token = tokens.next()
	while not (top_of_stack == Goal and token == ''):
		if is_handle(stack.top()):
			symbol, string = match_handle(stack.top(), token)
			stack.pop() # removes string from the top
			stack.push(symbol)
		elif token != 'EOF':
			stack.push(token)
			token = tokens.next()
		else:
			raise Exception("Should not get here!")
```
* This parser does not always work as it can lead into a dead-end wherein the goal state is reached before all the tokens are parsed. (Shift-Reduce conflicts)
* To prevent this from happening, a modified shift-reduce parser can be used which takes in an `LR(1)` grammar to look-ahead and make better decisions to either shift or reduce.

## LR Grammars
* `LR(n)` grammars are grammars where `n` input symbols are used for a lookahead.
* Grammars are LR(n) grammars if given a right-most derivation we can: 
	* Isolate the handle of each right-sentential form
	* Determine the production by which to reduce by scanning the sentential form from left to right, going at most `n` symbols beyond the right-end of the handle.

## Shift Reduce with LR(1)
![[Pasted image 20230520195454.png]]
* LR grammars contain a table that consists of 2 parts: 
	* `action(state_on_top_of_stack, input_symbol)`: Returns either a shift which pushes the next symbol and state.
	* `goto(state_on_top_of_stack, non_terminal_symbol)`: Returns the state to push onto the stack after a reduction.
* We can parse the expression by adding extra state information after each symbol in the stack that summarises the information contained in the stack below it.
* By querying the extra state information with the table, we can make a decision to either shift or reduce.
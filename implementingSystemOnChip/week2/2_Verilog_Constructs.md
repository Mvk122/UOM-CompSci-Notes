# Verilog Constructs

## Fork Join
```verilog
fork 
	// Thread 1
	// Thread 2
	// Thread 3
join
```
* Each line in the fork join block runs in parallel with one another.
* For multiple lines sequentially within a fork, use `begin` and `end`
![[Pasted image 20231114165514.png]]
![[Pasted image 20240207174211.png]]
* Process level parallelism: Multiple processes on multiple cores, allows for parallelism even in programs only designed for a single core. 
* Thread level parallelism: 1 Process on multiple cores.

## Instruction vs Thread Level Parallelism
[[4_Instruction_Level_Parallelism]]
* `Instruction Level Parallelism`: Hardware automatically parallelises a sequential stream of instructions to run them out of order, ensuring that the result produced is the same as if it was done in order.
* `Thread Level Parallelism`: The programmer divides the program into long sequences of instructions to be run in parallel. The main issue is synchronisation and sharing data between threads.

## Data Parallelism
* Exploiting structured parallelism in specific programs by running the same computations on different subsets of the data i.e matrix multiplication.
* 
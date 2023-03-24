# Control Hazards

## The Control Transfer Problem
* The simple pipelining process only works if the processor only fetches instructions sequentially. This is not the case for branch instructions.
* Hence fetching the instruction after a branch can lead to a wasted cycle as the branch is only detected in the decode stage, and the second instruction has already fetched by the decode stage of the first instruction.
* This problem becomes worse if it is a conditional branch as then the branch would only be detected at the execute stage of the first instruction, thus wasting 2 clock cycles.
* This problem can be alleviated using `branch prediction`. 

## Branch Prediction with a Branch Target Buffer
![[Pasted image 20230324063906.png]]
* Since instructions are rarely changed in memory, a Branch Target Buffer can be used as a cache to check if an instruction is a branch instruction and if so, what is its target address.
* Thus if the branch is a valid entry in the BTB (Has been taken before and the instruction hasn't changed), we can instead start processing the instruction in the target address as opposed to the instruction right after the branch instruction.
* For unconditional branches, this always works however for conditional branches, the effectiveness of this strategy depends on the probability of repeating the target, the probability will be higher on larger for loops.
* It is still only a prediction hence there is a penalty for getting it wrong.

### Real World Implications of BTB
* It is expensive to implement.
* It only uses the last branch to predict.
* Prediction accuracy can be increased with more history and context, thus other methods are used for better branch prediction. 
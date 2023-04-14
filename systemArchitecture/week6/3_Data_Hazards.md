# Data Hazards
* Pipelines can also cause problems in data, wherein a later instruction requires data returned from a previous instruction. Thus there is a `data dependency` between the instructions.
* This can occur if a later instruction needs data in its execute stage while the previous instruction has not updated the specific data in the registers in its memory write-back stage.

## Dealing with Data Dependencies
### Detect and Hold Instructions
![[Pasted image 20230324064943.png]]
* Dependencies can be detected in the hardware and later instructions with a data dependency are held in their decode stage, stalling their pipeline until the data is ready.

### Compiler re-ordering instructions 
* The compiler can reorder instructions to prevent data dependencies in adjacent instructions by doing other work in between instructions with data dependencies.
* This is entirely dependant on the compiler being able to find other work to do, otherwise it will insert many No-Operation instructions.

### Linked Inputs and Outputs (Forwarding)
#### Execute Stage Linkage
* Extra hardware can be used to link the output of execute into the input of the execute for the next instruction, allowing the next instruction to use the data from the previous instruction before it is written to the registers.
* This leads to the control being more complex.
* This is useful in scenarios such as:
```asm
ADD R1, R2, R3
MUL R4, R1, R2 // The MUL instruction needs the data in R1 however the first instruction is not in its memory writeback stage when the second instruction is in its execute stage
```

#### Memory to Execute Stage Linkage
* The above issue can happen in a different stage when using instructions such as `LDR`. 
* Subsequent instructions can require data that is in the MEM stage in the previous instruction.
* Thus another hardware linkage can be created between the memory stage and the inputs of the execute stage.
* This is useful in scenarios such as:
```asm
LDR R1, [R2, R3]
MUL R0, R1, R1
```

### Buffering
![[Pasted image 20230414052054.png]]
* Another method is to insert buffers between each stage, storing the result of the previous computation so that the next instruction can be performed without having to wait due to a data dependency.
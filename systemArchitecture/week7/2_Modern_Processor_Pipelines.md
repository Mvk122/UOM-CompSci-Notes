# Modern Processor Pipelines
![[Pasted image 20230414065222.png]]
![[Pasted image 20230414065213.png]]
* Modern processors have many execution flows (`Functional Units`)  as opposed to only one pipeline to allow for specific hardware to be used for specific instructions.
* This can allow for more parallelism as instructions can be put into the pipeline for the functional unit that their instruction corresponds to and instructions of different types can be executed at once.
* However, some of these `functional units` can be pipelined and others cannot, creating a `structural hazard` wherein if all suitable functional units for an instruction are busy, the instruction cannot be executed at the current time.


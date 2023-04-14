# Instruction Level Parallelism
![[Pasted image 20230414060422.png]]
* Real programs often have many instructions that are independent hence multiple instructions can be processed at once.
* This requires multiple instructions to be fetched, decoded and executed in the same cycle.
* This comes at the cost of needing multiple:
	* ALUs
	* Register Ports as the access rate will be multiplied.
	* Data cache Ports as the access rate will be multiplied.
* The instructions to be run in parallel need to be selected hence there can be a `dispatch unit` in the fetch stage that uses hardware to examine instruction dependencies and issue instructions in parallel if they are independent.
* Modern processors are usually up to 4-way superscalar. This is due to scalability issues wherein:
	* The complexity of the hardware increases greatly with every extra lane.
	* Applications may not exhibit enough parallelism to exploit such a large processor.
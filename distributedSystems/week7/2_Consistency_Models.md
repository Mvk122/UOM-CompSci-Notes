# Consistency Models
![[Pasted image 20230411200519.png]]
* A consistency model is a contract between processes and a distributed data store that the processes have access to.
* The data store aims to be consistent hence any write operations to a local copy are propagated to the other copies over time.
* A consistency model restricts the values that a read operation on a data item can return.

## Sequential Consistency
![[Pasted image 20230412081452.png]]
* The result of any execution if the same as if the operations by all processes on the data store were executed in some sequential order.
* Therefore, despite writing b after writing a, if process 3 reads b and only then a, all other processes must read b first and then a or only a.
* No process should be able to read a first and then b in this scenario.

## Causal Consistency
* Writes that are potentially causally related must be seen by all processes in the same order.
* Concurrent writes that are not causally related may be seen in a different order in different machines.
* Being `causally related` means that an event is caused or influenced by an earlier event.
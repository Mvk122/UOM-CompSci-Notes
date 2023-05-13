# Redundancy
* Used to hide faults from other processes (fault tolerance).
* There are many types of redundancy:
	* `Physical Redundancy`: Having extra resources/hardware that are redundant such that if one fails, the other identical resources can be used instead.
	* `Time Redundancy`: An action can be performed many times in sequence until it works. This is useful when faults are transient and intermittent.
	* `Information Redundancy`: Sending extra bits of information to allow for error recovery.

## Isolated Execution
* Even if individual transactions are atomic, their outputs can still be incorrectly modified by concurrent transactions involving the same resources. (Eg write after reads).
* There are 2 ways to solve issues caused by concurrency.
### Serial Execution
* Only one transaction at a time.
* Is simple but does not scale and is very slow.
### Concurrent Execution
* Can be done fast but requires following rules for transactions to remain ACID (Atomicity, Consistency, Isolation and Durable). Rules such as:
#### Using Transactions
* All operations must be transactions wherein results are only committed to the storage once all operations in the transaction are successful.
* There must be concurrency control to ensure that the execution is equivalent to a serial execution. This comes at a performance cost as long transactions will block other transactions.
	* This can be done using 2 phase locking wherein in the first step, read and write locks on resources are acquired. Then the operations are performed and then the locks are released.
#### Durability Mechanisms
* There must be `recovery algorithms` that replay the actions of committed transactions and undo the effects left behind by aborted transactions.

## Process Replication
* Is a redundancy mechanism to ensure calculations are done correctly.
* There is a performance penalty however as most solutions require a large exchange of messages between processes.
### 2 Phase Process Replication 
1. The coordinator sends a vote request message to all participants.
2. Participants send either a `vote-commit` or a `vote-abort` to the coordinator.
3. If all are `vote-commits`, the coordinator tells all participants to commit. 
4. If there is at least 1 `vote-abort`, the coordinator tells all participants to abort.

# Replication
* Data replication is a means to increase the `reliability` and `performance` of a system.
## Data Replication Motivation
### Reliability
* If data has been replicated, corruption or loss of data in one of the copies is not a significant issue as the system can switch to one of the replicas.

### Performance
* `Size`: Replicating data amongst many servers allows for more a multiplication of the data throughput as clients can request the data from any one of the servers.
* `Latency`: If replicas are placed in various geographic locations, the time to access the data decreases for clients as they can pull the data from their nearest sources.

## Cons of Data Replication
### File Modification
* More network bandwidth is consumed to keep all replicas up to date when a change occurs.

### Ensuring Tight Consistency
* To ensure that all copies are the same at all times, changes to the copies need to be `atomic` operations wherein they all succeed/fail and must all be done at the same time.
* This is difficult as:
	* The replicas could be widely dispersed across a large scale network.
	* Operations on the replicas may be required to complete quickly.

## Relaxing Tight Consistency
* In order to have data replication without the difficulty of ensuring tight consistency, we can relax the constraints on tight consistency by allowing other non-tight consistency models.
* In general, changes don't need to be instantaneous globally in these consistency models.


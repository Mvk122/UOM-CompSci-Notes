# Purpose of Distributed Systems

## Definitions
* `Distributed Systems`: A collection of autonomous `computing elements` that appears to its users as a `single coherent network`.
* `Computing Element / Node`: A hardware device or a software process. Since these nodes are autonomous, each node will have its own notion of time which causes complications.

## Purpose of Distributed Systems
* To make continuously evolving remote resources `accessible` for sharing.
* To open processes to `external interactions`.
* To achieve better `performance/cost` ratios.
* To `scale` effectively if demand for specific resources changes significantly.
    * Scaling up can be done to address more demand.
    * Breaking a system into multiple pieces allows for more modular scaling down when demand reduces, thus reducing costs.
* To achieve high levels of `reliability` and `availability`

## Properties of Distributed Systems
* Computations are `concurrent`.
* There is no shared state or global clock to follow hence nodes are `autonomous` and have their own notion of time.
* `Failures` occur and the system needs to recover from them.
* Nodes `communicate` with each other by exchanging messages. Thus nodes cannot ignore each other.
* There is `transparency` to ensure that it appears as a single coherent system to users.
* They often have a separate layer of software that is placed logically above the operating system to assist development by:
    * Facilitating inter-application communication.
    * Running security services.
    * Running failure recovery.
    * Facilitating web service composition.

## Challenges that Distributed Systems Face

### Network Reliability
* The `topology` of the system may vary as it is composed of varied software and hardware managed by different organizations hence routes for data transfers cannot be guaranteed.
* Network reliability can further be reduced by hardware failures/ downtimes.

### Network Security
* There is no assurance that the network is secure hence applications need to have their own forms of security.
* This can lead to programming challenges as networked resources may be gated behind specific privileges that need to be acquired.

### Network Heterogeneity
* Networks are not uniform hence `interoperability` through `standardized technologies` such as JSON and XML will be necessary.

### Topology Variance
* The `topology` of the system may vary.
* Hence specific endpoints or routes should not be relied upon.
* The physical structure of the network should be abstracted away such as using DNS instead of IP addresses.

### Network Latency
* Communicating over the network takes time hence network communication should be kept to a minimum for performance considerations.

### Network Bandwidth
* To avoid congestion and improve connection throughput, data packet loss can be reduced by using `larger packet sizes`.
* `Data compression` can also be used to make better use of bandwidth.

### Transport Cost
* Transporting data over the network costs time and money as information needs to be `serialized` and operating the network hardware has a cost.

### Multiple Administrators
* There are different administrators associated with different parts of the network hence due to the `human factor`, it can be hard to:
    * Locate problems.
    * Coordinate upgrades.

## Network Transparency
* The network needs to be transparent/ hide properties of the network to end users.
* `Access`: Hides differences in data representation and how objects are accessed.
* `Location`: Hides where an object is located.
* `Relocation`: Hides that an object may be moved during use.
* `Migration`: Hides that objects are moved to another location
* `Replication`: Hides that an object is replicated.
* `Concurrency`: Hides that an object can be shared by multiple users.
* `Failures`: Hides the failure and recovery of an object.
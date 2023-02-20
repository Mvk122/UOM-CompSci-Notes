# Naming in Distributed Systems
* Names are used to uniquely identify entities in order to address them.

## Centralised Naming
* Is the most obvious approach to guaranteeing that any name is handed out only once.
* It is not a scalable solution and creates a single point of failure.

## Free For All Naming
* Allows entities to make up their own names.
* Does not have a single point of failure but also does not guarantee uniqueness.

## Delegating Naming Responsibilities
* The authority to allocate names is delegated to smaller parts of the system.
* It is scalable and can guarantee uniqueness.
* Is used by `MAC Addresses`, `IP Addresses` and `Domain Names`.

## MAC Addresses
* A unique identifier given to each network device in a system.
* Made of an `Organisationally Unique Identifier`, purchased from the IEEE and the `Network Interface Controller` which is the vendor's responsibility to ensure is unique.

## IP Addresses
* Is delegated by the `IANA` to regional internet registries which delegate it further to ISPs.
* It is a unique identifier on the internet and contains information on where a device is on the network.
* The delegation strategy chosen gives some physical location information for any IP address.

## Domain Names
* Built on top of the internet to create human readable names that point to IP addresses.
* DNS needs to respond in real time to requests and it does so using a hierarchy of servers with the most authoritative server at the top of the hierarchy.
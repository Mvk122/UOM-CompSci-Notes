# Security

## Security Mechanisms
### Secure Channels
* Secure channels are methods used to ensure that communication between users/processes cannot be modified, read or deleted by unauthorised third parties.

### Access Control Mechanisms
* Access control methods deal with `authorisation` to ensure that a process gets only the access rights to the resources in a system that it is entitled to.

## Types of Security Threats
* `Interception`: An unauthorised party is able to gain access to a service or data and is able to overhear it.
* `Interruption`: A service or data becomes unavailable or destroyed.
* `Modification`: Data being changed without authorization
* `Fabrication`: Additional data or activity is generated that would normally not exist.

## Security Mechanisms
### Encryption
* Transforming data into something an attacker cannot understand 
* Prevents eavesdropping but can also support integrity checking to check that data has not been modified.
* Can be one of either: 
	* `Symmetric`: Using the same key for encryption and decryption.
	* `Asymmetric`: Using a different key for encryption and decryption.

### Authentication
* Used to verify that the claimed identity of a client is actually the identity that it is claiming.
* It is based on the client possessing secret information that can be verified.

### Authorization
* Checks whether a client has the authorisation to perform the requested action.

### Auditing
* Used for analysis to trace which clients accessed what and in which way, to analyse security breaches and take measures against intruders.

# Definitions
* `Synchronous design`: is based upon the principle that all state elements (dtypes) can only be changed on a single event trigger (for instance, a positive clock edge).

# Reasons to use Synchronous Design
* It is best to keep to a synchronous style when creating a design:
	* Time is quantised instead of continuous.
	* Given a state and inputs, the next state can be determined unambiguously.
	* Logic hazards are irrelevant.
	* Current toolchains and implementation technology is tuned for synchronous designs.

# Parallelism
## Reasons to use Parallelism
* Benefits of increased parallelism: 
	* Increased speed
	* Can decrease complexity 
	* Can decrease power usage
* Drawbacks of increased parallelism: 
	* can increase resources required.
## Parallelism Techniques
### Pipelining
* Subdivides the logic.
* Allows for an increase in clock speed as the computati
* Pre-evaluating some of the logic in an earlier stage.
* Using a more parallel logic expression (different algorithm).


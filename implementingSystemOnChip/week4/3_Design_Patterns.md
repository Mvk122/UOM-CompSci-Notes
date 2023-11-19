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
* Allows for an increase in clock speed as the computation is done in parallel by different pieces of hardware hence less operations are required from each hardware module. (Increased throughput)
* Can increase latency.
* Has a small area overhead.
* Depending on the design, can either save or use more power: 
	* Saves power by reducing logic switching by preventing glitch propagation.
	* Can increase power as `clock loading` is increased. (Getting the clock cycle to the components).
* Can simplify the design process by decomposing into sensible blocks.

### Data Parallelism
* `SIMD`: Single instruction multiple data, can process more smaller data elements simultaneously.
* `Interleaving`: In instructions that require multiple clock-cycles where the data flows through different components, interleaving can be used such that later instructions can be executed while waiting for the computation of a previous result.

### Other
* Pre-evaluating some of the logic in an earlier stage.
* Using a more parallel logic expression (different algorithm).


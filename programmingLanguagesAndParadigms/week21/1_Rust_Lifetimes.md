# Rust Lifetimes
* Lifetimes in rust refer to the time between the creation of an object and its last use.
* Lifetimes can be `scoped` using `{}` wherein objects created within the brackets do not exist outside the brackets.
* Functions need to represent the lifetimes of their inputs and outputs so the compiler can keep track of them, this is usually done implicitly but can be done explicitly. this can be done with `<'m>` syntax. https://stackoverflow.com/questions/31609137/why-are-explicit-lifetimes-needed-in-rust
```rust
fn main() {
	let a = 5;
	{
		let b = 4;
	} // b is not defined after this bracket.
}

// States the lifetimes of inputs and outputs using m and n
fn swap <'m, 'n>(x: &'m u32, y: &'n u32) -> (&'n u32, & 'm u32) {
	return (y, x);
}
```
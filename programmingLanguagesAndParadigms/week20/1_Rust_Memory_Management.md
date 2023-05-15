# Rust Memory Management
## Memory Management Paradigms
### C Memory Management
* Manually allocating and deallocating.
* Is very problematic as there can be occurrences of `use-after-free` which leads to undefined behaviour or forgetting to free which leads to a memory leak.
### Java Memory Management Paradigms
* Garbage collection with references.
* Solves the problems with C but has an efficiency cost and can still give `Null Pointer Exceptions` when 2 variables point to the same data and one variable modifies the data in a way which is unexpected for the intended use of the other variable.

## Rust Memory Management
* Rust solves memory management issues by using an `ownership` system that restricts the programmer to ensure that it does not run into memory issues.
* The restrictions that rust imposes are as such: 
	* Every value only has 1 owner. 
	* The data is deallocated as soon as the owner goes out of scope.
	* Assignments and function calls pass ownership between variables.

## Passing Variables in Rust (Borrowing)
* In rust, ownership can be passed between functions through borrowing (pass by reference) with the `&` symbol.
* This only needs to be done with non-basic types, basic types are copied in assignments.
```rust
fn main() {
	let s = String::from("test");
	my_func(s);
	println!("{}",s); // This is not allowed as s is no longer defined as it was used by my_func.

	// Alternative with reassignment
	let s = my_func(s); // my_func returns the value back to main
	fn my_func(s: String) -> String {
	// do stuff
	return(s);
	}

	// Borrowing method
	fn my_func(s: &String) {
	// do stuff, no return required 
	}
	my_func(&s); // my_func borrows s so it is returned to main at the end of its function call so it does not need to be reassigned
}
```

## Mutability
* In Rust, all variables are `immutable` by default, to make them mutable, we need to use the `mut` keyword.
 ```rust
fn main() {
	let i = 10;
	let j = i;

	// The first is not allowed as i is not set to mutable. 
	// The second is allowed as the old value of i is thrown away and i is reassigned.
	i = 11;
	let i = 11;
	// At this point j is still 10 as it was copied over
	incr(i); // The value of i is still 11 as it was copied to incr.
	// To change the value of i in main, it needs to be passed by reference using the & symbol.
} 
// the input to incr needs to have mutable so the copied value can be mutated in the function body. 
fn incr(mut t: u32) {
	t = t + 1;
}
```

## Mutable Borrowing
* To prevent multiple variables from mutably borrowing at once, rust enforces that: 
	* A variable can be immutably borrowed many times. 
	* A variable can be mutably borrowed only once. (It can't be borrowed immutably either).
* The lifetime of a borrow is the time between its creation and last use.
```rust
fn main() {
	let mut s = String::from("hello");
	s.push_str(" world!");
	// example of taking ownership
	let mut t = s; // t takes ownership from s hence s is no longer defined.

	// example of references
	let mut t = &s; // immutable borrow of s, both are still defined and both t and s cannot be modified

	// both the value of t and s are "hello world and universe" and it is allowed as t is used completely in between uses of s hence by the printing of s, t is no longer used anymore and its lifetime is over. 
	// Thus there would be an error if the order of the print statements was changed.
	let mut t = &mut s;
	t.push_str(" and universe");
	println!("{}", t);
    println!("{}", s);
}
```


# C++ Syntax
## Initialising with New
* New is used in C++ as opposed to malloc and it is better than malloc because there is no finnicky methodology in manually having to determine the size in bytes that the object requires.
* Using new is better than malloc but generally should not be used anyway as delete still needs to be called and it might not due to:
	* Programmer error.
	* Multiple lifetime possibilities in branching code.
```C++
int main(int argc, char ** argv) {
	int size = atoi(argv[1]);
	// C Method
	int * heap_arr = malloc(size*sizeof(int));
	free(heap_arr);
	// C++ Method
	int * heap_arr = new int[size];
	delete[] heap_arr
}
```

## C++ References
* References are a handle to another variable. 
* They can be used to pass values to functions without using pointers.
* They are always initialised, are never null and point to the same data for their entire lifetime.
```C++
int main() {
	int a = 5;
	int x = 6;
	int& y = a; // y is a reference to a
	swap(x, y); 
	
}

void swap(int& x, int& y) {
	int tmp = x;
	x = y;
	y = tmp;
}
```

## Function Overloading
* Functions can be defined multiple times with the same name but with different arguments/ argument types to be used with different data types
```C++
void my_func(int a, int b) {
// function body
}

void my_func(float a, float b) {
// function body
}
```

## C++ Classes
* C++ has classes similar to java wherein it has: 
	* A constructor (There can be multiple for different function parameters like function overloading)
	* Public and private functions and variables.
	* Destructors with the name `~ClassName`
	* Operator Overloading to allow for classes to use operators like `+, -, < , >` called with `operator_()` where the `_` is replaced by the symbol.
* Initialiser lists are used in the constructor here to set variables before the lifetime of the Circle Object. This is useful as it allows for constant values to be defined as they wouldn't be able to otherwise during the lifetime of the object.
* If there is no constructor defined, or the initialiser list is not passed, the default one is used. In this case it would set all the variables to 0.
```C++
class Circle {
private: 
	double x, y, r; // Variables of class objects
public:
	double getArea() {
		return 3.14 * r * r;
	}
	// Constructor that is called at the creation of the object
	Circle(double x, double y, double r) {
		x{y}, y{y}, r{r} {};
	}
	// Destructor that is called when the variable goes out of scope
	~Circle() {
	}
	// Defining the + operator for circles
	Cirle operator+(Circle& other) {
	}
}

int main() {
	Circle c1(0.0, 0,0, 1.0); // Initialising with initialiser list
}
```

## Class Code Organisation 
* The definitions of a class along with its variables and functions should be in a header file of its own.
* Each header file should have the definition of only 1 class. 
* The source file (CPP file) should then detail the implementations of the class.
```C++
// circle.h
class Circle{
	private:
		double x, y, r;
	public: 
		Circle(double x, double y, double r);
		~Circle(){};
};

//circle.cpp
#include "circle.h"
class Circle {
// Class definiton here, with :: to show it is part of the class
	Circle::Circle(double x, double y, double r) {
		x{y}, y{y}, r{r} {};
}
```

## Class Inheritance
* C++ classes can inherit methods and variables from other classes. 
* Inherited classes need to explicitly initialise the class they are inheriting.
* Allows for a new `protected` keyword wherein variables are not visible to the public but are to classes that inherit from it.
```C++
class Circle: public Shape {
// Class definition
}
```

## Virtual Functions


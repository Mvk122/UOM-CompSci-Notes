# Design Patterns


## Behavioral Patterns
* Patterns that dictate the ways classes interact and the responsibilities they adopt.

### Strategy Pattern
* Creating a set of objects that hold alternative algorithms that are interchangeable at runtime.
* Allows for strategies to be changed at runtime.
* New strategies can be easily added.
* Common behaviours of the different strategies can be defined in the strategy interface.

```java
//CustomerBill.java
public class CustomerBill () {
    
    public static BillingType billingType
    
    public CustomerBill(BillingType billType) {
        this.billingType = billType;
    }

    public int getAmount() {
        return this.billingType.getAmount();
    }
}

//BillStrategies.java
public abstract class BillingType() {
    public int getAmount();
}

// these 2 classes are in their own files
public class StandardBilling extends BillingType() {
    public int getAmount() {
        return 1;
    }
}

public class OtherBilling extends BillingType() {
    public int getAmount() {
        return 0;
    }
}

// main file
public static void main(String[] args) {
    CustomerBill c = new CustomerBill(new OtherBilling());
    // things can be done using OtherBilling here
    // the billing type can be changed at runtime
    c.billingType = new StandardBilling();

}

```

### State Pattern
* Creating a set of objects that perform a different function for different states.
* A different function will be selected based on the current internal state of a containing object.
* Better than using a bunch of if statements

```java
// Defining an interface for the states to inherit from
public interface PlayerState {
    void action(Player p);
}

// many of these states can be made
public class SurvivalState implements PlayerState {
    @Override
    public void action(Player p) {
        System.out.println("survival state")
    }
}

public class GameContext() {
    private PlayerState state = null;
    // getter and setter methods for the state
	public void setState(PlayerState state) {
		this.state = state;
	}
    // The GameContext can now run the appropriate action based on the state
	public void gameAction() {
		state.action(player);
	}
}

```

## Structural Patterns
* Patterns that dictate how classes and objects are composed to form larger structures.

### Composite Pattern
* Composite patterns create a common base class that defines interfaces and functions that are to be implemented by subclasses.
* Clients then interact with the interfaces defined by the common base class

### Adapter Pattern
* Creating a wrapper class that transforms an incoming request for a piece of functionality into the format accepted by another entity.

```java
// Socket class that needs to be adapted
public class Socket {

	public Volt getVolt(){
		return new Volt(120);
	}
}


// SocketAdapter contains the interfaces that are being adapted
public interface SocketAdapter {
    public void get120Volts();
    public void get240Volts();
}

public class SocketAdapterImpl extends Socket implements SocketAdapter {
    // has the methods defined in SocketAdapter and extends socket to add adapters
}
```


## Creational Patterns
* Patterns that dictate how objects are created.

### Factory Method Pattern
* Creating a class whos purpose is to create objects based on parameters passed at runtime.

```java
public interface Shape {
   void draw();
}
// classes that can be returned by the shape factory that implement/ extend Shape
public class Rectangle implements Shape {}
public class Circle implements Shape {}

public class ShapeFactory {
    public Shape getShape(String shapetype) {
        if (shapeType.equals("Rectangle")) {
            return new Rectangle();
        } else {
            return new Circle();
        }
    }
}
```

### Singleton
* A class whose constructor returns the same object when directed to give a new object.
* Must have a private constructor.
* Must contain a static instance of itself.
* Must have a static method to access its instance globally.

```java
public class Singleton {
    // singleton that is created at load time
    private static Singleton singleton = newSingleton();

    private Singleton() {
    }

    public static Singleton getSingleton() {
        return singleton;
    }

}
```
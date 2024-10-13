**Default Methods** were introduced in Java 8 to allow interfaces to have method implementations. This feature enables developers to add new functionality to interfaces without breaking the classes that implement them. Before Java 8, interfaces could only declare methods, and all methods had to be implemented in the classes implementing the interface.

# Key Points of Default Methods:

- **Backward Compatibility:** Default methods help to add new methods to interfaces without affecting the classes that already implement the interface. This avoids the need to modify the existing code in all implementing classes.
- **Code Reusability:** Interfaces can provide common functionality across multiple classes by implementing default methods, leading to more reusable code.
- **Diamond Problem Solved:** Java handles multiple inheritance scenarios, like when a class implements two interfaces with the same default method, through conflict resolution strategies.

# Syntax of Default Methods:

A default method is declared with the keyword default, followed by its method body.

```java
public interface MyInterface {
    // Abstract method
    void abstractMethod();

    // Default method
    default void defaultMethod() {
        System.out.println("This is a default method in an interface.");
    }
}
```

# Example: Using Default Methods in Interfaces

## Example 1: Implementing Default Methods

```java
public interface Vehicle {
    // Abstract method
    void start();

    // Default method
    default void stop() {
        System.out.println("Vehicle is stopping...");
    }
}

public class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Car is starting...");
    }

    // No need to implement 'stop' method because it has a default implementation in the interface
}

public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        car.start();  // Output: Car is starting...
        car.stop();   // Output: Vehicle is stopping...
    }
}
```

In this example, the Car class only implements the start() method, while the stop() method is inherited from the Vehicle interface via its default method.

## Example 2: Overriding Default Methods

Implementing classes can override default methods if they need custom behavior.

```java
public interface Vehicle {
    void start();

    default void stop() {
        System.out.println("Vehicle is stopping...");
    }
}

public class Bike implements Vehicle {
    @Override
    public void start() {
        System.out.println("Bike is starting...");
    }

    // Overriding the default stop method
    @Override
    public void stop() {
        System.out.println("Bike is stopping...");
    }
}

public class Main {
    public static void main(String[] args) {
        Bike bike = new Bike();
        bike.start();  // Output: Bike is starting...
        bike.stop();   // Output: Bike is stopping...
    }
}
```

In this example, the Bike class overrides the stop() method to provide its own implementation, replacing the default method behavior.

## Example 3: Multiple Interfaces with Default Methods (Conflict Resolution)

When a class implements two interfaces that both define default methods with the same signature, the implementing class must resolve the conflict by overriding the method.

```java
public interface Vehicle {
    default void service() {
        System.out.println("Vehicle is being serviced");
    }
}

public interface Machine {
    default void service() {
        System.out.println("Machine is being serviced");
    }
}

public class Car implements Vehicle, Machine {
    // Must override the conflicting default method
    @Override
    public void service() {
        System.out.println("Car is being serviced");
    }
}

public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        car.service();  // Output: Car is being serviced
    }
}
```

In this case, the Car class implements both Vehicle and Machine interfaces, which have conflicting default methods. The service() method must be overridden in the Car class to resolve this ambiguity.

# Why Were Default Methods Introduced?

- **Interface Evolution:** Before Java 8, adding new methods to interfaces would break all the implementing classes because they were required to implement all methods. Default methods allow interfaces to evolve without breaking the code.
- **Support for Functional Interfaces:** Default methods make it easier to add functional programming constructs (like lambdas and streams) to Java. Interfaces like Iterable, Stream, and Collection gained several default methods to enable functional operations like forEach(), map(), and filter() without changing the classes that implement them.

# Default Methods and Abstract Classes:

- Default methods in interfaces are similar to methods in abstract classes because they provide a concrete method implementation.
- However, interfaces with default methods still don’t allow state (i.e., no instance variables), whereas abstract classes can have instance variables.

# Limitations of Default Methods:

- **Cannot Override Object Methods:** You cannot declare default methods that override methods in Object like toString(), equals(), or hashCode(). This is to avoid ambiguity with the implementations already provided by Object.
- **Conflict Resolution:** If two interfaces provide the same default method, the class must resolve the conflict by overriding the method.

# Conclusion:

Default methods in Java interfaces offer a flexible and backward-compatible way to add new methods to existing interfaces without breaking the implementations of those interfaces. They promote reusability and can simplify the evolution of APIs. However, default methods also introduce complexity when dealing with multiple inheritance scenarios, which need to be carefully managed.

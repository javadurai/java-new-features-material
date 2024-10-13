In Java, Functional Interfaces are interfaces that have exactly one abstract method. They can represent a single behavior or functionality, which can be passed around as a parameter or returned as a result. These interfaces enable the use of lambda expressions and method references.

Java provides several predefined functional interfaces in the java.util.function package, and you can also define your own. A functional interface can have default and static methods, but it should only have one abstract method.

## Characteristics of Functional Interfaces:

1. **Single Abstract Method (SAM):** Functional interfaces are also called SAM interfaces because they contain only one abstract method. This allows them to be easily implemented using lambda expressions.
1. **Annotated with @FunctionalInterface:** This is an optional annotation that can be used to ensure that an interface is functional. If you try to add more than one abstract method to an interface annotated with @FunctionalInterface, the compiler will throw an error.

## Examples of Functional Interfaces:

1. Runnable (in `java.lang`)
1. Comparator (in `java.util`)
1. ActionListener (in `java.awt.event`)

Java 8 also introduced functional interfaces in the `java.util.function` package:

- `Predicate<T>`
- `Function<T, R>`
- `Consumer<T>`
- `Supplier<T>`

# 1. Predefined Functional Interfaces in java.util.function

## 1.1 `Predicate<T>`

Represents a function that takes one argument and returns a boolean result. It's commonly used for conditional checks.

### Syntax:

```java
@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);
}
```

### Example:

```java
import java.util.function.Predicate;

public class PredicateExample {
    public static void main(String[] args) {
        // Lambda expression implementing Predicate
        Predicate<Integer> isEven = (n) -> n % 2 == 0;

        // Test
        System.out.println(isEven.test(4));  // Output: true
        System.out.println(isEven.test(5));  // Output: false
    }
}
```

## 1.2 `Function<T, R>`

Represents a function that takes one argument of type T and returns a result of type R.

### Syntax:

```java
@FunctionalInterface
public interface Function<T, R> {
    R apply(T t);
}
```

### Example:

```java
import java.util.function.Function;

public class FunctionExample {
    public static void main(String[] args) {
        // Lambda expression implementing Function
        Function<String, Integer> lengthFunction = (s) -> s.length();

        // Apply the function
        System.out.println(lengthFunction.apply("Hello"));  // Output: 5
        System.out.println(lengthFunction.apply("Functional Interface"));  // Output: 18
    }
}
```

## 1.3 `Consumer<T>`

Represents a function that takes an argument of type T and returns no result. It is typically used for performing operations on input data.

### Syntax:

```java
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}
```

### Example:

```java
import java.util.function.Consumer;

public class ConsumerExample {
    public static void main(String[] args) {
        // Lambda expression implementing Consumer
        Consumer<String> printer = (s) -> System.out.println(s);

        // Accept and print values
        printer.accept("Hello, World!");  // Output: Hello, World!
        printer.accept("Consumer Interface");  // Output: Consumer Interface
    }
}
```

## 1.4 `Supplier<T>`

Represents a function that takes no arguments and returns a result of type T. It is commonly used for lazy evaluation or object creation.

### Syntax:

```java
@FunctionalInterface
public interface Supplier<T> {
    T get();
}
```

### Example:

```java
import java.util.function.Supplier;

public class SupplierExample {
    public static void main(String[] args) {
        // Lambda expression implementing Supplier
        Supplier<Double> randomSupplier = () -> Math.random();

        // Get random values
        System.out.println(randomSupplier.get());  // Output: random value
        System.out.println(randomSupplier.get());  // Output: another random value
    }
}
```

# 2. Custom Functional Interface

You can also define your own functional interface by ensuring it has a single abstract method.

### Example:

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void greet(String name);
}

public class CustomFunctionalInterfaceExample {
    public static void main(String[] args) {
        // Lambda expression implementing custom functional interface
        MyFunctionalInterface greeting = (name) -> System.out.println("Hello, " + name);

        // Invoke greet method
        greeting.greet("Alice");  // Output: Hello, Alice
        greeting.greet("Bob");    // Output: Hello, Bob
    }
}
```

# 3. Using Functional Interfaces with Method References

You can use method references to refer to methods, making the code even shorter and more readable.

### Example with Consumer:

```java
import java.util.function.Consumer;

public class MethodReferenceExample {
    public static void main(String[] args) {
        // Method reference to System.out.println
        Consumer<String> printer = System.out::println;

        // Accept and print values
        printer.accept("Method Reference Example");  // Output: Method Reference Example
    }
}
```

# 4. Chaining Functional Interfaces

Functional interfaces can be combined (chained) for more complex operations. For example, you can chain Predicates using and(), or(), and negate().

### Example:

```java
import java.util.function.Predicate;

public class PredicateChainingExample {
    public static void main(String[] args) {
        Predicate<Integer> isEven = (n) -> n % 2 == 0;
        Predicate<Integer> isPositive = (n) -> n > 0;

        // Chaining predicates
        Predicate<Integer> isEvenAndPositive = isEven.and(isPositive);

        System.out.println(isEvenAndPositive.test(4));   // Output: true
        System.out.println(isEvenAndPositive.test(-4));  // Output: false
    }
}
```

# 5. Key Advantages of Functional Interfaces:

- **Code Conciseness:** Using lambda expressions and method references makes the code shorter and easier to understand.
- **Reusability:** They promote the reuse of common behaviors like predicates, consumers, and suppliers.
- **Functional Programming:** They enable functional-style programming in Java, encouraging immutability and side-effect-free functions.

Commonly Used Functional Interfaces in java.util.function:
|Interface |Description |Abstract Method|
|-|-|-|
|`Predicate<T>` |Takes an argument and returns a boolean result boolean |`test(T t)`|
|`Function<T, R>` |Takes an argument and returns a result R |`apply(T t)`|
|`Consumer<T>` |Takes an argument and returns no result void |`accept(T t)`|
|`Supplier<T>` |Takes no argument and returns a result |`T get()`|
|`UnaryOperator<T>` |Takes an argument and returns a result of the same type |`T apply(T t)`|
|`BinaryOperator<T>` |Takes two arguments and returns a result of the same type |`T apply(T t, T u)`|
|`BiFunction<T, U, R>` |Takes two arguments and returns a result |`R apply(T t, U u)`|
|`BiPredicate<T, U>` |Takes two arguments and returns a boolean result boolean |`test(T t, U u)`|

# Conclusion

Functional interfaces in Java provide a powerful way to use functional programming constructs like lambda expressions and method references. They simplify the code and make it more readable by focusing on behavior rather than implementation. Predefined functional interfaces like Predicate, Function, Consumer, and Supplier are essential tools in modern Java development.

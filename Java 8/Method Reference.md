# Method References

**Method References** in Java 8 provide a shorthand for lambda expressions when they refer to a method directly. They allow us to refer to methods or constructors without explicitly invoking them, making the code more concise and readable.

There are four types of method references in Java:

- Reference to a static method
- Reference to an instance method of an object
- Reference to an instance method of an arbitrary object of a particular type
- Reference to a constructor

## 1. Reference to a Static Method

This type of method reference refers to a static method in a class. The syntax is ClassName::methodName.

### Example:

Let's define a static method that converts a string to an integer.

```java
import java.util.function.Function;

public class StaticMethodReference {
    public static void main(String[] args) {
        // Lambda expression
        Function<String, Integer> lambdaConvert = (s) -> Integer.parseInt(s);

        // Method reference to the static method parseInt of Integer class
        Function<String, Integer> methodRefConvert = Integer::parseInt;

        // Test
        String numberStr = "42";
        System.out.println("Using Lambda: " + lambdaConvert.apply(numberStr)); // Output: 42
        System.out.println("Using Method Reference: " + methodRefConvert.apply(numberStr)); // Output: 42
    }
}
```

## 2. Reference to an Instance Method of a Particular Object

In this type, a method reference refers to an instance method of a specific object. The syntax is instance::methodName.

### Example:

Let’s define an example with a method reference to an instance method of a particular object.

```java
import java.util.function.Supplier;

public class InstanceMethodReference {
    public static void main(String[] args) {
        // Create a String object
        String message = "Hello, world!";

        // Lambda expression
        Supplier<String> lambdaSupplier = () -> message.toUpperCase();

        // Method reference to the instance method toUpperCase of message
        Supplier<String> methodRefSupplier = message::toUpperCase;

        // Test
        System.out.println("Using Lambda: " + lambdaSupplier.get()); // Output: HELLO, WORLD!
        System.out.println("Using Method Reference: " + methodRefSupplier.get()); // Output: HELLO, WORLD!
    }
}
```

## 3. Reference to an Instance Method of an Arbitrary Object of a Particular Type

In this type, a method reference refers to an instance method of an arbitrary object of a particular type (e.g., all objects of a certain class). The syntax is ClassName::methodName.

### Example:

Let’s use the method compareToIgnoreCase() of the String class in this example. This method will be applied to arbitrary instances of String.

```java
import java.util.Arrays;

public class ArbitraryObjectMethodReference {
    public static void main(String[] args) {
        // Array of strings
        String[] names = {"John", "Peter", "Alice", "Bob"};

        // Sort using Lambda expression
        Arrays.sort(names, (s1, s2) -> s1.compareToIgnoreCase(s2));

        System.out.println("Sorted using Lambda: " + Arrays.toString(names));

        // Sort using Method reference
        Arrays.sort(names, String::compareToIgnoreCase);

        System.out.println("Sorted using Method Reference: " + Arrays.toString(names));
    }
}
```

### Output:

```sql
Sorted using Lambda: [Alice, Bob, John, Peter]
Sorted using Method Reference: [Alice, Bob, John, Peter]
```

## 4. Reference to a Constructor

This type of method reference refers to a constructor. The syntax is `ClassName::new`.

### Example:

Suppose we want to create a Person object using a method reference to its constructor.

```java
import java.util.function.Supplier;

class Person {
    String name;

    public Person() {
        this.name = "Anonymous";
    }
}

public class ConstructorReference {
    public static void main(String[] args) {
        // Lambda expression
        Supplier<Person> lambdaSupplier = () -> new Person();

        // Method reference to the constructor of Person class
        Supplier<Person> methodRefSupplier = Person::new;

        // Test
        System.out.println("Using Lambda: " + lambdaSupplier.get().name); // Output: Anonymous
        System.out.println("Using Method Reference: " + methodRefSupplier.get().name); // Output: Anonymous
    }
}
```

### **Comparison:** Lambda Expression vs. Method Reference

A lambda expression:

```java
(s1, s2) -> s1.compareToIgnoreCase(s2)
```

A method reference for the same logic:

```java
String::compareToIgnoreCase
```

- Method references are more concise but less flexible (since they directly refer to an existing method).
- Use a lambda when you need to implement custom logic.
- Use a method reference when you just need to call an existing method.

### When to Use Method References

- **Simplicity:** Method references are best when the lambda expression only calls an existing method and nothing more.
- **Readability:** Method references can make code more readable by removing redundancy when a lambda is doing nothing but calling a method.

### Common Use Cases in Functional Programming

Method references are commonly used with functional interfaces such as:

- Supplier
- Function
- Consumer
- Predicate

For example, a static method reference can be used as a `Function` to convert strings to integers, and an instance method reference can be used as a `Consumer` to print elements in a collection.

## Conclusion

Method references provide a more concise and readable way to express simple lambda expressions. They directly refer to methods or constructors and are powerful when used in the right context, particularly in conjunction with Java's functional programming interfaces.

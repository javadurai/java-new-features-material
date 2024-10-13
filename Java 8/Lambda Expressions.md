# Lambda Expressions

Lambda expressions are a feature in Java (introduced in Java 8) that enable treating functionality as a method argument or passing code as data. In simple terms, a lambda expression allows you to create a function without belonging to any class (i.e., it’s an anonymous function). This makes code more concise and readable, especially when used with functional interfaces.

## Structure of Lambda Expressions

The basic syntax of a lambda expression is:

```java
(parameters) -> expression or { block of code }
```

- **Parameters:** The input to the lambda expression. If there are no parameters, you can use empty parentheses `()`. If there's only one parameter, parentheses can be omitted.
- **Arrow operator:** The `->` separates the parameter(s) from the body.
- **Body:** The code that is executed. It can be a single expression or a block of statements enclosed in braces `{}`.

### Example 1: Lambda with a Functional Interface

A common use of lambdas is with functional interfaces, which are interfaces with a single abstract method. An example is the Runnable interface.
Without Lambda

```java
Runnable r1 = new Runnable() {
    @Override
    public void run() {
        System.out.println("Runnable without Lambda");
    }
};
r1.run();
```

With Lambda

```java
Runnable r2 = () -> System.out.println("Runnable with Lambda");
r2.run();
```

Here, the lambda expression `() -> System.out.println("Runnable with Lambda") `replaces the need for an anonymous inner class. The empty parentheses represent no arguments, and the code after the arrow represents the `run()` method's body.

### Example 2: Passing Code as Data to a Method

A lambda expression can be passed as an argument to a method where functionality needs to be defined dynamically.

Suppose you have a method that performs an action on a list of strings:

```java
import java.util.Arrays;
import java.util.List;

public class LambdaExample {
    public static void processStrings(List<String> list, StringProcessor processor) {
        for (String s : list) {
            processor.process(s);
        }
    }

    public static void main(String[] args) {
        List<String> strings = Arrays.asList("apple", "banana", "cherry");

        // Lambda to print each string
        processStrings(strings, (String s) -> System.out.println(s));
    }
}

@FunctionalInterface
interface StringProcessor {
    void process(String s);
}
```

In this example, the method `processStrings` takes a `StringProcessor` (a functional interface) as an argument. The lambda `(String s) -> System.out.println(s)` is passed to it, which defines what to do with each string in the list.

### Example 3: Treating Functionality as Data

Lambda expressions can represent actions that can be passed around like data. This is common in functional programming.

```java
import java.util.function.Function;

public class LambdaExample {
    public static void main(String[] args) {
        Function<Integer, Integer> square = (Integer x) -> x * x;

        System.out.println(applyFunction(5, square));  // Output: 25
    }

    public static Integer applyFunction(Integer value, Function<Integer, Integer> function) {
        return function.apply(value);
    }
}
```

Here, `square` is a lambda expression that takes an integer and returns its square. This lambda is passed as an argument to the `applyFunction` method, treating the functionality as data.

## Key Points:

- **Lambdas simplify the code:** They allow you to express instances of single-method interfaces (functional interfaces) more concisely.
- **Used in APIs:** Many Java APIs use lambdas, especially those in the `java.util.function` package (like `Predicate`, `Function`, `Consumer`, etc.).
- **Functional Programming:** They bring functional programming concepts into Java by allowing you to treat behavior as data.

Java Records are a feature introduced in Java 14 as a preview and became a standard feature in Java 16. They provide a concise way to declare immutable data carrier classes. Records reduce boilerplate code, such as constructors, accessors, equals(), hashCode(), and toString() methods, which are typically needed for simple data-holding objects.
Key Features of Java Records:

    Immutable by Default: Fields of a record are implicitly final, meaning that once a value is assigned, it cannot be changed.
    Automatic Generation of Methods: The compiler automatically generates:
        A constructor to initialize the fields.
        Getter methods for all fields (but without the get prefix).
        equals(), hashCode(), and toString() methods based on the fields.
    Compact Syntax: You declare a record with a compact syntax, reducing the boilerplate code of typical Java classes.

Syntax of Records:

A record is defined using the record keyword, followed by the record name and the fields (components) in parentheses.

java

public record RecordName(Type field1, Type field2, ...) {}

Example: Simple Record

java

// Define a record to store information about a person
public record Person(String name, int age) {}

public class Main {
    public static void main(String[] args) {
        // Creating a record instance
        Person person = new Person("John", 25);

        // Accessing fields (note: no getName(), just name())
        System.out.println("Name: " + person.name());  // Output: Name: John
        System.out.println("Age: " + person.age());    // Output: Age: 25

        // toString(), equals(), and hashCode() are automatically generated
        System.out.println(person.toString());         // Output: Person[name=John, age=25]
        
        // Testing equality
        Person anotherPerson = new Person("John", 25);
        System.out.println(person.equals(anotherPerson));  // Output: true
    }
}

Behind the Scenes:

The Person record automatically generates the following code:

java

public final class Person {
    private final String name;
    private final int age;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String name() { return name; }
    public int age() { return age; }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age && Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }

    @Override
    public String toString() {
        return "Person[name=" + name + ", age=" + age + "]";
    }
}

Important Features of Records:

    Immutable Fields: Fields in records are final by default, meaning their values cannot be changed after the object is created.

    Accessor Methods: Records automatically generate accessor methods for each field, using the same name as the field. There are no traditional "getters" with getField() names; you access the field with field().

    Constructor: The canonical constructor is generated automatically, and it initializes the fields in the order they are defined in the record declaration.

    equals(), hashCode(), toString(): These methods are automatically generated based on the fields of the record. This is particularly useful for data classes, where these methods are often implemented based on field values.

Customizing Records:

Though records automatically generate a constructor and methods, you can still customize or override them if needed.
Custom Constructor:

You can define custom constructors with validation logic.

java

public record Person(String name, int age) {
    // Custom constructor with validation
    public Person {
        if (age < 0) {
            throw new IllegalArgumentException("Age cannot be negative");
        }
    }
}

Custom Methods:

You can also add custom methods to records.

java

public record Person(String name, int age) {
    // Custom method
    public String greet() {
        return "Hello, my name is " + name + " and I'm " + age + " years old.";
    }
}

Override Methods:

You can override methods like toString(), equals(), or hashCode() if needed.

java

public record Person(String name, int age) {
    @Override
    public String toString() {
        return "Person's name: " + name + ", age: " + age;
    }
}

Limitations of Records:

    Immutability: Once a record is created, its field values cannot be changed, which makes records unsuitable for use cases that require mutable state.

    Cannot Extend Other Classes: Records are implicitly final and cannot extend any other class. However, they can implement interfaces.

    No Additional Fields: Records cannot have fields that are not part of their declaration. You can only use the fields listed in the record header.

When to Use Records:

    Data Carrier Classes: Use records when you need simple classes that primarily hold data, like DTOs (Data Transfer Objects) or POJOs (Plain Old Java Objects).
    Immutability: When you want to ensure the immutability of the objects, records are a good fit because they enforce immutability by default.
    Boilerplate Reduction: If your class requires standard equals(), hashCode(), toString(), and accessors, records help to reduce boilerplate code.

Example: Records Implementing Interfaces

java

// Define an interface
public interface Printable {
    void print();
}

// Define a record that implements the interface
public record Book(String title, String author) implements Printable {
    @Override
    public void print() {
        System.out.println("Title: " + title + ", Author: " + author);
    }
}

public class Main {
    public static void main(String[] args) {
        Book book = new Book("Java in Action", "John Doe");
        book.print();  // Output: Title: Java in Action, Author: John Doe
    }
}

In this example, Book is a record that implements the Printable interface and defines a custom method print().
Conclusion:

Java Records simplify the creation of immutable data classes by automatically generating constructors, accessors, and common methods like equals(), hashCode(), and toString(). They are ideal for use cases where immutability is desired, and you need to store data in a concise, boilerplate-free manner.
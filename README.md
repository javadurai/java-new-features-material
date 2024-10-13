# Java New Features

## Java 8 (March 2014)

1. **Lambda Expressions** - Enables treating functionality as a method argument or passing code as data.
1. **Stream API** - For processing sequences of elements (e.g., collections) in a functional programming style.
1. **Default Methods in Interfaces** - Allows method implementations in interfaces.
1. **Optional Class** - To handle null values more effectively, avoiding NullPointerExceptions.
1. **New Date and Time API (java.time)** - A new date and time library inspired by Joda-Time.
1. **Nashorn JavaScript Engine** - A new, faster JavaScript engine.
1. **Parallel Arrays** - Added parallel processing support to arrays.
1. **Method References** - Easier syntax for referring to methods using ::.
1. **Functional Interfaces** - Single-method interfaces that can be used as lambdas.

## Java 9 (September 2017)

1. **JShell (REPL)** - Interactive Java Shell for running and testing snippets of Java code.
1. **Module System (Project Jigsaw)** - Modularized the JDK for improved application scalability and maintainability.
1. **Stream API Enhancements** - New methods such as takeWhile(), dropWhile(), and iterate().
1. **Private Interface Methods** - Support for private methods inside interfaces.
1. **Multi-Release JARs** - Enabled packaging multiple versions of class files for different Java versions in a single JAR.
1. **Improved Optional API** - Added methods like ifPresentOrElse(), or(), etc.

## Java 10 (March 2018)

1. **Local Variable Type Inference (var)** - Allows type inference for local variables.
1. **Garbage Collector Interface** - Unified interface for various garbage collectors.
1. **Application Class-Data Sharing** - Improved startup and memory footprint for Java applications.
1. **Thread-Local Handshakes** - Enabled stopping individual threads rather than all threads in safepoints.

## Java 11 (September 2018)

1. **HTTP Client (Standard)** - A new, fully-featured HTTP client API supporting HTTP/2 and WebSockets.
1. **Local-Variable Syntax for Lambda Parameters** - You can now use var in lambda parameters.
1. **Removal of Java EE and CORBA Modules** - Java EE and CORBA modules were removed from the JDK.
1. **String API Enhancements** - Added methods like isBlank(), lines(), strip(), repeat().
1. **Launch Single-File Programs** - Run single-file Java source code without compiling explicitly.

## Java 12 (March 2019)

1. **Switch Expressions (Preview)** - Enhanced switch to be used as a statement or an expression.
1. **JVM Constants API** - New API to model key class-file and runtime artifacts.
1. **Garbage Collector Improvements** - G1 garbage collector optimizations.

## Java 13 (September 2019)

1. **Text Blocks (Preview)** - Multiline string literals using triple quotes """.
1. **Switch Expressions (Second Preview)** - Improvements to switch expressions.
1. **Dynamic CDS Archives** - Improved class data sharing for application classes.

## Java 14 (March 2020)

1. **Records (Preview)** - New data class that minimizes boilerplate for immutable data containers.
1. **Pattern Matching for instanceof (Preview)** - Simplified syntax for casting in instanceof.
1. **Switch Expressions (Standard)** - Switch expressions became a standard feature.
1. **Helpful NullPointerExceptions** - Improved NPE messages for easier debugging.

## Java 15 (September 2020)

1. **Text Blocks (Standard)** - Multiline string literals became a standard feature.
1. **Sealed Classes (Preview)** - Allows restriction of which classes can extend or implement a class/interface.
1. **Hidden Classes** - Support for classes that are not discoverable by regular bytecode APIs.
1. **Pattern Matching for instanceof (Second Preview)** - More improvements to pattern matching.

## Java 16 (March 2021)

1. **Records (Standard)** - Records became a standard feature.
1. **Pattern Matching for instanceof (Standard)** - Finalized pattern matching for instanceof.
1. **Sealed Classes (Second Preview)** - Continued refinements to sealed classes.
1. **Vector API (Incubator)** - Introduced a new API for vector computations.

## Java 17 (September 2021)

1. **Sealed Classes (Standard)** - Finalized sealed classes feature.
1. **Pattern Matching for Switch (Preview)** - Adds pattern matching to switch statements.
1. **Context-Specific Deserialization Filters** - Helps prevent security risks in deserialization.
1. **Foreign Function & Memory API (Incubator)** - Provides an API to interact with native code and memory.

## Java 18 (March 2022)

1. **Simple Web Server** - A minimal web server for prototyping and testing.
1. **UTF-8 by Default** - UTF-8 becomes the default charset for the standard Java APIs.
1. **Vector API (Third Incubator)** - Continued work on the vector API.
1. **Code Snippets in JavaDoc** - Support for inclusion of code snippets in Javadoc.

## Java 19 (September 2022)

1. Virtual Threads (Preview) - Lightweight threads for scalable concurrency.
1. Structured Concurrency (Incubator) - Simplifies multithreaded programming.
1. **Pattern Matching for switch (Second Preview)** - Enhancements to switch pattern matching.
1. **Foreign Function & Memory API (Second Incubator)** - Continued development of native code integration.

## Java 20 (March 2023)

1. **Scoped Values (Incubator)** - Allows sharing of immutable data between threads.
1. **Record Patterns (Second Preview)** - Introduced record pattern matching in more contexts.
1. **Foreign Function & Memory API (Third Preview)** - Further refinements to interacting with native code.
1. **Pattern Matching for switch (Fourth Preview)** - Continued improvements to pattern matching for switch.

## Java 21 (September 2023)

1. **Virtual Threads (Standard)** - Finalized virtual threads for better concurrency support.
1. **Sequenced Collections** - New interfaces for collections with well-defined iteration orders.
1. **Pattern Matching for switch (Standard)** - Finalized switch pattern matching.
1. **Record Patterns (Standard)** - Record patterns became a full feature.
1. **String Templates (Preview)** - Simplified the creation of string literals with placeholders.

These feature lists show the significant advancements made in Java versions since Java 8, with a strong focus on improving syntax simplicity, performance, and scalability.
